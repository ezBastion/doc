# Make your first api
**Hello World step by step**

## Perequisite

- ezBastion up and running
- An automation powershell script
- A youtube access to read this page.



## Automation script adaptation

**A incredible "hello world" in powershell, will be our automation script who need api**
<iframe width="640" height="360" src="https://www.youtube.com/embed/BWTGAsUUxaM?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Input

By defaut ezBastion push routing information to the script. You can use this information, using some variables:
```powershell
[CmdletBinding()]
param (
    $tokenid,
    $methode,
    $tag,
    $path,
    $version,
    $query,
    $constant,
    $xtrack,
    $body
)
```
Variables, tags, path, query, constant and body, are json string. You must unserialize it befor use.

### Output

ezBastion worker waiting for script output, a json or empty string or error on stderr channel. Json produce a http 200 code, empty output a http 204 (no content) and a error produce a http 500.

If $out exist return a json (http 200) or nothing (http 204)
```powershell
try {
    your code here
}
catch {
    write-error $_
}
finally{
  if ($out) {
      $out | convertto-Json -Compress 
  }
}
```


## Admin console

- Declare your script.
- Test Bastion and STA (only for the fist api ^^ ).
- Register your first worker.
- Create an end point.
- Link this endpoint to user account.

### 1 Job

A simple declaration, but don't forget to activate it.

**Add test1.ps1 as a job**
<iframe width="640" height="360" src="https://www.youtube.com/embed/SqhZ5o1MK1o?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 2 Bastion / STA
The easy way to test ezBastion front and authentication service, it's to use the *authorize* end point. If you receive a jwt in *access_token*, it smells good. You can decode this jwt, using https://jwt.io/ 
```powershell
PS C:\> Invoke-RestMethod https://ezbastion.company.ltd/authorize -UseDefaultCredentials


expire_in    : 3600
expire_at    : 1471825528
access_token : slfghqsfjkihgq.swgfsqfdgsfdghsf.sfghsfgqf
token_type   : bearer

```
### 3 Workers

As worker is the service they run your script. Be sure to install all needed sdk on the machine and run the service with a account granted. Add one or more tag, we will need it after.

**Add "pocworker1" worker and create "poc" tag**
<iframe width="640" height="360" src="https://www.youtube.com/embed/EBb47HLt98I?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 4 End point

Where we link all. We will generate a unique URL for this api. But first, take a look at ezBastion end point format:
![ ](https://github.com/ezBastion/doc/raw/master/image/api-url.jpg)

we can split this url in seven parts, ezBastion use it to route the api.

- GET: REST methode used.
- https: scheme or protocol used.
- api.ezbastion.com: bastion dns name.
- v1: api version.
- controller: name use in routing system.
- action: same as controller, it's a legacy of MVC model.
- path: some static or variables items need by the script.
- query: a other way to provide items to script.

**Add an api end point https://api.ezbastion.com/v1/poc/test**
<iframe width="640" height="360" src="https://www.youtube.com/embed/iPObw6jC9xo?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 5 Grant an account

**Add a Windows account and link the api**
<iframe width="640" height="360" src="https://www.youtube.com/embed/YkhsE4Gv_ks?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Test it

- call authorization endpoint to get a bearer token, with basic or NTLM auth
- call our api using this token as bearer authentication

### With Postman

Postman is a very popular rest (http) client based on chrome. http://www.getpostman.com/

<iframe width="640" height="360" src="https://www.youtube.com/embed/Aavjbiw68X4?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### With Powershell

The same using 4 lines of powershell:
```powershell
PS C:\> $bastion = "http://CHAVERS-DESK:5505"
PS C:\> $b = Invoke-RestMethod "$bastion/authorize"  -UseDefaultCredentials 
PS C:\> $h = @{authorization = $b.token_type + " " + $b.access_token}
PS C:\> Invoke-RestMethod -Headers $h -Uri "$bastion/v1/poc/test"
hello world!

PS C:\> 
```

## Debug

If you have some issue to integrate your existing powershell scripts.

### Runas
On the worker machine, start a powershell using the service account used by ezb_wks service. And try to run the script manually.

### Log
Have a look in the worker log folder. Do the same with bastion (ezb_srv) log.

### DB browser
You can refer to "log" table where all api request information are logged.
with:
- date
- status
- client ip address
- token (user accoçunt)
- controller/action
- full url
- bastion and worker used
- duration
- error message *normally null ;-)*


