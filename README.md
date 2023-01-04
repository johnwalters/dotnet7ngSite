# dotnet7ngSite
A dotnet core framework 7 website with angular and authentication and the fix for the 401 auth problem
401 auth problem: Somewhere along the line, when you create a .NET Core 6.0 website with Angular and authentication, in Visual Studio 2022, it wouldn't work out of the box. When testing in a localhost environment, registering a user, clicking the migration button, then clicking the Fetch Data option, you'd get a '401 unauthorized' error, so no data coming back from the WeatherForcast server side API. This repo contains just the Program.cs file with the change needed to fix that bug.

To replicate:
1. In Viusal Studio 2022, Create a New Project, Search for templates with Angular, choose ASP.NET Dot Net Core with Angular, next, name it, next, choose Framework .NET 6.0 or .NET 7.0, Authentication Type = Individual Accounts, and select 'Do not use top-level statements', click Create.

2. Run it (it'll take awhile first time), register a new user, click the Apply Migrations button, refresh, log in, click Fetch Data. Nothing comes back, because you got a 401 authentication error on the API call to the server.

To fix the bug:
1. Replace Program.cs in the created project with the one in this repo. Change the port number to the one that is in the created project's .cproj file, <PropertyGroup>|<SpaProxyServerUrl>https://localhost:PORTNUMBER</SpaProxyServerUrl>

2. That should do it.
  
Thanks to Ogglas https://stackoverflow.com/users/3850405/ogglas for this
  
https://stackoverflow.com/questions/60306175/bearer-error-invalid-token-error-description-the-issuer-is-invalid/66664653
https://github.com/dotnet/core/blob/main/release-notes/6.0/known-issues.md#spa-template-issues-with-individual-authentication-when-running-in-development


