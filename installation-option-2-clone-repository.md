# Installation Option 2: Clone Repository

These steps are very similar to option 1.

1. **Clone the repository:**

```bash
git clone https://github.com/yourgithub/fluent_cli.git
```

2. **Navigate to the FluentCLI directory:**

```bash
cd fluent_cli
```

3. **Build the application:**

```bash
cargo build --release
```

4. Create the profile directory and copy the necessary files

```bash
mkdir ~/.fluent_cli
copy /path/to/your/fluent_cli/repo/fluent_cli/target/release/fluent ~/.fluent_cli
copy /path/to/your/fluent_cli/repo/fluent_cli/config.json ~/.fluent_cli
copy /path/to/your/fluent_cli/repo/fluent_cli/fluent_cli_autocomplete.sh ~/.fluent_cli
```

5. If you have not used amber, [https://github.com/fpco/amber](https://github.com/fpco/amber), you need to initialize the repository.

```
cd ~/.fluent_cli
amber init
```

> <mark style="color:orange;">MAKE SURE YOU SAVE THE RESULTING PRIVATE KEY IN A PASSWORD STORE</mark>

6. Create both the two necessary user `env` entries.

```bash
export AMBER_YAML=/path/to/your/user/profile/.fluent_cli/amber.yaml
export FLUENT_CLI_CONFIG_PATH=/path/to/your/user/profile/.fluent_cli/config.json
```
