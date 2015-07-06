# Introduction #

The `LightOpenIDProvider` class is an OpenID Provider implementation.

It requires PHP >= 5.1.2, or >= 5 with [Hash](http://php.net/hash) extension.
Also, if you aren't running it over https and want to support associations (not required, however recommended), you must have GMP or BCMath extensions. GMP is faster, and is used if available.

# Usage #
The class has to be extended in order to use it -- it offers no predefined interface.
## Functions to implement ##
### Required ###
<dl>
<dt><code>checkid($realm, &amp;$attributes)</code></dt>
<dd>This function should return an identifier (i.e. openid) if the user is authenticated, and false otherwise. <br />
It should check whether the user has allowed to be authenticated with $realm.<br />
If the user wished to send any attributes to the site, they should be put in $attributes. <br />
The function <b>must not</b> interact with the user in any way.</dd>
<dt><code>setup($identity, $realm, $assoc_handle, $attributes)</code></dt>
<dd>Handles user interface if it's needed. <br />
Should ask the user whether he wants to login to <code>$realm</code> using <code>$identity</code>, and providing <code>$attributes</code>. See <code>example-mysql.php</code> for an example interface. <br />
<code>$assoc_handle</code> must be present as <code>openid.assoc_handle</code> in <code>$_GET</code> or <code>$_POST</code> in every request.</dd>
</dl>
### Optional ###
<dl>
<dt><code>setAssoc($handle, $assoc)</code></dt>
<dt><code>getAssoc($handle)</code></dt>
<dt><code>delAssoc($handle)</code></dt>
<dd>Set, retrieve or delete an association. <code>$handle</code> is an association handle returned by <code>assoc_handle()</code>, and <code>$assoc</code> is an array. <br />
Uses PHP Sessions by default.</dd>
<dt><code>assoc_handle()</code></dt>
<dd> Generates an association handle.<br>
</dd>
</dl>

## Single user ##
The `example.php` file contains an single-user implementation that you can use as a simple replacement for phpMyID. It uses HTTP authentication and doesn't support SREG or AX extensions.
To use it from another url, just `include 'example.php';` at the top of it. The script shouldn't interfere with your page until someone tries to authenticate with OpenID.

## Multiple users ##
`example-mysql.php` shows how to use mysql database to provide identities. You can integrate the provider into your website based on that example.

## select\_id ##
If you set `$select_id` flag in the provider, it will return a different XRDS document, stating that:

  1. user will be prompted for his username (hence not needing to provide it in the identity url).
  1. this url does not belong to a user

Because of 2., you can't set select\_id on user's identity urls. If you do, most clients will return an error during verification.

Also, remember to set `$xrdsLocation` for the identity urls, so that select\_id can be disabled there too.