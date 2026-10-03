# Linux System Reconnaissance Cheat Sheet

## 1. System & OS Information
*   `cat /etc/os-release` : Display distribution name, version, and OS details.
*   `uname -a` : Print kernel version, architecture, and system hostname.
*   `hostnamectl` : Show detailed system, OS, and hardware info.
*   `uptime` : Show system uptime and current system load averages.
*   `lscpu` : Display CPU architecture, cores, and threads.
*   `free -h` : Show RAM and swap memory usage in human-readable format.
*   `df -h` : Display disk space usage for all mounted filesystems.
*   `lsblk` : List all block devices (storage drives and partitions).

## 2. Network Configuration
*   `ip a` : Show all network interfaces, MAC addresses, and assigned IP addresses.
*   `ip route` : Display the IP routing table and default gateway.
*   `ss -tulnp` : List all active listening TCP/UDP ports and the processes using them (run with `sudo` to see all PIDs).
*   `nmcli device show` : Display detailed status and configuration of all network interfaces via NetworkManager.
*   `resolvectl status` : View current DNS servers and resolution configuration per interface.

## 3. Wi-Fi & Saved Passwords (Requires `sudo`)
*   `sudo nmcli device wifi show-password` : Display the plaintext password and a QR code for the active Wi-Fi connection.
*   `sudo nmcli connection show` : List the names (SSIDs) of all saved network connection profiles.
*   `sudo nmcli connection show "<SSID_Name>" -s | grep 802-11-wireless-security.psk` : Extract the plaintext password for a specific saved Wi-Fi network.
*   `sudo grep -r '^psk=' /etc/NetworkManager/system-connections/` : Bulk print the plaintext passwords for all saved Wi-Fi network profiles.

## 4. Running Processes & Services
*   `top` : Real-time, interactive monitor for system processes, CPU, and memory usage.
*   `ps aux` : Complete snapshot of all currently running processes across all users with full command lines.
*   `systemctl list-units --type=service --state=running` : List all active, running background systemd services.
*   `sudo lsof -i -P -n` : List all open network connections, ports, and the specific processes tied to them.
*   `kill -9 <PID>` : Forcefully terminate a specific process by its Process ID.

## 5. User Identity & Sessions
*   `whoami` : Print the current logged-in username.
*   `id` : Show the current user ID (UID), group ID (GID), and all group memberships.
*   `w` : Show who is currently logged in, their terminal, and what command they are running.
*   `last -a` : Display a history of recent user logins, logouts, and system reboots.
