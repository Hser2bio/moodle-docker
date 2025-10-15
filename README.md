# Moodle Docker
### Recommended Specs
```txt
CPU: 4 Core
RAM: 8 GB
Storage: 30 GB
Versi OS:  Ubuntu 20.04
```

## Install Docker by following the official Ubuntu guide:
install docker https://docs.docker.com/engine/install/ubuntu/ 

Grant your user Docker permissions (log out and log back in after running this command): `usermod -aG docker $USER`

## Setup Moodle
- Clone the repository:
```bash
git clone https://github.com/Derkora/moodle-docker
cd moodle-docker
```
- Create the environment file from the example:
```bash
cp .env.example .env
```
- Create the dedicated Docker network for Moodle:
```bash
docker network create moodle-network
```
- (Optional) Build the Moodle Docker image locally:
```bash
cd ver/5.0-nginx
docker build -t derkora/moodle:5.0-nginx .
```
- Run the Docker containers:
```bash
docker compose up -d
```

## Setup Web (Initial Moodle Configuration)
1. Open your web browser and navigate to your server's IP address: `http://YOUR-VPS-IP`

2. Follow the on-screen installation steps:
   - Language: Choose your language and click "Next".
   - Confirm paths: The default paths should be correct. Click "Next".
   - Choose database driver: Select "MariaDB (native/mariadb)".
   - Database settings: Enter the following details:
     - Database host: moodle_db
     - Database name: moodle
     - Database user: ${MOODLE_DATABASE_USER} (from your .env file)
     - Database Password: ${MOODLE_DATABASE_PASSWORD} (from your .env file)
    
3. On the "Installation - Moodle" screen, click "Continue".

4. The installation process will now run. This may take several minutes.

5. Once complete, you will be prompted to create an administrator account and provide site details. Fill these in as required to finish the setup.
