# 🚀 Vagrant VM Commands Cheat Sheet


### Lifecycle Commands

| Command                      | Description                                         |
| ---------------------------- | --------------------------------------------------- |
| `vagrant init box-name]`     | Creates a new `Vagrantfile` in current directory    |
| `vagrant up`                 | Starts and provisions the Vagrant environment       |
| `vagrant halt`               | Shuts down the running machine                      |
| `vagrant reload`             | Restarts VM and applies any new Vagrantfile changes |
| `vagrant suspend`            | Suspends the VM (saves state to disk)               |
| `vagrant resume`             | Resumes a suspended VM                              |
| `vagrant destroy`            | Stops and deletes all resources created during `up` |
| `vagrant reload --provision` | Reload and force reprovision the machine            |


### 📦 Box Management

| Command                                             | Description                           |
| --------------------------------------------------- | ------------------------------------- |
| `vagrant box list`                                  | Lists all downloaded boxes            |
| `vagrant box add <name> <url>`                      | Adds a new box                        |
| `vagrant box update`                                | Updates the box to the latest version |
| `vagrant box outdated`                              | Checks if box has updates             |
| `vagrant box remove <name>`                         | Removes a downloaded box              |
| `vagrant box repackage <name> <provider> <version>` | Repackages a box (for redistribution) |


### ⚙️ Provisioning

| Command                           | Description                                      |
| --------------------------------- | ------------------------------------------------ |
| `vagrant provision`               | Runs the provisioners defined in `Vagrantfile`   |
| `vagrant reload --provision`      | Reloads VM and provisions it                     |
| `vagrant up --provision`          | Starts and provisions                            |
| `vagrant --provision-with <name>` | Runs specific provisioner (e.g., shell, ansible) |


### 🔍 Information & Debugging

| Command                 | Description                                        |
| ----------------------- | -------------------------------------------------- |
| `vagrant status`        | Shows current state of the VM                      |
| `vagrant global-status` | Shows status of all Vagrant environments on system |
| `vagrant ssh`           | SSH into the running Vagrant machine               |
| `vagrant ssh-config`    | Outputs SSH config (useful for external SSH tools) |
| `vagrant version`       | Shows installed version of Vagrant                 |
| `vagrant --debug`       | Runs any command in debug mode                     |
| `vagrant validate`      | Validates the `Vagrantfile` for syntax errors      |


### 🔌 Plugin & Environment Management

| Command                             | Description                                        |
| ----------------------------------- | -------------------------------------------------- |
| `vagrant plugin list`               | Lists installed plugins                            |
| `vagrant plugin install <plugin>`   | Installs a plugin                                  |
| `vagrant plugin uninstall <plugin>` | Uninstalls a plugin                                |
| `vagrant plugin update`             | Updates all plugins                                |
| `vagrant plugin expunge --force`    | Removes all plugins (reset state)                  |
| `VAGRANT_HOME=/path`                | Sets custom path for Vagrant environment (env var) |


### 🧵 Snapshots (Save/Restore VM States)

| Command                           | Description                             |
| --------------------------------- | --------------------------------------- |
| `vagrant snapshot save <name>`    | Saves current state with given name     |
| `vagrant snapshot list`           | Lists all saved snapshots               |
| `vagrant snapshot restore <name>` | Restores VM to that snapshot            |
| `vagrant snapshot delete <name>`  | Deletes snapshot                        |
| `vagrant snapshot pop`            | Restores latest snapshot and deletes it |
| `vagrant snapshot push`           | Takes temporary snapshot (stack-based)  |


### 🧹 Cleanup & Forced Operations

| Command                         | Description                               |
| ------------------------------- | ----------------------------------------- |
| `vagrant destroy -f`            | Forces destroy without confirmation       |
| `vagrant halt -f`               | Forces shutdown                           |
| `vagrant box prune`             | Removes old versions of installed boxes   |
| `vagrant global-status --prune` | Cleans invalid entries from global status |


### 🖥️ Provider-Specific Operations

| Command                              | Description                                   |
| ------------------------------------ | --------------------------------------------- |
| `vagrant up --provider=virtualbox`   | Specifies provider (VirtualBox, VMware, etc.) |
| `vagrant package`                    | Packages the current VM into a reusable box   |
| `vagrant reload --provider=hyperv`   | Reloads VM with specific provider             |
| `vagrant halt --provider=virtualbox` | Halts VM using specified provider             |
| `vagrant up --parallel`              | Starts multiple machines in parallel          |


### 🌐 Sharing (Remote Access to VM)

| Command                        | Description                                  |
| ------------------------------ | -------------------------------------------- |
| `vagrant share`                | Creates a publicly accessible URL to your VM |
| `vagrant connect`              | Connects to a shared Vagrant environment     |
| `vagrant share --ssh`          | Shares SSH access                            |
| `vagrant share --http 8080`    | Shares HTTP port over share service          |
| `vagrant share --disable-http` | Disables HTTP sharing                        |


### 🌍 Networking & Port Forwarding

| Command                                                     | Description                               |
| ----------------------------------------------------------- | ----------------------------------------- |
| `config.vm.network "forwarded_port", guest: 80, host: 8080` | Forwards port 8080 on host to 80 on guest |
| `config.vm.network "private_network", type: "dhcp"`         | Enables private DHCP network              |
| `config.vm.network "private_network", ip: "192.168.33.10"`  | Private network with static IP            |
| `config.vm.network "public_network"`                        | Bridges guest network to public interface |
| `vagrant reload`                                            | Must run after network config changes     |
