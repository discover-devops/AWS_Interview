# Ansible Interview Questions

#### 1. Direct Technical Questions

**a. What is Ansible and what are its main features?**
- Ansible is an open-source automation tool for configuration management, application deployment, and task automation. Its main features include agentless architecture, simple YAML-based playbooks, and extensive module support.

**b. Explain the architecture of Ansible.**
- Ansible uses a simple architecture that consists of:
  - Control Node: The machine where Ansible is installed and from which commands are run.
  - Managed Nodes: The machines being managed by Ansible.
  - Inventory: A list of managed nodes.
  - Modules: Units of work that Ansible executes.
  - Playbooks: YAML files containing a series of tasks to be executed on managed nodes.
  - Plugins: Extend Ansible's core functionality.

**c. What are Ansible Playbooks?**
- Playbooks are YAML files that define a series of tasks to be executed on managed nodes. They describe automation in a human-readable format and can include variables, conditionals, loops, and handlers.

**d. What is an Ansible module?**
- An Ansible module is a reusable, standalone script that Ansible runs to perform a specific task, such as managing files, packages, services, or systems.

**e. How do you manage sensitive data in Ansible?**
- Sensitive data in Ansible can be managed using Ansible Vault, which allows you to encrypt variables, files, and playbooks.

**f. What is the difference between a role and a playbook in Ansible?**
- A playbook is a collection of tasks that define automation for a specific set of hosts. A role is a way to organize playbooks and other files in a standardized file structure, making reuse and sharing easier.

#### 2. Troubleshooting Questions

**a. Ansible is unable to connect to a managed node. What steps do you take to troubleshoot?**
- Check the SSH connectivity and credentials.
- Verify the managed node's IP address and hostname.
- Ensure the managed node is listed in the inventory.
- Check the Ansible configuration file for any misconfigurations.
- Look at the Ansible debug logs for detailed error messages.

**b. A playbook fails to execute a task. How do you diagnose and resolve the issue?**
- Review the error message and the specific task that failed.
- Use `--check` and `--diff` modes to see what changes would be made without applying them.
- Run the playbook in verbose mode (`-vvv`) for detailed output.
- Check for syntax errors or incorrect module usage.
- Ensure all dependencies and required modules are available on the managed node.

**c. How do you handle idempotency issues in Ansible?**
- Ensure that tasks are written in an idempotent manner, meaning they can be run multiple times without changing the state beyond the initial application.
- Use Ansible modules that are designed to be idempotent.
- Test playbooks thoroughly to confirm they achieve the desired state without causing unintended changes.

#### 3. Scenario-Based Questions

**a. How would you set up a LAMP stack on a group of servers using Ansible?**
- Create an inventory file listing the target servers.
- Write a playbook with tasks to install and configure Apache, MySQL, and PHP.
- Use appropriate modules (`yum`, `apt`, `service`, `file`, etc.) to ensure each component is installed and configured correctly.
- Test the playbook on a single server before applying it to all servers.

**b. Describe the process of rolling updates using Ansible.**
- Define a playbook with tasks to update the application or system.
- Use the `serial` keyword to specify the number of hosts to update at a time.
- Implement health checks to verify the success of updates before proceeding to the next batch of hosts.
- Use handlers to restart services or perform other actions only when changes are made.

**c. How would you use Ansible to manage configuration drift?**
- Regularly apply playbooks to ensure the desired state is maintained.
- Use Ansible Tower or AWX to schedule playbook runs and monitor their execution.
- Implement continuous integration and continuous deployment (CI/CD) pipelines to automatically enforce configurations.

**d. How do you integrate Ansible with a CI/CD pipeline?**
- Use a CI/CD tool like Jenkins, GitLab CI, or CircleCI to trigger Ansible playbooks.
- Store Ansible playbooks in a version control system (e.g., Git).
- Define pipeline stages for different environments (development, staging, production).
- Use the CI/CD tool to run Ansible commands and apply configurations as part of the deployment process.

#### 4. Real-World Use Cases

**a. Automated Server Provisioning**
- Use Ansible to automate the provisioning of new servers. A playbook can install the necessary packages, configure system settings, and deploy applications.

**b. Configuration Management**
- Maintain consistent configurations across multiple servers. Use playbooks to enforce configurations and ensure that all servers comply with the desired state.

**c. Application Deployment**
- Deploy applications with zero downtime. Use Ansible to manage the deployment process, including code updates, database migrations, and service restarts.

**d. Security Compliance**
- Automate security compliance checks and remediation. Write playbooks to ensure that all servers adhere to security policies and standards.

**e. Multi-Cloud Orchestration**
- Manage resources across different cloud providers (e.g., AWS, Azure, GCP). Use Ansible to provision and configure cloud resources, ensuring consistent infrastructure management.

These questions and scenarios will help you prepare for an Ansible interview by covering a broad range of topics and practical use cases.
