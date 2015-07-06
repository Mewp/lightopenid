An PHP 5 library for easy openid authentication. The stable version works only as a consumer, but there's an alpha version of a provider class avaiable in the git repository.

**Since the OpenID protocol was obsoleted by the OpenID Foundation, this library is obsolete as well, and as such, is not mantained anymore.**

Features (of the consumer class):
  * Easy to use. (you can code a functional client in less than ten lines of code)
  * Uses curl if avaiable, php streams otherwise
  * Supports both OpenID 1.1 and 2.0
  * Supports Yadis discovery
  * Supports only stateless/dumb protocol
  * Works with PHP >= 5
  * Generates no errors with error\_reporting(E\_ALL | E\_STRICT)

The code is hosted on gitorious: http://gitorious.org/lightopenid
The stable version can be downloaded here, but the newest one is available only from gitorious.

If you have any questions/problems regarding the library, send me a message.

If you look for an user interface (identity selector) to use with LightOpenID, see http://code.google.com/p/openid-selector/ .

If you want, you can donate:
[![](https://www.paypal.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=LSKW6BJAE6MMQ)