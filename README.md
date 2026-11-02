# LIVI-embedded-tablet-install
The **LIVI Tablet Prep Script** automates the initial system configuration of a Dell Latitude 7400 2-in-1 running a minimal Debian Trixie installation, preparing it for use as a dedicated LIVI embedded CarPlay system. It verifies that the `carplay` user exists, installs the required system dependencies, and grants the user sudo privileges. It then modifies GRUB and kernel settings to reduce boot time, suppress unnecessary boot messages, and provide a cleaner, quieter startup experience. The script also removes default login messages and creates a background power-monitoring service that continuously checks the tablet's AC adapter status and automatically shuts down the system when external power is disconnected (with a one-minute startup grace period). Finally, it configures the power monitor to launch automatically at boot and provides instructions for configuring Wi-Fi through NetworkManager. This script is intended to be run as root after a base Debian installation and before running the official LIVI headless installation script as the `carplay` user.

# Before running the script
Install debian using the netinstall image.  I used "debian-13.3.0-amd64-netinst.iso"  
DESELECT "Debian dekstop environment" and "GNOME".  
SELECT "SSH Server" and "Standard System Utilities" only.  

# After running the script
`curl -fL -o install.sh https://raw.githubusercontent.com/f-io/LIVI/main/scripts/install/install.sh`

`chmod +x install.sh`

`./install.sh --headless`

# Auto-Poweron (system dependent)
In the Dell BIOS, you can configure the tablet to power on upon being plugged into a charger (or car turns on and provides power to the charger).  Not sure if other brands have the same feature.  This makes my tablet turn on and launch LIVI upon starting the car, as my car only provides electricity to the charger while it's running.

