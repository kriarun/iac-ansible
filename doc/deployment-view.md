flowchart LR

  subgraph CI[CI Environment]
    GITLAB[GitLab CI]
    RUNNER[Self-hosted GitLab Runner]
    CONTAINER[Ansible Execution Container]
  end

  subgraph WINDOWS[Windows Infrastructure]
    HOSTS[Managed Windows VMs]
  end

  subgraph SERVICES[Internal Services]
    VAULT[HashiCorp Vault]
    REPO[Software Repository / File Share]
  end

  GITLAB --> RUNNER
  RUNNER --> CONTAINER
  CONTAINER -->|WinRM| HOSTS
  HOSTS -->|Download installers| REPO
  GITLAB -->|Fetch secrets| VAULT
