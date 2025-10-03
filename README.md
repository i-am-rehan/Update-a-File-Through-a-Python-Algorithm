# Activity: Update a File Through a Python Algorithm

## 📌 Project Description
This project demonstrates how to use Python to automate the process of updating an **allow list** file.  
The algorithm:
- Reads IP addresses from a text file  
- Removes unauthorized IPs  
- Updates the file with the revised list  

This type of automation helps security analysts manage access controls efficiently.

🔗 **Full Documentation:** [View Google Doc](https://docs.google.com/document/d/1D2DvZv0VpKi6M-xlC4zP9SPZpbmZ0b-8m2Gs_jdvChw/edit?usp=sharing)

---

## 🛠️ Python Code

```python
# Activity - Create Another Algorithm
# Author: Rehan
# Description: Parses an allow list of IP addresses and removes unauthorized ones.

def update_file(import_file, remove_list):
    """Reads a file of allowed IPs, removes the ones in remove_list, and rewrites the file."""
    
    # Step 1: Read contents of the file
    with open(import_file, "r") as file:
        ip_addresses = file.read()

    # Step 2: Convert file content into a list
    ip_addresses = ip_addresses.split()

    # Step 3: Remove disallowed IPs
    for element in ip_addresses:
        if element in remove_list:
            ip_addresses.remove(element)

    # Step 4: Convert list back into string
    ip_addresses = " ".join(ip_addresses)

    # Step 5: Rewrite the file with updated IPs
    with open(import_file, "w") as file:
        file.write(ip_addresses)


# Example run
if __name__ == "__main__":
    import_file = "allow_list.txt"
    remove_list = ["192.168.25.60", "192.168.140.81", "192.168.203.198"]

    # Update file with function
    update_file(import_file, remove_list)

    # Verify update
    with open(import_file, "r") as file:
        text = file.read()

    print("✅ Updated allow list:\n", text)

```
    
## 🔑 Explanations of Key Syntax and Functions

- with statement & open() → Safely opens and closes files in read (`"r"`) and write (`"w"`) mode.

- .read() → Reads the file contents as a string.

- .split() → Splits a string into a list (used to separate IP addresses).

- for loop → Iterates through the list of IPs to check each one.

- .remove() → Deletes specific IPs from the list.

- .join() → Converts the list back into a string so it can be written back to the file.

Function `update_file()` → Encapsulates the logic so it can be reused easily.
    

## 🎯 Benefits of this Algorithm

- Automates removal of unauthorized IPs

- Prevents manual errors in editing files

- Improves security by keeping access lists updated

- Encapsulation in functions → reusable and clean code  


## ✅ Summary

This activity shows how Python can be used by security analysts to automate file parsing, enforce access controls, and streamline security tasks.

By combining file handling, string methods, loops, and functions, we created a repeatable and efficient algorithm that updates IP allow lists without manual effort.
