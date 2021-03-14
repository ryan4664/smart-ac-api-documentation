## Register Device

Registers a device in the database.  

```http
POST /devices/register
```

```javascript
{
  "serial_number": string,
  "registration_date": string,
  "firmware_version": string,
  "secret": string,
}
```

### Success (200)

```javascript
{
  "id" : number,
  "token": string,
}
```

The token in the response body will be a [jwt](https://jwt.io/) and required on subsequent requsts to authenticate with the API. 

### Error (400)

```javascript
{
  "error" : string,
}
```
