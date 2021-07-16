Advanced Usage
--------------

### Custom Fields

This example shows how to add a custom phone number field to the `Member` object which is available on the member profile page. You do this by using an extension to add the database field, and then hooking into `Member::updateMemberFormFields` to add the form field. The module then picks this form field up and makes it available in the CMS.

```php
class MemberExtension extends DataExtension {

  private static $db = array(
    'PhoneNumber' => 'Text'
  );

  public function updateMemberFormFields(FieldList $fields) {
    $fields->push(new TextField('PhoneNumber', 'Phone number'));
  }

}
```


Configuration
--------------
```yml
Symbiote\MemberProfiles\Pages\MemberApprovalController:
  # Redirect the user to the 'admin/Security' member edit page instead
  # of immediately approving after visiting the approve link.
  redirect_to_admin: false
Symbiote\MemberProfiles\Email\MemberConfirmationEmail:
  extensions:
    - 'MemberConfirmationEmailExtension'
```

Modify Email URL Extension Example
--------------

This example shows how to override the base URL so that MemberProfilePage will work with the Multisites module.

```yml
Symbiote\MemberProfiles\Email\MemberConfirmationEmail:
  extensions:
    - 'MemberConfirmationEmailExtension'
```

```php

class MemberConfirmationEmailExtension extends Extension {
    public function updateBaseURL(&$absoluteBaseURL) {
        $page = $this->owner->getPage();
        if (!$page) {
            return;
        }
        $site = $page->Site();
        if (!$site || !$site->exists()) {
            return;
        }
        $absoluteBaseURL = $site->AbsoluteLink();
    }
}
```
