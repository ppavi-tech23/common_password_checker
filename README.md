# Password Checker

A simple Python command-line tool that checks if a user-entered password appears in the top 100,000 most common passwords list. Helps identify weak passwords by showing their rank if matched or confirming uniqueness.

## 🚀 Features
- ✅ Reads common passwords from `passwords.txt` (top 100k list from SecLists)
- ✅ Displays match rank with ❌ (e.g., `password: ❌ (#2)`) or ✅ Unique status
- ✅ Efficient early exit on first match using `enumerate()` for 1-based ranking
- ✅ No external dependencies - pure Python 3

## 📋 Quick Start

1. **Setup files**:
   ```bash
   # Rename your paste.txt to passwords.txt
   mv paste.txt passwords.txt

# CHANGE THIS:
with open('passwords.text', 'r') as file:

# TO THIS:
with open('passwords.txt', 'r') as file:

# Run
python main.py

Example output:

text
Enter a password: 123456
123456: ❌ (#1)

Enter a password: MySecurePass123!
MySecurePass123!: ✅ (Unique)
📁 File Structure
text
password-checker/
├── main.py          # Main script
└── passwords.txt    # Common passwords list (~100k entries)
🔧 How It Works
python
def check_password(password: str):
    with open('passwords.txt', 'r') as file:
        common_passwords: list[str] = file.read().splitlines()
    
    for i, common_password in enumerate(common_passwords, start=1):
        if password == common_password:
            print(f'{password}: ❌ (#{i})')
            return
    print(f'{password}: ✅ (Unique)')
⚙️ Customization Options
Feature	Code Change
Case insensitive	password.lower() == common_password.lower()
Return boolean	return True instead of print()
Different wordlist	Replace passwords.txt
🧪 Test Examples
text
123456       → ❌ (#1)
password     → ❌ (#2)  
qwerty       → ❌ (#4)
letmein      → ❌ (#17)
MyStrongPass → ✅ (Unique)
🔒 Security Notes
✅ Uses industry-standard SecLists top 100k passwords

✅ Memory-efficient (~881KB for 100k entries)

⚠️ Production: Add length checks, complexity rules, rate limiting

✅ Perfect for portfolio projects & security demos

📚 Source
Password list from: SecLists 10-million-password-list-top-100000.txt

📄 License
MIT License - Free to use for learning and portfolio projects


