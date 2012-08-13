```
// Copyright 2012, Nick Drost - Sales Engineering, Salesforce.com Inc.
// All rights reserved.
//
// Redistribution and use in source and binary forms, with or without
// modification, are permitted provided that the following conditions are met:
//
// - Redistributions of source code must retain the above copyright notice,
//   this list of conditions and the following disclaimer. 
// - Redistributions in binary form must reproduce the above copyright notice, 
//   this list of conditions and the following disclaimer in the documentation
//   and/or other materials provided with the distribution.
// - Neither the name of the salesforce.com nor the names of its contributors
//   may be used to endorse or promote products derived from this software
//   without specific prior written permission. 
//
// THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
// AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
// IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
// DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE
// FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
// DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
// SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
// CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
// OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
// OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```
Facebook/Force.com/Heroku sample app -- Ruby
============================================

This is a sample Facebook app showing use of the Force.com REST API, written in Ruby, designed for deployment to [Heroku](http://www.heroku.com/).

This app was shown at my Cloudstock 2012 session 'Create a Force.com-Powered Facebook App on Heroku'. [Presentation slides](https://github.com/metadaddy-sfdc/Facebook-Sinatra-Force.com-Heroku/blob/master/CS12_Heroku_Facebook.pdf?raw=true).

Run locally
-----------

Install dependencies:

    bundle install

[Create an app on Facebook](https://developers.facebook.com/apps) and set the Website URL to `http://localhost:5000/`.

Copy the App ID and Secret from the Facebook app settings page into your `.env`:

    echo FACEBOOK_APP_ID=12345 >> .env
    echo FACEBOOK_SECRET=abcde >> .env
    
[Create a remote access app in your org](https://login.salesforce.com/help/doc/en/remoteaccess_about.htm) on Force.com and set the Website URL to `http://localhost:5000/`.

Copy the Consumer Key and Secret, and the username and password of an API user, from the Force.com remote app settings page into your `.env`:

        echo SFDC_OAUTH_CLIENT_ID=67890 >> .env
        echo SFDC_OAUTH_CLIENT_SECRET=fghij >> .env
        echo USERNAME=apiuser@example.com >> .env
        echo PASSWORD=******** >> .env

Launch the app with [Foreman](http://blog.daviddollar.org/2011/05/06/introducing-foreman.html):

    foreman start

Deploy to Heroku
----------------

If you prefer to deploy yourself, push this code to a new Heroku app on the Cedar stack, then copy the IDs, secrets and credentials into your config vars:

    heroku create --stack cedar
    git push heroku master
    heroku config:add FACEBOOK_APP_ID=12345 FACEBOOK_SECRET=abcde \
        SFDC_OAUTH_CLIENT_ID=67890 SFDC_OAUTH_CLIENT_SECRET=fghij USERNAME=apiuser@example.com \
        PASSWORD=********

Enter the URL for your Heroku app into the Website URL section of the Facebook app settings page, then you can visit your app on the web.

