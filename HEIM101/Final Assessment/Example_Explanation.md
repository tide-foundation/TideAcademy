# Exemplar Submission for PlatyPus Passwords Explanation
## Explanation
For too long, Password Managers have required us to remember long complex passwords that hold the key to all of our other passwords. While this does may save us time from remembering all of the other passwords, it produces a massive security risk as seen with the popular password manager LastPass, who recently had all of their users' encrypted passwords stolen. The only thing stopping the attackers from cracking everyone's password, is just the master password the user used - which may not be strong enough. 

Instead of securing all of the users' passwords on PlatyPus Passwords with a long complex master password that the user might forget or leak - the Heimdall SDK was used to authenticate users through Tide and retrieve a secure key using only a basic username and password. Moreover, PlatyPus Passwords server never have access to the user's username, password, plaintext password lists, OR the encryption key for the data it holds, meaning an attacker would gain practically 0 from attacking PlatyPus Passwords' servers.

## Implementation
signIn and signUp functions are used to retrieve users' CVKs and UIDs, which are then stored on the browser for later. The user is always given the option to 'log out' which would clear the browser of the CVK and UID.

Adding a new password:

Instead of requiring a master password to encrypt it, PlatyPus Passwords uses the user's CVK to encrypt (using AES) the new entry (consisting of a website, and the password for that site). After it is encrypted, it is sent to the PlatyPus Passwords servers.

![image](https://user-images.githubusercontent.com/87186823/232673700-a5598d3e-c1a4-4eee-ad3c-8089622b9626.png)

Viewing your passwords:

Using the user's UID and CVK (which should be on the browser since they logged in), the page will request all encrypted data fields for the specified UID. Once all of the data has been returned, the CVK is used to decrypt the data, then display it for the user. All of the data help on PlatyPus Passwords is technically 'public', but will only be able to be decrypted by the correct CVK, which only the user has access to.

![image](https://user-images.githubusercontent.com/87186823/232673648-84a3e548-d6c7-41c2-bdcd-38864012ddcc.png)
