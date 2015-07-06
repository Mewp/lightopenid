OpenID has two extensions, called AX and SREG that allow getting more information about an user when authenticating. These extensions are supported.
To use them, specify $openid->required and/or $openid->optional before calling $openid->authUrl().
These are arrays, with values being AX schema paths (the 'path' part of the URL).
For example:
> $openid->required = array('namePerson/friendly', 'contact/email');
> $openid->optional = array('namePerson/first');

Since AX attributes are a superset of SREG attributes, they are automatically translated in LightOpenID, so that you don't have to know anything about SREG.

As for the AX attributes, they are defined at [axschema.org](http://www.axschema.org/types/), But here's a list of the more common ones (copied from axschema.org):
| **Name**              | **Meaning** |
|:----------------------|:------------|
| namePerson/friendly   | Alias/Username |
| contact/email         | Email       |
| namePerson            | Full name   |
| birthDate             | Birth date  |
| person/gender         | Gender      |
| contact/postalCode/home | Postal code |
| contact/country/home  | Country     |
| pref/language         | Language    |
| pref/timezone         | Time zone   |

Note that even if you mark some field as required, there is no guarantee that you'll get any information from a provider. Not all providers support all of these attributes, and some don't support these extensions at all.

Google, for example, completely ignores optional parameters, and for the required ones, it supports, according to [it's website](http://code.google.com/apis/accounts/docs/OpenID.html):
  * namePerson/first (first name)
  * namePerson/last (last name)
  * contact/country/home
  * contact/email
  * pref/language