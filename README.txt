/// webOS OAuth2 \\\

This Files where downloaded from http://github.com/ioNull/webOS-OAuth2

Forked from http://github.com/fillito/WebOS-OAuth
By: Tsung Wu (ioNull)
E-Mail: i@tsung.bz
Web: http://tsung.bz
Fujian - China
Last Update : 2011 March 13

Description : 
------------

    This is just a small library for making OAuth2 Authentications in Palm WebOS. 
You just have to instantiate it passing a json object with the complete OAuth configurations (authorize Url, accessToken Url, client_id, client_secret) and push it as a normal Mojo Scene. 

The application MUST be configured as a web-application on the server side (non client application).
This library captures the callback redirect url to get the final token to complete the authentication. 


Installation :
-------------

1.  Simple copy and paste All files except the sources.json into your WebOS Application folder. 
2.  Open your application's sources.json file and paste the content of the sources.json included in this library

   	 {
        	"scenes": "oauth",
	        "source": "app/assistants/oauth-assistant.js"
	 } 

     So your application can access the library files

3. Simple set up a json object containing the configuration data as shown here and push the oauth Scene

	var oauthConfig={
		callbackScene:'assistantName', //Name of the assistant to be called on the OAuth Success
		authorizeUrl:'http:// -domain- /oauth/authorize',
		accessTokenUrl:'http:// -domain- /oauth/access_token',
		accessTokenMethod:'GET', // Optional - 'GET' by default if not specified
		client_id:' -your client id- ',
		client_secret:' -your client secret- ',
		redirect_uri:'http://www.google.com', // Optional - 'oob' by default if not specified
        response_type:'code', // now only support code
        scope: ['likes','comments','relationships'] //for example, this is instagram scope
	 };
	 Mojo.Controller.stageController.pushScene('oauth',oauthConfig);	
	

Web App Configuration :
----------------------

This library does a little tricky hack so you can make an OAuth Authentication for any OAuth API. 
Some OAuth API offers two types of application authentication : web app & client app.
Client Apps type returns a PIN code that you can use as authentication token, but not all API offers this method. 

This library enable OAuth2 on WebOS ONLY for Web App type Authentication. If you know a little bit about OAuth2, you will realise that web app type needs a Callback URL to return the oauth token as a GET parameter. The trick this library uses, is to capture this token as the server redirects. 

To enable this, the only thing you have to take into account, is to configure your application (registered to access the API) callback URL to redirect to www.google.com.  <----- IMPORTANT !!!!

This library listen the embedded web browser to be redirected to www.google.com/?oauth_token=******* , so you MUST set it so it works.

- Contact me if you have dubts about it -

Comments : 
---------

This is just the first version of this library for instagram. Please, contact me if you need anything related to this library or you want to make any suggestion to improve it.

Thanks for download !!


(CC) 2011 Tsung Wu

Licensed under the Creative Commons, Attribution-ShareAlike 3.0 Unported; 
you may not use this file except in compliance with the License. 
You may obtain a copy of the License at 

     http://creativecommons.org/licenses/by-sa/3.0/

Unless MUTUALLY AGREED TO BY THE PARTIES IN WRITING, licensor offers 
the work "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, 
either express or implied. 
See the License for the specific language governing permissions and 
limitations under the License. 
