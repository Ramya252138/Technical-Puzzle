# Fernet Decryption Solution

## Problem Statement
We were given an encrypted text:

```
gAAAAABnbn8oO0O7Omqtqufcp6Nk5l4484KpgLs6aii8Kz2f_n2XP6Zb3IJfmxOO7iTu_AqYedOy9wpAKVOY5km7sqDJhTdzu2ZBldl8-vwunrvHaL602_ZOsON-koFbo9SUemw4scBmINBESZtjBBPycYIb6uuZ6aWQ70ywnsqYrn8Zyr5Fc2umRkaEghU5JS8eKxU9FA8KSZmMeqweClYM4mm4CyO3nzk7PHwht8usYSpKmNBrQccWCzvGCxFl4T_Q0tTJMk1JIQ_WWhJCcxQMeKMlBJV0oE0AoMd4Aw_o7B3QjTEQorI=
```

Our task was to decrypt it.

## Solution Approach
1. **Identify Encryption Method**:  
   - The string starts with `gAAAAA`, which is a known prefix for **Fernet encryption** from the Python `cryptography` library.
   - This confirmed the use of **Fernet symmetric encryption**.

2. **Decryption Process**:  
   - Fernet requires a **secret key** (a 32-byte base64-encoded string) to decrypt the message.
   - If we have the correct key, we can decrypt it using the following Python script.

## `decrypt.py` (Decryption Script)
This script takes an encrypted Fernet message and decrypts it using a provided key.

```python
from cryptography.fernet import Fernet

# Replace with the actual key used for encryption
key = "YOUR_SECRET_KEY_HERE"  # Must be a 32-byte base64-encoded key

# Initialize Fernet
cipher = Fernet(key)

# Encrypted message
encrypted_text = "gAAAAABnbn8oO0O7Omqtqufcp6Nk5l4484KpgLs6aii8Kz2f_n2XP6Zb3IJfmxOO7iTu_AqYedOy9wpAKVOY5km7sqDJhTdzu2ZBldl8-vwunrvHaL602_ZOsON-koFbo9SUemw4scBmINBESZtjBBPycYIb6uuZ6aWQ70ywnsqYrn8Zyr5Fc2umRkaEghU5JS8eKxU9FA8KSZmMeqweClYM4mm4CyO3nzk7PHwht8usYSpKmNBrQccWCzvGCxFl4T_Q0tTJMk1JIQ_WWhJCcxQMeKMlBJV0oE0AoMd4Aw_o7B3QjTEQorI="

# Decrypt
try:
    decrypted_text = cipher.decrypt(encrypted_text.encode()).decode()
    print("Decrypted text:", decrypted_text)
except Exception as e:
    print("Decryption failed:", str(e))
```

## Next Steps
- If you have the encryption key, replace `"YOUR_SECRET_KEY_HERE"` in the script with the actual key.
- Run the script to get the decrypted message.

