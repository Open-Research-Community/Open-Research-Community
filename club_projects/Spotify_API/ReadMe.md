# Prerequisites
This tutorial assumes you have a Spotify account (free or premium).
We will use cURL to make API calls. You can install it from here our using the package manager of your choice.

# Set Up Your Account
1. Login to the Spotify Developer Dashboard. If necessary, read the latest Developer Terms of Service to complete your account set up.
2. Create an app
  - An app provides the Client ID and Client Secret needed to request an access token by implementing any of the authorization flows.
  - To create an app, go to your Dashboard, click on the Create an app button and enter the following information:
    - App Name: My App
    - App Description: This is my first Spotify app
    - Redirect URI: You won't need this parameter in this example, so let's use http://localhost:3000.
    - Finally, check the Developer Terms of Service checkbox and tap on the Create button.
    - Request an access token
    
The access token is a string which contains the credentials and permissions that can be used to access a given resource (e.g artists, albums or tracks) or user's data (e.g your profile or your playlists).

In order to request the access token you need to get your Client_ID and Client Secret:
  - Go to the Dashboard
  - Click on the name of the app you have just created (My App)
  - Click on the Settings button
  The Client ID can be found here. The Client Secret can be found behind the View client secret link.
With our credentials in hand, we are ready to request an access token. This tutorial uses the Client Credentials, so we must:
Send a POST request to the token endpoint URI.
Add the Content-Type header set to the application/x-www-form-urlencoded value.
Add a HTTP body containing the Client ID and Client Secret, along with the grant_type parameter set to client_credentials.
curl -X POST "https://accounts.spotify.com/api/token" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d "grant_type=client_credentials&client_id=your-client-id&client_secret=your-client-secret"

The response will return an access token valid for 1 hour:
{
  "access_token": "BQDBKJ5eo5jxbtpWjVOj7ryS84khybFpP_lTqzV7uV-T_m0cTfwvdn5BnBSKPxKgEb11",
  "token_type": "Bearer",
  "expires_in": 3600
}

