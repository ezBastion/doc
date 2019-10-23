# Make your first api

## Perequisite

- ezBastion up and running



## Automation script adaptation

### Input

### Output

### Log

## Admin console

- Declare your script.
- Test Bastion and STA (only for the fist api ^^ ).
- Register your first worker.
- Create an end point

### Job

A simple declaration, don't forget to activate it.

**Add test1.ps1 as a job**
<iframe width="640" height="360" src="https://www.youtube.com/embed/SqhZ5o1MK1o?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### Bastion / STA
The easy way to test ezBastion front and authentication service, it's to use the *authorize* end point. If you receive a jwt in *access_token*, it smells good. You can decode this jwt, using https://jwt.io/ 
```powershell
PS C:\> Invoke-RestMethod https://ezbastion.company.ltd/authorize -UseDefaultCredentials


expire_in    : 3600
expire_at    : 1471825528
access_token : slfghqsfjkihgq.swgfsqfdgsfdghsf.sfghsfgqf
token_type   : bearer

```
### Workers

As worker is the service they run your script. Be sure to install all needed sdk on the machine and run the service with a account granted. Add one or more tag, we will need it after.

**Add "pocworker1" worker and create "poc" tag**
<iframe width="640" height="360" src="https://www.youtube.com/embed/EBb47HLt98I?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### End point

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

### Grant an account

**Add a Windows account and link the api**
<iframe width="640" height="360" src="https://www.youtube.com/embed/YkhsE4Gv_ks?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Test it

### Postman

http://www.getpostman.com/

### Powershell

```powershell
PS C:\Users\chavers> Write-Information "test"
```
## Debug

### Log

### Polling

### DB browser

### Debug mode

