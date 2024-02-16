OAuth 2 Grant Types:

	The Authorization Code Grant
		
		1. user sign up to your app
		2. your app provide different provider such as google, facebook and etc
		3. you choose one provider for example google
		3. app send request with it client id to google service
		4. google ask user to authenticate and accept authorization to share data with app
		5. user authenticate with his/her credential
		6. google give authorization code to app
		7. app give the recently authorization code with secret key
		8. google share access token with app
		9. app get account or profile info using access token
		
	
	The Client Credentials Grant
	
		0. The Client Credentials Grant involves machine to machine authentication.
			In case of Client credentials grant type the user has no role to play. 
			This is typically used by clients to access resources about themselves rather than to access a user's resources. 
		1. client app send request (client id, client secret with grant type client credentials) to authorization server
		2. authorization server give back auth-token
		3. client app send request to resource server with this auth-token
		4. resource server verify received token through communicate with authorization server
		5. if auth-token is valid, resource server return requested resource
			
		for example: reservaton hotel, as client app communicate with several third party apis to show search result
		
		
	The Password Credentials Grant.
		
		1. In case of Password grant type the user triggers the client to get some resource. 
		2. While doing so it passes the username and password to the client. 
		3. The client then communicates with the authorization server using the provided username, 
			password and also its own clientId and clientSecret to get the access token. 
		4. Using this access token it then gets the required resource from the resource server. 
		
		The real life example of Password grant will be you doing a login to you facebook account using its mobile application. 
		Here the user will have to specify the facebook credentials to the app. 
		Also the app will be having its own client id and client secret.