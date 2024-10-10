## Tasks

1. **Install Docker and Jenkins:**
   - Install Docker and Jenkins on your system from your terminal using package managers.

# Installing Docker and Jenkins on Ubuntu

## Step 1: Update your system

```
sudo apt-get update
```

## Step 2: Install Docker

1. Uninstall old versions (if any):

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

2. Set up the Docker repository:

```bash
sudo apt-get install ca-certificates curl gnupg lsb-release
```

3. Add Docker's official GPG key:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

4. Add the Docker APT repository:

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. Install Docker Engine:

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
```

6. Verify that Docker is installed correctly:

```bash
sudo docker run hello-world
```

## Step 3: Install Jenkins

1. Install Java (Jenkins requires Java):

```bash
sudo apt install openjdk-11-jdk -y
```

2. Add the Jenkins repository:

```bash
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
```

3. Add the Jenkins repository to the system's sources list:

```bash
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

4. Update the package list:

```bash
sudo apt-get update
```

5. Install Jenkins:

```bash
sudo apt-get install jenkins -y
```

6. Start Jenkins:

```bash
sudo systemctl start jenkins
```

7. Enable Jenkins to start on boot:

```bash
sudo systemctl enable jenkins
```

## Step 4: Access Jenkins

Open your web browser and navigate to `http://<your_server_ip_or_domain>:8080`. Use the initial password from `/var/lib/jenkins/secrets/initialAdminPassword` to unlock Jenkins.

## Tasks

1. **Check Docker Service Status:**
   - Check the status of the Docker service on your system (ensure you have completed the installation tasks above).
```
sudo systemctl status docker
```

2. **Manage Jenkins Service:**
   - Stop the Jenkins service and post before and after screenshots.
```
sudo systemctl status jenkins.
sudo systemctl stop jenkins
sudo systemctl status jenkins
```

3. **Read About Systemctl vs. Service:**
   - Read about the differences between the `systemctl` and `service` commands.
   - Example: `systemctl status docker` vs. `service docker status`.

# `systemctl` vs `service` Commands

### 1. **Framework**
- **`systemctl`**: Part of the modern `systemd` system for managing services, timers, sockets, and more.
- **`service`**: Part of the older `SysVinit` system, used primarily for managing services.

### 2. **Usage**
- **`systemctl`**:
  - Example: `systemctl status docker`
  - Supports starting, stopping, checking status, and advanced management of services.
  - Provides detailed logs and state information.

- **`service`**:
  - Example: `service docker status`
  - Limited to basic service management: starting, stopping, and status.
  - Acts as a wrapper for `systemd` in modern systems.

### 3. **Key Differences**
| Feature            | `systemctl`                   | `service`                   |
|--------------------|-------------------------------|-----------------------------|
| **Framework**       | `systemd`-based               | `SysVinit`-based             |
| **Scope**           | Services, timers, mounts, etc. | Primarily services           |
| **Logging**         | Integrated with `journalctl`  | Limited output               |
| **Output**          | More detailed                 | Basic service status         |

### 4. **Recommendation**
- Use **`systemctl`** on modern Linux distributions (Ubuntu 15.04+, CentOS 7+).
- Use **`service`** for compatibility with older systems.


### Additional Tasks

4. **Automate Service Management:**
   - Write a script to automate the starting and stopping of Docker and Jenkins services.
```
#!/bin/bash

# Function to check service status
check_status() {
    echo "Checking status of $1..."
    sudo systemctl status $1 --no-pager
}

# Function to start services
start_services() {
    echo "Starting Docker and Jenkins services..."
    sudo systemctl start docker
    sudo systemctl start jenkins
    echo "Docker and Jenkins services started."
}

# Function to stop services
stop_services() {
    echo "Stopping Docker and Jenkins services..."
    sudo systemctl stop docker
    sudo systemctl stop jenkins
    echo "Docker and Jenkins services stopped."
}

# Function to show usage instructions
show_usage() {
    echo "Usage: $0 {start|stop|status}"
    exit 1
}

# Main script logic
case "$1" in
    start)
        start_services
        ;;
    stop)
        stop_services
        ;;
    status)
        check_status docker
        check_status jenkins
        ;;
    *)
        show_usage
        ;;
esac

```

```
start - ./manage_services.sh start

stop - ./manage_services.sh stop

status - ./manage_services.sh status
```

5. **Enable and Disable Services:**
   - Use systemctl to enable Docker to start on boot and disable Jenkins from starting on boot.
```
sudo systemctl enable docker
sudo systemctl disable jenkins

```

6. **Analyze Logs:**
   - Use journalctl to analyze the logs of the Docker and Jenkins services. Post your findings.

# Analyzing Docker and Jenkins Logs with journalctl

## 1. Analyzing Docker Logs
To view the logs for the Docker service, use:
```bash
sudo journalctl -u docker.service
```

## 2. Analyzing Jenkins Logs
To view the logs for the Jenkins service, use:
```bash
sudo journalctl -u jenkins.service
```

## Findings

### Docker Logs:
- **Startup Messages**: Information about Docker daemon startup and any configurations loaded.
- **Container Events**: Logs about container creation, starting, stopping, and errors related to containers.
- **Errors**: Any issues that occurred during container operations, such as network problems or resource constraints.

### Jenkins Logs:
- **Startup Messages**: Details about Jenkins startup, including plugins loaded and server configuration.
- **Build Logs**: Output from jobs that have run, including success messages and errors encountered during job execution.
- **User Activity**: Logs related to user actions, such as logins, job executions, and API calls.
- **Errors**: Any errors or warnings related to plugin issues, job failures, or system resources.

## Example Output
Here’s a sample output snippet you might encounter:

**Docker Logs:**
```
Oct 10 10:15:15 s74n13y-host dockerd[1302]: time="2024-10-10T10:15:15.123456789Z" level=info msg="Starting up"
Oct 10 10:15:20 s74n13y-host dockerd[1302]: time="2024-10-10T10:15:20.987654321Z" level=info msg="Container created: my_container"
```

**Jenkins Logs:**
```
Oct 10 10:15:15 s74n13y-host jenkins[1402]: INFO: Jenkins is fully up and running
Oct 10 10:15:20 s74n13y-host jenkins[1402]: WARNING: Failed to run job 'Build Project'
```

## Conclusion
Using `journalctl`, you can effectively monitor the health and activities of Docker and Jenkins services. These logs are essential for troubleshooting issues and ensuring that both services run smoothly.

To filter logs for specific entries or a particular timeframe, you can use options like `--since` and `--until`. For example:
```bash
sudo journalctl -u docker.service --since "2024-10-10 10:00:00" --until "2024-10-10 11:00:00"
``` 

