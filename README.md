﻿python-client
=============

Client in Python that allows to send SMS messages and managing account in SMSAPI.com service.
Klient napisany w języku Python, pozwalający na wysyłanie wiadomości SMS, MMS, VMS oraz zarządzanie kontem w serwisie SMSAPI.pl

EXAMPLES:
```python
    from smsapi.client import SmsAPI
    from smsapi.responses import ApiError
    
    
    api = SmsAPI()
    
    api.set_username('YOUR USERNAME')
    api.set_password('YOUR PASSWORD')

    #sending SMS
    try:
        api.service('sms').action('send')
    
        api.set_content('Hello [%1%] [%2%]')
        api.set_params('name', 'last name')
        api.set_to('60xxxxxxx')
        api.set_from('Info') #Pole nadawcy lub typ wiadomość 'ECO', '2Way'
    
        result = api.execute()
    
        for r in result:
            print r.id, r.points, r.status
    
    except ApiError, e:
        print '%s - %s' % (e.code, e.message)
```

Przykład zmiany adresu serwera na zapasowy:

```python
    api = SmsAPI()
    api.set_hostname('https://api2.smsapi.pl/') #Zapasowy serwer
```

## LICENSE
[Apache 2.0 License](https://github.com/smsapi/smsapi-python-client/blob/master/LICENSE)


## INFO ABOUT DEPRECATED MODULES
Module for phonebook endpoints is deprecated, please use https://github.com/smsapi/smsapi-contacts-python-client