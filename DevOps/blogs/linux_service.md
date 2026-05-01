# Linux as a service

- A service is just a program that runs in the background
- systemctl is the tool to control it
- systemd is the system that manages services

A simple analogy is to think of a service as a car. You can start it, stop it, and check its status. The systemd is like the engine that keeps the car running smoothly.

## What you'll learn

- Create a service
- Start / stop using `systemctl`
- Enable / disable
- Delete cleanly (no mess)

## Step 1: Create a simple script

Create a file:

```bash
sudo nano ~/my_simple_service.sh
```

Paste this content:

```bash
#!/bin/bash

while true
do
  echo "Hello! Service is running..."
  sleep 5
done
```

Save and exit. Ctrl + O, Enter, Ctrl + X.

Make it executable:

```bash
chmod +x ~/my_simple_service.sh
```

