# OIDC Demo Portal

## Overview
This repository contains the reference implementation of a relying party's website that wants to use [MOSIP's IDP (Identity Provider) services](https://github.com/mosip/idp) to log in users into its portal.

This portal uses [OpenID specs](https://openid.net/specs/openid-connect-core-1_0.html) to communicate with [MOSIP IDP Services](https://github.com/mosip/idp).

This portal contains 2 pages.

1. **Home Page**: This page represents the login screen for the relying party's website. This page includes a button with the text, "Sign in with MOSIP". On the click this button, the user gets redirected to the MOSIP's IDP Portal. The user now has to authenticate and provide consent to share information from MOSIP to relying party, on the IDP portal.

2. **User Profile Page**: This page shows the user profile on the relying party's website. On successful authentication and consent approval, the user gets navigated to this page with an Auth Code. This Auth Code would be shared with the relying party's backend service via the `/fetchUserInfo` endpoint. The backend then uses the Auth Code to fetch the access token and user details from MOSIP IDP services.
