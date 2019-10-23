# Make your first api

## Perequisite

- ezBastion up and running



## Automation script adaptation

### Input

### Output

### Log

## Admin console

- Declare your script.
- Test Bastion and STA (only for the fist api ).
- Register your first worker.
- Create end point

### Job



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

<iframe width="640" height="360" src="https://www.youtube.com/embed/EBb47HLt98I?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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

