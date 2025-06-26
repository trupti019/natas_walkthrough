## Natas 0  Source Code is Everything
View source page and find the password.
![image](https://github.com/user-attachments/assets/e16033d8-c9cf-46de-9d38-1bb8b2ce120f)
Password: 0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq

## Natas1  Don’t Trust the UI
View source page and find the password but the twist is---Right click has been blocked.
Press Ctrl+Shift+I to open the inspect tool and find the password.
![image](https://github.com/user-attachments/assets/947bef2d-1194-44d5-918c-c1174735bffe)
Password: <!--The password for natas2 is TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI -->

## Natas2 Directory Guessing
View source page and find that there’s a folder /files/ on the web root. Inside this folder there’s a file named as users.txt. Open it and find the password.
![image](https://github.com/user-attachments/assets/e942442c-eb7c-4fd1-b776-fcbd5a079945)
Password: 3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH

## Natas3 Hidden in Plain Sight
Source code shows: <!-- No more information leaks!! Not even Google will find this one... -->
Robots.txt? Yes.
Go to /robots.txt → leads to /s3cr3t/
Got to know about robots.txt and how search engines work.
![image](https://github.com/user-attachments/assets/628f7b7e-695c-442e-adce-5e4580dcfef8)
password: QryZXc2e0zahULdHrtHxzyYkj59kUxLQ

## Natas4 Cookies Are Not Just for Snacking
The website checks the **Referer** header to verify if you came from a specific page (`http://natas5.natas.labs.overthewire.org`). If not, access is denied.
Bypass the referrer check and access the password for the next level.
We change that Referer parameter value to Natas5
![image](https://github.com/user-attachments/assets/c24c12da-24d4-4df2-8164-1d703bfbc35e)

## Natas 5
Change cookie loggedin to 1, reload the page and find the password.

## Natas6
On successfully logging in the natas6 webpage, we will have a form in front of us. It says “Input secret:”
![image](https://github.com/user-attachments/assets/dea2b230-65ac-4fc1-9209-6aa981e59852)
![image](https://github.com/user-attachments/assets/c2b995d2-79e4-4d92-8445-14877f3aa9dd)

View source page. Note that the file includes/secret.inc is included in the page. Open it and get the secret.

Input the secret and get the password.

## Natas7
we are given two links, Home and About 

![image](https://github.com/user-attachments/assets/4f4f3442-620b-49d3-8024-2273178700f1)

Here, we can see the links “index.php?page=” in the given image. We have also hinted the location of the password, that is., /etc/natas_webpass/natas8.

![image](https://github.com/user-attachments/assets/4c5817e3-8c3a-4056-8c09-a05b7e147441)

So, we modify the link to read the password stored in the natas_webpass.

//natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8

And we have the password for the next level. This is called command injection.

## Natas8
we will have a form in front of us. It says “Input secret"
![image](https://github.com/user-attachments/assets/cfe36ca6-f8b8-407f-b38d-09254926e81e)

opened the source code and found that the secret is encoded. Also, we have a function which encodes the secret.
Hence to decode the secrete we just create a function that can decode the secret. This can be done as shown in the given image.

![33](https://github.com/user-attachments/assets/1bcfdade-5dde-4d30-882e-c2d630d70b0d)

![image](https://github.com/user-attachments/assets/01b5667c-bf10-43f1-a5c1-88818c958acb)

## Natas 9
we will have a form in front of us. It says “Find words containing” as shown in the figure given below.

![image](https://github.com/user-attachments/assets/e5d2d69d-7257-4f05-8c64-22a71966ae87)

We opened the source code and found that when we enter a keyword, it is passed via a function called passthru(). It takes the value in $key and executes it directly.

![image](https://github.com/user-attachments/assets/0b4aaa1f-7734-4676-8e62-f17df4a6e217)

So, we will use (;) to execute multiple commands. We will try to read the password at the next level.

;cat /etc/natas_webpass/natas10

![image](https://github.com/user-attachments/assets/cdc60d4e-da24-40a0-9827-f5330ba2a8a9)

## Natas 10

Comparing to Natas 9, this challenge filters the key characters to command injection. However, we could take advantage of the grep command to print the password.

Note that the command line grep -i <word> <file 1> <file 2> ... <file n> will print every line in each file that contains the . Thus, we could compile such command and go through the 26 letters and their capitalized format to find a ‘matched letter’ to the password.

For this challenge, we could input c /etc/natas_webpass/natas11 and print the password out.


![image](https://github.com/user-attachments/assets/66c28120-16eb-4909-b0bf-6ed67d96c665)





