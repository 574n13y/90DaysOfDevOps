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

