# instagram_scraper
<img src="https://raw.githubusercontent.com/realsirjoe/designs/master/flat_illustration.png" align="right">
This is a minimalistic Instagram scraper written in Python.
<br /><br />
It can fetch media, accounts, videos, comments etc.
`Comment` and `Like` actions are also supported.

It is not easy to get Applications approved for Instagram's API therefore I created this tool inspired by [instagram-php-scraper](https://github.com/postaddictme/instagram-php-scraper).
<br /><br />
The goal of this project is to become as minimalistic as possible while still having all the needed functionality so that its easy to add code to it!

Any ⭐️ or contribution is appreciated if you like the project 🤘

## install
Simply run:
```
pip install igramscraper
```

or download the project via git clone and run the following:
```
pip install -r requirements.txt
```

## usages
Some methods do require authentication:
```python

from igramscraper.instagram import Instagram

instagram = Instagram()

# authentication supported
instagram = Instagram()
instagram.with_credentials('username', 'password')
instagram.login()

account = instagram.get_account_by_id(3)
# Available fields
print('Account info:')
print('Id', account.identifier)
print('Username', account.username)
print('Full name', account.full_name)
print('Biography', account.biography)
print('Profile pic url', account.get_profile_pic_url_hd())
print('External Url', account.external_url)
print('Number of published posts', account.media_count)
print('Number of followers', account.followed_by_count)
print('Number of follows', account.follows_count)
print('Is private', account.is_private)
print('Is verified', account.is_verified)
# or simply for printing use 
print(account)
```
If you use authentication, the program will cache the user session by default so one doesn't need to create session every time.  
If one want to disable the user session cache, assign `True` to Instagram.login() method

Two Factor Authentication is also supported through cli interface, simply use 'True' for second argument of login() function 
  
Many of the methods do not require authentication

for more info browse through the examples folder

Using proxy for requests:
```python
from igramscraper.instagram import Instagram 

proxies = {
    'http': 'http://123.45.67.8:1087',
    'https': 'http://123.45.67.8:1087',
}

instagram = Instagram()
instagram.set_proxies(proxies)

account = instagram.get_account('kevin')
print(account.identifier)
```

## more usages
See examples [here](https://github.com/SergioWagenleitner/instagram-scraper/tree/master/examples).

## other
instagram-php-scraper [here](https://github.com/postaddictme/instagram-php-scraper/tree/master/examples).
