sequenceDiagram
  actor U as Engineer/Developer
  participant CI as GitLab Job
  participant R as Runner + Ansible Container
  participant W as Windows Hosts
  participant S as Internal Software Source (Share / Repo)
  participant V as Vault

  U->>CI: Trigger manual job (env + playbook)
  CI->>V: Fetch secrets
  V-->>CI: Return secrets
  CI->>R: Start job
  R->>W: Connect via WinRM
  R->>W: Execute roles

  alt Install directly from network share (UNC)
    R->>W: Install from UNC path (no staging)
  else Stage locally then install
    W->>S: Copy/Download installer to local temp
    R->>W: Install from local path
    R->>W: Optional cleanup of staged files
  end

  R-->>CI: Job result
  CI-->>U: Pipeline status
