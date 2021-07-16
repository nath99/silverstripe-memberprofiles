Usage Overview
--------------
A new page type is added in the CMS called a "Member Profile Page". This allows
you to create a page that allows users to register and/or manage their profile.
Registration can be enabled or disabled in the "Behaviour" tab.

### Content Blocks
The "Profile", "Registration" and "After Registration" allow you to set an
individual title and content to display for each of these contexts.

![Example registration content](/docs/images/registration-content.jpg)

### Profile Fields
In the "Main" tab you are presented with a table to manage the fields that a
user is presented with on the profile page. These are automatically kept in
sync with the Member object.

You can control if the field is shown on registration, or to already registered
users. You can also give it a custom title, and for some fields a default value
that is pre-populated on registration. You can also specify if the field is
required, or should be unique across all members. A custom error message can
also be set to display if there are any validation errors.

### Groups
You can choose a set of groups that are attached to the profile page. When a
user registers they will be added to these groups, and an existing Member must
belong to these groups in order to edit their profile on this profile page.

In addition to the fixed group membership, users are also able to select optional
groups to belong to (if desired). The list of groups they can select from is
chosen in the bottom group list. To actually let users select, the "Groups"
field must be made editable in the list of fields above.

### Validation
The "Validation" tab makes it possible to enable email validation, which means
that a user must click on a link emailed to them before they can log in.

If a user loses their confirmation email, or you wish to manually confirm an
account you can do so via the "Security" CMS section - just click on a member
and there will be a dropdown down the bottom allowing you to perform these
actions.

### Template Usage
You can link to the profile page with the optional ?BackURL= parameter
which will set a URL that the user will be redirected to after they complete
registration. This requires the "RegistrationRedirect" property to be set
on the After Registration tab.

If you like, you can manually set a redirection target by setting
`Session::set('MemberProfile.REDIRECT')` to a URL value.

See [Advanced Usage](/docs/en/advanced-usage.md) for customisation examples.
