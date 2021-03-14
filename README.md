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


## Reauthentice Device
To be used when the token expires (currently expires after 7 days) to authenticate and receieve a new token.  
```http
POST /devices/login
headers: {
    'Authorization': 'YOUR_TOKEN'
}
```
```javascript
{
  "secret": string,
}
```
### Success (200)
```javascript
{
  "token": string,
}
```
### Error (401)
Invalid token.
```javascript
{
  "error" : string,
}
```

### Error (400)
Invalid secret.
```javascript
{
  "error" : string,
}
```

## Update
Inserts a new `device_sensor_data` record.  
```http
POST /devices/update
headers: {
    'Authorization': 'YOUR_TOKEN'
}
```
```javascript
{
  "temp_celsius": string,
  "air_humidity_percentage": string,
  "carbon_monoxide_level": string,
  "status": string,
}
```
### Success (200)

### Error (401)
Invalid token.
```javascript
{
  "error" : string,
}
```

## Update Bulk
Inserts multiple new `device_sensor_data` records.  A maximum of 500 records can be past in.  
```http
POST /devices/update
headers: {
    'Authorization': 'YOUR_TOKEN'
}
```
```javascript
[
  {
    "temp_celsius": string,
    "air_humidity_percentage": string,
    "carbon_monoxide_level": string,
    "status": string,
  },
  {
    "temp_celsius": string,
    "air_humidity_percentage": string,
    "carbon_monoxide_level": string,
    "status": string,
  },
  ...
]
```
### Success (200)

### Error (400)
Occurs when there are too many records or the value passed in is not an array.
```javascript
{
  "error" : string,
}
```

### Error (401)
Invalid token.
```javascript
{
  "error" : string,
}
```
