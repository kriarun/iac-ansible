# Roles

Roles will be added under this directory in follow-up iterations.

Expected role behavior:
- Install software from MSI/EXE packages stored on the shared file server.
- Be idempotent using per-software checks (registry keys, installation paths, or service state).
- Configure environment variables such as PATH and JAVA_HOME when required.
- Encapsulate installation checks and remediation logic per software package.
