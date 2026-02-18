flowchart TB

  PLATFORM[Ansible Windows IaC Platform]

  PLATFORM --> REPO[IaC Repository]
  PLATFORM --> EXEC[Execution Environment]

  REPO --> INV[inventories]
  REPO --> GV[group_vars_common]
  REPO --> PB[playbooks]
  REPO --> RL[roles]

  INV --> LAB[lab]
  INV --> DEV[dev]
  INV --> TEST[test]
  INV --> PRD[prd]

  EXEC --> RUNNER[GitLab Runner]
  RUNNER --> CONTAINER[Ansible Execution Container]
