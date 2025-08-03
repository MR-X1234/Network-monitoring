# Network-monitoring
Check connectivity between host it's reachable or not
automation for ping command

import subprocess
import platform

# Get user input
source_ip = input("Enter source IP (for your reference only): ")
destination_ip = input("Enter destination IP or hostname to ping: ")

# Determine ping count option based on OS
ping_count_option = "-n" if platform.system().lower() == "windows" else "-c"

print(f"\nChecking connectivity from {source_ip or 'this system'} to {destination_ip}...\n")

# Run the ping command
try:
    result = subprocess.run(
        ["ping", ping_count_option, "3", destination_ip],
        stdout=subprocess.PIPE,
        stderr=subprocess.PIPE,
        text=True
    )

    if result.returncode == 0:
        print("✅ Ping successful!")
    else:
        print("❌ Ping failed!")

    print("\n--- Ping Output ---")
    print(result.stdout)

except Exception as e:
    print(f"⚠️ Error: {e}")

Output : 

Enter source IP (for your reference only): 192.168.1.10
Enter destination IP or hostname to ping: 8.8.8.8

Checking connectivity from 192.168.1.10 to 8.8.8.8...

✅ Ping successful!

--- Ping Output ---
PING 8.8.8.8 (8.8.8.8): 56 data bytes
64 bytes from 8.8.8.8: icmp_seq=0 ttl=118 time=11.003 ms
...
