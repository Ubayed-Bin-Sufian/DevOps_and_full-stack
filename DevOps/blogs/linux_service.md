# Linux as a service (The simplest Way to Understand It)

- A service is just a program that runs in the background
- `systemctl` is the tool to control it
- `systemd` is the system that manages services

**Simple analogy**

Think of a service like a car 🚗:

- You can start it
- You can stop it
- You can check if it’s running

The systemd is like the engine that keeps the car running smoothly behind the scenes.

## What you'll learn

By the end of this, you’ll be able to:
- Create your own service
- Start / stop it using `systemctl`
- Enable / disable it at boot
- Delete it cleanly (no leftover mess)

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

Save and exit. 
- `Ctrl + O` --> Enter
- `Ctrl + X`

Make it executable:

```bash
chmod +x ~/my_simple_service.sh
```

## Step 2: Create a systemd service 

Now we tell **systemd** how to run our script.

```bash
sudo nano /etc/systemd/system/my-simple.service
```

Paste this:

```bash
[Unit]
Description=My Simple Demo Service

[Service]
ExecStart=/home/$USER/my-simple-service.sh
Restart=always

[Install]
WantedBy=multi-user.target
```

👉 Replace `/home/your-username` with your actual username
(Don’t use `$USER` here — systemd won’t expand it properly)

## Step 3: Reload systemd and start the service

```bash
sudo systemctl daemon-reload
sudo systemctl start my-simple.service
```

## Step 4: Check status

```bash
sudo systemctl status my-simple.service
```

You should see the service running.

## Step 5: Stop the service

```bash
sudo systemctl stop my-simple.service
```

## Step 6: Enable / Disable (auto-start on boot)

Enable:

```bash
sudo systemctl enable my-simple.service
```

Disable:

```bash
sudo systemctl disable my-simple.service
```

## Step 7: View logs

```bash
sudo journalctl -u my-simple.service
```

You should see:

```bash
"Hello! Service is running..."
```
…repeating every 5 seconds.

## Step 8: Clean up (Delete everything properly)

```bash
sudo systemctl stop my-simple.service
sudo systemctl disable my-simple.service
sudo rm /etc/systemd/system/my-simple.service
sudo systemctl daemon-reload
sudo rm ~/my_simple_service.sh
```

Now your system is back to a clean state—no leftover services, no hidden issues.

You just created and managed your first Linux service from scratch 🎉

This is a small step—but it’s exactly how real-world services (like web servers and databases) are managed in production.