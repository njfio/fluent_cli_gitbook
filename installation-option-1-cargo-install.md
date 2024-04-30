# Installation Option 1: Cargo Install

1. Run `cargo install`

{% code overflow="wrap" %}
```bash
cargo install --git https://github.com/njfio/fluent_cli.git
```
{% endcode %}

2. This will install the `fluent` executable to

{% code overflow="wrap" %}
```
~/.cargo/fluent
```
{% endcode %}

3. Create a fluent profile directory.

> Creating this directory as a git repository allows your config.json and amber.yaml file to be versioned, protected, and used across any system you want to use `fluent` on.

```
mkdir ~/.fluent_cli
```

4. Download the config.json file from the repository.

[https://github.com/njfio/fluent\_cli/blob/main/fluent\_cli/config.json](https://github.com/njfio/fluent\_cli/blob/main/fluent\_cli/config.json)

5. Copy that file to your fluent\_cli profile path.

```
cp ~/Downloads/config.json ~/.fluent_cli
```

6. If you have not used amber, [https://github.com/fpco/amber](https://github.com/fpco/amber), you need to initialize the repository.

```
cd ~/.fluent_cli
amber init
```

> <mark style="color:orange;">MAKE SURE YOU SAVE THE RESULTING PRIVATE KEY IN A PASSWORD STORE</mark>

7. Create both the two necessary user `env` entries.

```bash
export AMBER_YAML=/path/to/your/user/profile/.fluent_cli/amber.yaml
export FLUENT_CLI_CONFIG_PATH=/path/to/your/user/profile/.fluent_cli/config.json
```
