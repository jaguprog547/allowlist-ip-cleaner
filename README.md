# allowlist-ip-cleaner
Python script that reads an IP allowlist file and removes suspicious or flagged IP addresses automatically.  Demonstrates basic security automation and file handling used in SOC environments.
screeshot.v
[Before Execution.pdf](https://github.com/user-attachments/files/25875848/Before.Execution.pdf)
##Before Execution
This screenshot shows the original allow_list.txt file before running the Python script.
The file contains multiple IP addresses including those that will be removed.
<img width="847" height="186" alt="image" src="https://github.com/user-attachments/assets/35460f18-9bc2-4718-a7f9-760d26d9f80d" />
##Script Execution
 This screenshot shows the Python script being executed from the terminal.
The script reads the allowlist and removes the specified IP addresses.
<img width="827" height="80" alt="image" src="https://github.com/user-attachments/assets/7ec14450-0c3f-4ea7-9543-d83ee752abd2" />
##After Execution
This screenshot shows the updated allow_list.txt file after running the script.
The suspicious IP addresses have been successfully removed.
<img width="925" height="75" alt="image" src="https://github.com/user-attachments/assets/473dd9f1-fcac-435c-ab6d-185fcdbd0d13" />
[ip_allowlist_cleaner.py](https://github.com/user-attachments/files/25876263/ip_allowlist_cleaner.py)
def update_file(import_file, remove_list):

    with open(import_file, "r") as file:
        ip_addresses = file.read()

    ip_addresses = ip_addresses.split()

    for element in ip_addresses:
        if element in remove_list:
            ip_addresses.remove(element)

    ip_addresses = " ".join(ip_addresses)

    with open(import_file, "w") as file:
        file.write(ip_addresses)


remove_list = [
    "192.168.25.60",
    "192.168.140.81",
    "192.168.203.198"
]

update_file("allow_list.txt", remove_list)


with open("allow_list.txt", "r") as file:
    print(file.read())
