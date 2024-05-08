
# Encryption and Decryption Utility for Node.js

This repository contains utility functions for encrypting and decrypting strings in Node.js using AES encryption. These functions provide a simple yet effective way to secure sensitive data in your applications.

## Encryption Function

The `encrypt` function takes a string as input and encrypts it using AES encryption. It generates a random Initialization Vector (IV) and uses a secret to create a cipher. The encrypted value is returned as a hexadecimal string, combining the IV and encrypted text.

### Code

```typescript
/**
 * Encrypts a string value using AES encryption.
 * @param value The string to encrypt.
 * @returns The encrypted string.
 */
export const encrypt = (value: string) => {
  // Generate Initialization Vector (IV)
  const iv = crypto.randomBytes(16);

  // Create cipher using AES algorithm and secret.
  const cipher = crypto.createCipheriv(algorithm, {{SECRET}}, iv);

  // Encrypt the value
  let encrypted = cipher.update(value);
  encrypted = Buffer.concat([encrypted, cipher.final()]);

  // Combine IV and encrypted value and return as hex string
  return iv.toString('hex') + encrypted.toString('hex');
};;

```

## Decryption Function

The `decrypt` function decrypts a string that has been encrypted using AES encryption. It extracts the IV and encrypted text from the input string and uses them along with the secret to create a decipher. The decrypted value is returned as a string.

### Code

```typescript
/**
 * Decrypts a string value encrypted using AES encryption.
 * @param value The encrypted string to decrypt.
 * @returns The decrypted string.
 */
export const decrypt = (value: string): string => {
  // Extract Initialization Vector (IV) and encrypted text
  const iv = value.substr(0, 32);
  const encryptedText = value.substr(32);

  // Create decipher using AES algorithm and secret.
  const decipher = crypto.createDecipheriv(algorithm, {{SECRET}}, Buffer.from(iv, 'hex'));

  // Decrypt the value
  let decrypted = decipher.update(Buffer.from(encryptedText, 'hex'));
  decrypted = Buffer.concat([decrypted, decipher.final()]);

  // Return the decrypted value
  return decrypted.toString();
};


```


## Usage
###  Encryption Function

```typescript
import { encrypt } from './your-utility-folder';

const encryptedValue = encrypt('mySecretData');
console.log(encryptedValue);
```

###  Decryption Function

```typescript
import { decrypt } from './your-utility-folder';

const decryptedValue = decrypt(encryptedValue);
console.log(decryptedValue);
```


## Requirements

- Node.js (version 14 or higher)
- `crypto` module


## Contribution

Contributions are welcome! If you find any issues or have suggestions for improvements, feel free to open an issue or create a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
