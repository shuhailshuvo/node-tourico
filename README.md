> Tourico Connector for nodeJs.

This module lets you connect to tourico web services using WSDL. 

- [Install](#install)
- [Usages](#usages)

## Install

Install with [npm](http://github.com/isaacs/npm):

```
  npm install node-tourico
```

## Usages

Require node-tourico

```
  const tourico = require('node-tourico');
```

Create async client:

```
  tourico.createClientAsync(url, user, pass, culture, version)
```

Add headers:

```
  tourico.createClientAsync(url).then((client) => {
    const header = {
      'aut:AuthenticationHeader': {
        'aut:LoginName': user,
        'aut:Password': pass,
        'aut:Culture': culture,
        'aut:Version': version
      }
    };
    tourico.addSoapHeaderAsync(header);
  });
```

Set SOAP Action:

```
  tourico.setSOAPAction(actionUrl);
```

Call API:

```
  const inputs = {
    'hot:SearchHotelsById': {
      'hot:request': {
        'hot1:HotelIdsInfo': '<hot1:HotelIdInfo id="1234"/>',
        'hot1:CheckIn': '2019-04-25',
        'hot1:CheckOut': '2019-04-26',
        'hot1:RoomsInformation': {
          'hot1:RoomInfo': {
            'hot1:AdultNum': 1
          }
        }
      }
    }
  }
  tourico.SearchHotelsByIdAsync(inputs);
```
