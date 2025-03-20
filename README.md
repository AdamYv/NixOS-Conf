# NixOS-Conf
My `configuration.nix` file, just in case.

## NixOS Command Cheat Sheet

### Package Management

- **Install:**
  ```bash
  nix-env -iA nixos.curl
  ```

- **Search:**
  ```bash
  nix-env -qaP 'curl'
  ```

- **Update an installed package:**
  ```bash
  nix-env -u
  ```

- **Uninstall a package:**
  ```bash
  nix-env -e curl
  ```

- **List my packages:**
  ```bash
  nix-env -q
  ```

### System Management

- **Change generation (configuration version):**
  ```bash
  sudo nixos-rebuild switch --upgrade
  ```

- **Rollback:**
  ```bash
  sudo nixos-rebuild switch --rollback
  ```

- **Build and test a config:**
  ```bash
  sudo nixos-rebuild build
  ```

- **Apply the config:**
  ```bash
  sudo nixos-rebuild switch
  ```

- **Clean the last generation:**
  ```bash
  sudo nix-collect-garbage -d
  ```

### Channel Management

- **Add a channel:**
  ```bash
  sudo nix-channel --add <channel_url>
  ```

  Example:
  ```bash
  sudo nix-channel --add https://nixos.org/channels/nixos-unstable
  ```

- **Update channels:**
  ```bash
  sudo nix-channel --update
  ```

- **List channels:**
  ```bash
  nix-channel --list
  ```

- **Remove a channel:**
  ```bash
  sudo nix-channel --remove <channel_name>
  ```

### Development and Environments

- **Enter a shell (like Fedora Kinoite ToolBox):**
  ```bash
  nix-shell -p python38
  ```

- **Create a reproducible development environment:**
  Create a `shell.nix` file with the necessary dependencies, then run:
  ```bash
  nix-shell
  ```

### Other Useful Commands

- **View available configuration options:**
  ```bash
  nixos-option <option>
  ```

  Example:
  ```bash
  nixos-option services.nginx.enable
  ```

- **Generate hardware configuration:**
  ```bash
  sudo nixos-generate-config
  ```

- **Build an ISO image:**
  ```bash
  nix-build '<nixpkgs/nixos>' -A config.system.build.isoImage -I nixos-config=<configuration_file>
  ```
