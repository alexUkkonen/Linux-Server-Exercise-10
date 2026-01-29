# Linux-Server-Exercise-10

## passwords answers (Exerpt from exercise 9)

The data is stored in 3 separate places.

the first one is /etc/passwd despite the name passwd contains no passwords. This file contains the user id (UID) group id (GID) and their home/shell aka their home directory and terminal enviorment.

bellow you will find an image of the contents. the x stands for password witch is encrypted in /etc/shadow.

the first numbers are UID and the second GID

<img width="609" height="85" alt="image" src="https://github.com/user-attachments/assets/2894979a-87ef-4ede-92d9-17a5475da093" />

in shadow like mentioned you can see the passwords. these are only visible to the root users.

the ! in this image means that we haven't sett a password.

<img width="420" height="110" alt="image" src="https://github.com/user-attachments/assets/86035087-f00b-4b30-a7be-f664320c3245" />

letts add passwords to the users. We can't do it directly in to the shadow file as what it stores is the hash of the password, and if we sett a password like "pass123" it would limply lock the account as that isn't a viable hash.

to do it propperly we can as the root user type "$ sudo passwd [username]"

<img width="593" height="312" alt="image" src="https://github.com/user-attachments/assets/65fadedb-75ab-4ded-b17e-937c4ceb2b94" />

now we can look at the hashed password in shadow again:

<img width="1488" height="61" alt="image" src="https://github.com/user-attachments/assets/5382af11-7b3d-47f2-9a1d-1dc043692f74" />

For reference the passwords i used for the users are user1pass and user2pass respectively.

If we take a closer look at the hash you will notice that both start the same.

$y$j9T$ To brake this down the $y$ means we used Yescrypt to encrypt the password, Yescrypt is a more modern encryptin method compared to SHA-512 (
6
). It is much harder to crack.

the j9T$ tells us how much ram/cpu time was used to create the hash. everything after the last $ is the salted has itself.

Salted means that a random string of characters was added in from to enshure that 2 identical passwords look different in hashed form.

the last file containing information on the user is the /etc/group file. This file contains info about the groups and their members. this file can be read by everyone.

<img width="405" height="114" alt="image" src="https://github.com/user-attachments/assets/a09f5e6c-3cf4-4979-af43-78c937f8ee6b" />

## Permissions

1. we make the directory with the "mkdir" command

<img width="913" height="214" alt="image" src="https://github.com/user-attachments/assets/f5423925-80e8-4e98-81d6-c1bb127449ce" />

2. We made the file using nano and inputted the text "this is a secret file"

3. We changet the permission to 600 meaning only i (and root users) can read and write in the file.

<img width="810" height="338" alt="image" src="https://github.com/user-attachments/assets/3bb35487-2572-46b7-91f7-bc2d53d163e6" />

4. We add a file the same way that is called public.txt, with the text "this is a public file" inside of it.

We then change the perms the same way

<img width="836" height="377" alt="image" src="https://github.com/user-attachments/assets/aa3e944f-1b8b-46f6-97f0-ea8eb6664a61" />
