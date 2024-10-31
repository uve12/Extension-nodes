# Extension-nodes

Installing Chromium browser to run the extension depin nodes

---

# Join Crypto Console Community

Join TG : [Crypto Console Telegram](https://t.me/cryptoconsol) 

Follow X : [Crypto Console Twitter](https://www.x.com/cryptoconsol) 

Subscribe : [Crypto Console Youtube](https://www.youtube.com/@cryptoconsole)

---

## Hardware requirements:

| **Hardware** | **Minimum Requirement** |
|--------------|-------------------------|
| **CPU**      | 4 Cores                 |
| **RAM**      | 4 GB                    | 
| **Disk**     | 10   GB  SSD            |

---

# VPS Options

Credit Card/Paypal/Crypto credit card : 

VPS 1 : [Contabo: Cloud VPS 1](https://www.jdoqocy.com/click-101278318-15692486) 

VPS 2 : [Contabo: Cloud VPS 2](https://www.tkqlhce.com/click-101278318-13796472)

VPS 3 : [Contabo: Cloud VPS 3](https://www.dpbolvw.net/click-101278318-13796474)

VPS 4 : [Contabo: Cloud VPS 4](https://www.anrdoezrs.net/click-101278318-13796476)

---

## 1-click Script
```
git clone https://github.com/uve12/Extension-nodes.git
cd Extension-nodes
```
Make executable:

```
chmod +x extnodes.sh
```
Start the Script :
```
./extnodes.sh
```

Here’s an alternative method to install and run Chromium using Docker, based on the `lscr.io/linuxserver/chromium:latest` image:

###  1: Update VPS
```bash
sudo apt-get update && sudo apt-get upgrade -y
sudo apt install curl -y
sudo apt install ca-certificates
```

###  2: Install Docker
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
docker version
```
###  3: Install docker compose
```
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)

curl -L "https://github.com/docker/compose/releases/download/"$VER"/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

### 4. Create a Project Directory:
```bash
mkdir chromium
cd chromium
```

### 5. Create a `docker-compose.yml` File:
```bash
nano docker-compose.yml
```

### 6. Paste This Docker Compose Configuration:

```yaml
version: "3.8"
services:
  chromium:
    image: lscr.io/linuxserver/chromium:latest
    container_name: chromium_browser
    environment:
      - PUID=1000  # User ID for file permissions
      - PGID=1000  # Group ID for file permissions
      - TZ=Europe/Berlin  # Adjust timezone
      - CUSTOM_USER=your_username  # Set your own username
      - PASSWORD=your_password  # Set your password
      - CHROME_CLI=https://www.google.com  # Optional: Default starting page
    ports:
      - "3050:3000"  # Adjust ports if necessary
      - "3051:3001"
    security_opt:
      - seccomp:unconfined
    volumes:
      - /root/chromium/config:/config  # Config directory for Chromium
    shm_size: "1gb"  # Prevents crashes by giving the container enough shared memory
    restart: unless-stopped  # Automatically restart on failures or reboots
```

### 7. Save and Exit:
Save the file by pressing `Ctrl + X`, then `Y`, and press `Enter`.

### 8. Start the Container:
Run the following command to spin up the Chromium container:
```bash
docker-compose up -d
```

### 9. Access Chromium:
Open your browser and visit:

http://<VPS_IP>:3050

Or

https://<VPS_IP>:3051

You can now access Chromium remotely via the VNC interface with your set username and password.


