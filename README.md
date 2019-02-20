# Process Frontend Admin Page

A demonstration of how a Process module could execute on the frontend. This is just a proof-of-concept.

![frontend](https://user-images.githubusercontent.com/1538852/53064024-2b6de900-352b-11e9-882b-05659b0e0dd4.gif)

## Usage

Install the ProcessFrontendAdminPage module.

Create a new role named "frontend-only". Give this role the "process-frontend-admin-page" permission and no other permissions.

Create a new user named "frontend-only" and give them the "frontend-only" role.

## How the module works

On install the module creates a "Demo frontend admin page" under Home. This page uses the admin template with the ProcessFrontendAdminPage process assigned.

When this page is viewed by a guest they are silently logged as the "frontend-only" user. This allows them to see the rendered output of the Process module.

The header and footer of the admin theme are not rendered when the page is viewed. 

When a user logged into the "frontend-only" account accesses any other page they are logged out. This is for the sake of logged-out users of other roles, so that when they go to log into the PW admin they don't find themselves already logged in as the "frontend-only" user.

## Taking the concept further

You could embed the ProcessFrontendAdminPage output in an iframe on another page, to preserve a global header/footer and avoid conflicts with the admin CSS.

You could add extra markup, Javascript and CSS to the ProcessFrontendAdminPage output to make it look more like the rest of your site.

You could create additional `executeSomething()` methods to render different output depending on URL segment.

You could create additional pages within your site that use the admin template and assign the ProcessFrontendAdminPage process. I think you would have to use API code to do this. Then in the `execute()` method you could check the name of the page being viewed and render different output accordingly.