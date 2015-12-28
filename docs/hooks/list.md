# Action and Filter Hooks

List of available action and filter hooks supported by [UserMetaPro](http://user-meta.com).

## Forms and Fields

1. **Action Hook: _user_meta_before_form_** (since 1.1.3)  
Runs when generating form. Calling just before `<form>` tag.  
**Parameter:** `(string) $formName`
>

1. **Action Hook: _user_meta_after_form_** (since 1.1.3)  
Runs when generating form. Calling just after `<form>` tag.  
**Parameter:** `(string) $formName`
>

1. **Filter Hook: _user_meta_form_config_** (since 1.1.3)   
Can be modify forms data by calling this filter hook.  
**Parameter:** `(array) $formData, (string) $formName`
>

1. **Filter Hook:
_[user_meta_field_config](../hooks/examples.md#user_meta_field_config-filter)_** (since 1.1.3)  
Can be modify fields data by calling this filter hook.  
 **Parameter:** `(array) $formData, (int) $fieldID, (string) $formName`
 >

1. **Filter Hook: _user_meta_field_display_** (since 1.1.3)  
Applied to field html before browser output.  
 **Parameter:** `(string) $html, (int) $fieldID, (string) $formName, (array) $formData`
 >

1. **Filter Hook: _user_meta_form_display_** (since 1.1.3)  
Applied to form html before browser output.  
 **Parameter:** `(string) $html, (string) $formName, (array) $formData`

## [User Registration](../hooks/examples.md#user-registration)

1. **Fliter Hook: _user_meta_pre_user_register_** (since 1.1.2)  
This filter can be used to modify user data before user registration.  
**Parameter:** `(array) $userData`
>

1. **Action Hook: _user_meta_after_user_register_** (since 1.1.2)  
This action will run immediately after user registration.  
**Parameter:** `(object) $response`
>

## User Profile Update

1. **Fliter Hook: _user_meta_pre_user_update_** (since 1.1.3)  
This filter can be used to modify user data before user profile update.  
 **Parameter:** `(array) $userData`
 >

1. **Action Hook: _user_meta_after_user_update_** (since 1.1.3)  
Runs when user update their profile.  
 **Parameter:** `(object) $response`
 >

## User Activation/Deactivation

1. **Action Hook: _user_meta_user_activate_** (since 1.1.2)  
Runs when user activated.  
 **Parameter:** `(int) $userID`
 >

1. **Action Hook: _user_meta_user_deactivate_** (since 1.1.2)  
Runs when user deactivated.  
 **Parameter:** `(int) $userID`
 >

## Email Verification

1. **Action Hook: _user_meta_email_verified_** (since 1.1.2)  
Runs when user verified their email.  
 **Parameter:** `(int) $userID`

## Redirection

1. **Filter Hook: _login_redirect_** (since 1.1.2)  
Can be used to change login redirection url.  
 **Parameter:** `(string) $url, (string) $request_url, (WP_User | WP_Error) $user`  
>

1. **Filter Hook: _logout_redirect_** (since 1.1.2)  
Can be used to change login redirection url.  
 **Parameter:** `(string) $url, (string) $request_url, (WP_User) $user`
>

1. **Filter Hook: _registration_redirect_** (since 1.1.2)  
Can be used to change login redirection url.  
 **Parameter:** `(string) $url, (int) $userID`

 __Note__: By default, all redirection filters is disabled. To enable them use `user_meta_wp_hook` filter.

## [User Export](../hooks/examples.md#user-export)

1. **Filter Hook: _user_meta_user_export_filename_** (since 1.1.8)  
Change file name of exported csv file.  
**Parameter:** `(string) $fileName`
>

1. **Filter Hook: _user_meta_user_export_csv_delimiter_** (since 1.1.8)  
Change default delimiter `,`  
**Parameter:** `(string) $delimiter`
>

1. **Filter Hook: _user_meta_user_export_csv_enclosure_** (since 1.1.8)  
Change default enclosure `"`  
**Parameter:** `(string) $enclosure`
>

1. **Filter Hook: _user_meta_user_export_label_** (since 1.1.8)  
Change label of csv file (first row).  
**Parameter:** `(array) fields`
>

1. **Filter Hook: _user_meta_user_export_fields_** (since 1.1.8)  
Change field value of exported file.  
**Parameter:** `(array) $userData, (WP_User) $user`


## Misc

1. **Filter Hook: _user_meta_msg_** (since 1.1.3)  
Message text can be changed by this filter.  
**Parameter:** `(string) $message, (string) $key`
>

1. **Filter Hook: user_meta_wp_hook** (since 1.1.6)  
Enable or disable conflicted hooks.  
 **Parameter:** `(boolean) $enable, (string) $hookName, (array) $args`
