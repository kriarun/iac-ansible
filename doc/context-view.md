flowchart LR

  USER[Platform Engineer / Developer]
  GITLAB[GitLab CI Pipeline]
  RUNNER[GitLab Runner]
  CONTAINER[Ansible Execution Container - custom image]
  HOSTS[Managed Windows Hosts]
  VAULT[HashiCorp Vault]
  REPO[Software Repository - JFrog / File Share]

  USER -->|Manual trigger| GITLAB
  GITLAB -->|Start job| RUNNER
  RUNNER -->|Pull image| CONTAINER

  GITLAB -->|Fetch credentials| VAULT
  VAULT -->|CI env vars| GITLAB

  CONTAINER -->|WinRM| HOSTS
  HOSTS -->|Download installers| REPO
