lu-system_engineering-devops

Projects and exercises for the System Engineering & DevOps track at ALU. This repository contains scripts and notes covering Linux, shell scripting, web infrastructure, and debugging.

## Repository Structure

```
alu-system_engineering-devops/
├── README.md
└── web_stack_debugging_0/
    └── 0-give_me_a_page
```

## Projects

### web_stack_debugging_0

Introductory web stack debugging project using Docker and Apache.

| File | Description |
|------|-------------|
| `0-give_me_a_page` | Bash script that starts Apache and serves a page containing `Hello Holberton` at the root of the container |

**The task:** in a Docker container running Apache, make a request to the root (`/`) of the server return a page containing `Hello Holberton`.

**How to test it:**

```bash
# Start the container (use any free host port)
docker run -p 8090:80 -d -it holbertonschool/265-0

# Copy the script into the container and run it
docker cp 0-give_me_a_page <container_id>:/0-give_me_a_page
docker exec -it <container_id> bash /0-give_me_a_page

# Check the result
curl http://localhost:8090
# Hello Holberton
```

Replace `<container_id>` with the ID shown by `docker ps`.

## Requirements

- Ubuntu / Debian-based environment
- Bash scripts start with `#!/usr/bin/env bash`
- Scripts must be executable (`chmod +x <file>`)
- Docker installed on the host to run the debugging containers

## Usage

Clone the repository:

```bash
git clone https://github.com/acyubahiroo/alu-system_engineering-devops.git
cd alu-system_engineering-devops
```

Make scripts executable if needed:

```bash
chmod +x web_stack_debugging_0/0-give_me_a_page
```

## Author

**acyubahiroo** - [GitHub](https://github.com/acyubahiroo)
