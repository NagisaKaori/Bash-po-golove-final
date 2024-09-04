# Bash-po-golove-v2

#!/bin/bash
  for i in(1..10)
    password=$(mysql -u -root -p'root' -e "USE USER_BD, SELECT password FROM USERS where id=$i;")
echo $password

temp_pw=$(echo $password | openssl enc -aes-256-cbc -md sh512 -a -pbkdf2 -iter 10000 -salt -pass pass:Secret@123$)

mysql -u -root -p'root' -e "UPDATE FROM USERS WHERE SET password=$password;"
