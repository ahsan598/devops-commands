# 🛠️ Terraform Commands Cheat Sheet

This is a simple reference for common Terraform CLI commands, perfect for quick use or interview prep.

---

### ✅ Basic Commands

| Command              | What It Does                                                       |
| -------------------- | ------------------------------------------------------------------ |
| `terraform init`     | Sets up Terraform in your project folder (downloads plugins, etc.) |
| `terraform validate` | Checks if your code is correct                                     |
| `terraform plan`     | Shows what Terraform **will do** before doing it                   |
| `terraform apply`    | Makes the changes (creates/updates infrastructure)                 |
| `terraform destroy`  | Deletes everything Terraform created                               |


---

### 🧠 Workspace Commands (For managing different environments like dev/stage/prod)

| Command                             | What It Does                  |
| ----------------------------------- | ----------------------------- |
| `terraform workspace new <name>`    | Create a new environment      |
| `terraform workspace list`          | See all environments          |
| `terraform workspace show`          | Show current environment      |
| `terraform workspace select <name>` | Switch to another environment |
| `terraform workspace delete <name>` | Delete an environment         |



---

### 🗂️ State Management (Tracks what Terraform manages)

| Command                           | What It Does                                                         |
| --------------------------------- | -------------------------------------------------------------------- |
| `terraform show`                  | Shows current state and outputs                                      |
| `terraform state list`            | Lists all resources tracked by Terraform                             |
| `terraform state show <resource>` | Show attributes of a specific resource                               |
| `terraform state mv <old> <new>`  | Moves a resource in the state file                                   |
| `terraform state rm <resource>`   | Removes a resource from the state file (Terraform stops tracking it) |
| `terraform state pull`            | Pull raw state file                                                  |
| `terraform state push`            | Push state file (advanced/manual use)                                |


---

### 📦 Modules (Reusable code blocks)

| Command                   | What It Does                              |
| ------------------------- | ----------------------------------------- |
| `terraform get`           | Downloads the modules used in your config |
| `terraform get --update`  | Updates modules to latest version         |
| `terraform get --upgrade` | Upgrade all providers and modules (preferred over `get --update`) |


---

### 🔁 Resource Importing (Importing cxisting infrastructure)

| Command                               | What It Does                                                                       |
| ------------------------------------- | ---------------------------------------------------------------------------------- |
| `terraform import <type>.<name> <id>` | Brings in existing resource into Terraform control (e.g. an existing AWS instance) |


---

### 📤 Output Management

| Command             | What It Does                                                         |
| ------------------- | -------------------------------------------------------------------- |
| `terraform output`  | Shows the output values defined in config                            |
| `terraform refresh` | Refreshes the state file (not used much anymore—deprecated in v1.6+) |


---

### 🎨 Formatting and Docs

| Command                     | What It Does                                                          |
| --------------------------- | --------------------------------------------------------------------- |
| `terraform fmt`             | Auto-formats your code (clean layout)                                 |
| `terraform-docs markdown .` | Generates README-like docs from your code (requires `terraform-docs` tool installed) |

---

### 🛠️ Debugging & Utilities

| Command               | Purpose                                                               |
| --------------------- | --------------------------------------------------------------------- |
| `terraform console`   | Opens an interactive shell to evaluate expressions and inspect values |
| `terraform graph`     | Generates a DOT format graph of resource relationships                |
| `terraform providers` | Lists all required and installed providers                            |
| `terraform version`   | Displays the current Terraform version                                |
| `terraform config`    | Shows or sets CLI config options (e.g., credentials, settings)        |


📤 Cloud & Backend / State Management (Advanced Use)

| Command                               | Purpose                                                            |
| ------------------------------------- | ------------------------------------------------------------------ |
| `terraform login`                     | Authenticate to Terraform Cloud (stores credentials locally)       |
| `terraform logout`                    | Remove saved credentials for Terraform Cloud                       |
| `terraform state pull`                | Download the raw state from the backend                            |
| `terraform state push`                | Upload a modified state file to the backend (use with caution)     |
| `terraform force-unlock <lock-id>` ⚠️ | Manually remove a stuck state lock (only if you're sure it's safe) |

### ⚠️ Notes:
- `terraform state push` is rarely used — generally only in manual recovery or advanced automation.
- `terraform force-unlock` is risky and should only be used when you're sure no one else is modifying the state.

---

### 🔍 Extra Useful Commands (Nice to know!)

| Command                        | What It Does                                                            |
| ------------------------------ | ----------------------------------------------------------------------- |
| `terraform graph`              | Outputs a graph of your resources (useful for visualizing dependencies) |
| `terraform taint <resource>` ⚠️       | Mark resource for destruction (deprecated; use `-replace`)       |
| `terraform apply -replace="resource"`  | Recreate a specific resource                                    |
| `terraform untaint <resource>` | Removes taint (won’t recreate)                                          |
| `terraform version`            | Shows current Terraform version                                         |
| `terraform providers`          | Lists the providers being used (like AWS, Azure, etc.)                  |


---

### 📚 Pro Tip

Use `make` to group commands into reusable automation tasks.  

➡️ [Learn how to use the Makefile](../automation-snippets/terraform/terraform-makefile-guide.md)



### 🧠 Tips for Interviews

- Understand Terraform State: It's critical to know how Terraform tracks resources.
- Be ready to explain terraform plan vs terraform apply
- Know how to use Workspaces for multi-env setups (like dev/prod)
- Be aware of the purpose of terraform import (bringing unmanaged resources under control)
- Formatting and validation is part of Terraform best practices
- Know the difference between plan, apply, destroy.
- Be able to explain how state works, especially terraform state commands.
- Practice workspace commands if your projects support multiple environments.
- Know how to import existing infra (this shows advanced understanding).
- For CI/CD, make sure you understand init, plan, apply, and backend configuration.
