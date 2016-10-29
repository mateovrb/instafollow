# instafollow

This scripts help you to grow your instagram account.
The most common way to get followers is to follow a lot of people, 
wait some time and unfollow them, this is what the script does, but automated.

## How it works

We use browser simulator built in javascript, the script logs in 
your account and starts clicking on buttons.

## Dependencies

The scripts only depends the browser simulator called CasperJS:
http://casperjs.org/

To install CasperJS you need a dependency manager called NPM
https://www.npmjs.com/

## Getting started

- Download source files.
- Inside each file, you need to change the first variables
  - login.js
    - YOUR_USERNAME
    - YOUR_PASSWORD
    - ENTER_BUTTON_NAME (Depends on your language, ex: Log In, Entrar, Anmelden)
  - findfollowers.js
    - TAG (The script will follow people using this hashtag)
  - follow.js
    - FOLLOW_BUTTON_NAME (Depends on your language, ex: Follow, Seguir, Folgen)
  - unfollow.js
    - FOLLOW_BUTTON_NAME (Depends on your language, ex: Following, Seguindo)

## Running the scripts

You need to run each script to get the desired behavior

### login.js

`casperjs --verbose  --log-level=debug  --ignore-ssl-errors=true  --ssl-protocol=any --cookies-file=/tmp/cookies test login.js`

This script logs into your account, it is using the file `/tmp/cookies` to store your login information, so you don't need to login
again to perform each action. You will login once, given that the session will expire, will need to run the login again.

### findfollowers.js

`casperjs --verbose  --log-level=debug  --ignore-ssl-errors=true  --ssl-protocol=any --cookies-file=/tmp/cookies test findfollowers.js`

This script will search for your chosen hashtag and store 10 people in the `/tmp/peopletofollow`

### follow.js

`casperjs --verbose  --log-level=debug  --ignore-ssl-errors=true  --ssl-protocol=any --cookies-file=/tmp/cookies test follow.js`

This will open the `/tmp/peopletofollow` file and follow each person.

### unfollow.js
`casperjs --verbose  --log-level=debug  --ignore-ssl-errors=true  --ssl-protocol=any --cookies-file=/tmp/cookies test unfollow.js`

This will open the `/tmp/peopletofollow` file and unfollow each person.
IMPORTANT: Wait some time between follow and unfollow, because it may takes some minutes for people to follow you back. 

### Improve the automation

You can improve doing a shell script that calls every javascript in a loop, example:

```
login

Start forever loop:
  
  find followers
  follow
  wait 20 minutes
  unfollow
  
end loop:
```


