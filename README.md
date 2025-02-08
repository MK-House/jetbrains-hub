# JetBrains Hub Setup

This repository contains the setup for deploying JetBrains Hub using Docker, Ansible, and GitHub Actions.

## Prerequisites

- Docker
- Docker Compose
- Ansible
- GitHub Actions

## Configuration

### Docker Configuration

The Docker configuration is defined in the `docker-compose.yml` file located in the `docker` directory. The configuration includes services for JetBrains Hub and PostgreSQL database.

### Environment Variables

The environment variables required for the setup are defined in the `hub-config.properties` file located in the `docker` directory. These variables are substituted using `envsubst` during the GitHub Actions workflow.

### Ansible Playbook

The Ansible playbook for deploying JetBrains Hub is located in the `ansible/playbooks` directory. The playbook performs the following tasks:

- Checks if the project directory exists and creates a backup if it does.
- Cleans and publishes the JetBrains Hub project to remote nodes.
- Installs Docker if it is not already installed.
- Deploys JetBrains Hub using Docker Compose.

### GitHub Actions Workflow

The GitHub Actions workflow is defined in the `.github/workflows/main.yaml` file. The workflow performs the following steps:

- Checks out the repository.
- Installs `gettext` for `envsubst`.
- Substitutes environment variables in the `hub-config.properties` file.
- Copies the project to the dropfolder.
- Runs the Ansible playbook to deploy JetBrains Hub.

## Usage

1. Clone the repository:

    ```sh
    git clone https://github.com/yourusername/mk-house.git
    cd mk-house/jetbrains-hub
    ```

2. Set up the required environment variables in the `hub-config.properties` file.

3. Run the GitHub Actions workflow to deploy JetBrains Hub.

## License

This project is licensed under the MIT License. See the [LICENSE](../LICENSE) file for more details.
