## Sample project. Deploy java spring application on CentOS host with DEVOPS tools

Required DEVOPS Tools: Ansible, Jenkins, Sonatype Nexus.

### Jenkins setup

Install Jenkins with apt-get install/zip download/docker and run

Required Jenkins Plugins:
- Blue Ocean(optional)
- Ansible plugin
- Command Agent Launcher Plugin
- Generic Webhook Trigger Plugin
- Maven Integration plugin
- Nexus Artifact Uploader
- Nexus Platform
- Pipeline
- Pipeline Maven Integration Plugin
- Pipeline Utility Steps
- SSH Agent Plugin

For this sample you need 3 different Credentials configured in Jenkins:
- **Username with password** for Nexus
- **Secret text** for Ansible vault file
- **SSH Username with private key** for access to destination host

### Sonatype Nexus setup

Download Nexus and run

- Create necessary Repositories(maven, yum and etc) or use existing
- Create Roles with previligies for certain repositories
- Create Users and assign them certain Roles

These Users can be used for an access to Nexus by Jenkins and Ansible agents

### Delivery steps

#### Jenkins pipeline

1. Build maven artifact
2. Run unit tests
3. Upload artifact to Nexus
4. Run andible deploy script

#### Ansible deploy

1. Check necessary libs
2. Configure Nginx(TODO: move nginx related setup from deploy role to nginx role)
3. Download Artifact
4. Setup service for java application
5. Configure Nginx as a proxy for java application

#### Notes

- In Pipeline curl might be used insted of Nexus plugin for uploading artifacts to Nexus