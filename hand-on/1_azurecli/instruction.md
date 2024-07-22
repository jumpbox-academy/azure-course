# AzureCLI instruction

This instruction is a course material used for practicing.

## Basic section

1. Install Azure cli

   for mac

   ```bash
   brew update && brew install azure-cli
   ```

   for window

   ```bash
   winget install -e --id Microsoft.AzureCLI
   ```

2. Login with interactive mode. In this mode, you need browser to proceed this step.

   ```bash
   az login
   ```

3. Check login session and current subscription.

   ```bash
   # Show current active subscription.
   az account show

   # Check subscription list.
   az account list
   ```

4. Try switch subscription

   ```bash
   az account set <subscription id>
   ```

## Az cli Extension

1. Show current extension

   ```bash
   az extension list
   ```

2. Install or upgrade extension

   Examples.

   ```bash
   # Add a specific version of extension
   az extension add --name <name> --version <version>

   # Upgrade the extension if already installed
   az extension add --name <name> --upgrade

   # Upgrade the extension if already installed
   az extension update --name <name>
   ```

   Install SSH extension

   ```bash
   az extension add --name ssh --upgrade

   az extension add --name interactive --upgrade
   ```
