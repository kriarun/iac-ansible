sequenceDiagram
  actor U as Engineer/Developer
  participant CI as GitLab Job
  participant R as Runner + Ansible Container
  participant W as Windows Hosts
  participant S as File Share / Artifact Repo
  participant V as Vault

  U->>CI: Trigger manual job (env + playbook)
  CI->>V: Fetch secrets (svc account creds)
  V-->>CI: Return secrets (env vars)
  CI->>R: Start job (pull image + checkout repo)
  R->>W: Connect via WinRM (NTLM)
  R->>S: Download/copy installers (MSI/EXE)
  R->>W: Install/configure (idempotent roles)
  R-->>CI: Job result (changed/ok/failed)
  CI-->>U: Pipeline status
