# NativeScript Active Directory Authentication Library Plugin


This plugin allows you to quickly add Azure Active Directory Authentication to your NativeScript app
Thanks to NavaraBV

## Prerequisites / Requirements

Your application requires to be registered inside your Azure Active Directory (AAD). Visit the [Azure Portal](https://portal.azure.com) and log in with your organizational account. Grab your Azure AD Tenant ID and Application ID after registering your application.
The ReplyUrl of your Azure SPA must be urn:ietf:wg:oauth:2.0:oob

## Installation

```javascript
tns plugin add @aminebizid/nativescript-adal
```

## Usage (Angular example)

Import the AdalContext class in application in, for example, an 'AdalService' and initialize it.

```javascript
import { Injectable } from '@angular/core';
import { AdalContext } from '@aminebizid/nativescript-adal';

const authority: string = 'https://login.microsoftonline.com/{your-tenant-id}';
const clientId: string = '{your-application-id}';
const resourceId: string = '00000002-0000-0000-c000-000000000000';

@Injectable()
export class AdalService {

  public adalContext: AdalContext;

  constructor() {
    this.adalContext = new AdalContext(authority, clientId, resourceId);
  }
}
```

...and consume this service in your application!

```javascript
export class AppComponent {

  constructor(private adalService: AdalService) { }

  public login() {
    this.adalService.adalContext.login().then((result) => {
      console.log('Success!');
    })
  }

  public logout() {
    this.adalService.adalContext.logout();
  }
}
```


    
## License

See [LICENSE](LICENSE) for details.
