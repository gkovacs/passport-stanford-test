A test app for passport-stanford.

Stanford's shibboleth implementation is undocumented and gives absolutely no error messages so it took me 2 days of debugging to get it to work so I would strongly recommend using anything other than shibboleth (ie, facebook connect and google oauth are much better documented and far easier to set up and actually give useful error messages) however here is the process if you decide you absolutely need to use stanford's shibboleth implementation

If using nodejs with express:

clone my repo at https://github.com/gkovacs/passport-stanford-test and edit the variables in app.js to replace the hostname with your own, then deploy the app at  to heroku

visit https://passport-stanford-test.herokuapp.com/metadata (substitute URL with wherever you deployed your app) and copy the XML there

now visit https://spdb.stanford.edu and paste the resulting XML in your app registration. it says you need to be a faculty or staff to do the registration, in reality they apparently didn't implement that check correctly as I was able to do it so ignore the warning

for login url, enter https://passport-stanford-test.herokuapp.com/login

now wait 15 minutes and visit your app and pray that the login works. if you get a white screen instead of the login page try substituting prod with  in the saml configuration, if the latter works but the former doesn't then you screwed up something in the registration process, if the latter doesn't work either then double-check that your passport-saml configuration is correct.

