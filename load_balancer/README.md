# Load balancer

This project adds redundancy to the web stack by running two web servers
(web-01 and web-02) behind an HAProxy load balancer (lb-01).

## Servers

| Name        | IP              | Role          |
|-------------|-----------------|---------------|
| 7263-web-01 | 18.175.227.94   | Nginx web server |
| 7263-web-02 | 35.177.58.26    | Nginx web server |
| 7263-lb-01  | 35.178.111.161  | HAProxy load balancer |

## Files

| File | Description |
|------|-------------|
| `0-custom_http_response_header` | Installs Nginx and adds a custom `X-Served-By` response header whose value is the server's hostname. Run on web-01 and web-02. |
| `1-install_load_balancer` | Installs HAProxy and distributes traffic to web-01 and web-02 using the roundrobin algorithm. Run on lb-01. |

## Usage

On web-01 and web-02:

```bash
chmod +x 0-custom_http_response_header
./0-custom_http_response_header
```

On lb-01:

```bash
chmod +x 1-install_load_balancer
./1-install_load_balancer
```

## Testing

```bash
curl -sI 18.175.227.94 | grep X-Served-By    # 7263-web-01
curl -sI 35.177.58.26 | grep X-Served-By     # 7263-web-02
curl -sI 35.178.111.161 | grep X-Served-By   # alternates between both
```

## Requirements

- Ubuntu 16.04 LTS
- Hostnames set to `7263-web-01`, `7263-web-02` and `7263-lb-01`
- Scripts pass Shellcheck (SC2154 ignored)
