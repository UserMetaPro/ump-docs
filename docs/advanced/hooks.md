# Action and Filter Hooks

List of all available action and filter hooks supported by UserMetaPro.

### Forms and Fields

1. **Action Hook: _user_meta_before_form_** (since 1.1.3)  
Runs when generating form. Calling just before `<form>` tag.  
**Parameter:** `(string) $formName`

1. **Action Hook: _user_meta_after_form_** (since 1.1.3)  
Runs when generating form. Calling just after `<form>` tag.  
**Parameter:** `(string) $formName`

1. **Filter Hook: _user_meta_form_config_** (since 1.1.3)  
Can be modify forms data by calling this filter hook.  
**Parameter:** `(array) $formData, (string) $formName`

1. **Filter Hook: _user_meta_field_config_** (since 1.1.3)  
Can be modify fields data by calling this filter hook.  
 **Parameter:** `(array) $formData, (int) $fieldID, (string) $formName`

1. **Filter Hook: _user_meta_field_display_** (since 1.1.3)  
Applied to field html before browser output.  
 **Parameter:** `(string) $html, (int) $fieldID, (string) $formName, (array) $formData`

1. **Filter Hook: _user_meta_form_display_** (since 1.1.3)  
Applied to form html before browser output.  
 **Parameter:** `(string) $html, (string) $formName, (array) $formData`

### User Registration

1. Fliter Hook: _user_meta_pre_user_register_** (since 1.1.2)  
This filter can be used to modify user data before user registration.  
 **Parameter:** `(array) $userData`

1. **Action Hook: _user_meta_after_user_register_** (since 1.1.2)  
Runs when user registration is completed.  
 **Parameter:** `(object) $response`

### User Profile Update

1. **Fliter Hook: _user_meta_pre_user_update_** (since 1.1.3)  
This filter can be used to modify user data before user profile update.  
 **Parameter:** `(array) $userData`

1. **Action Hook: _user_meta_after_user_update_** (since 1.1.3)  
Runs when user update their profile.  
 **Parameter:** `(object) $response`

### User Activation/Deactivation

1. **Action Hook: _user_meta_user_activate_** (since 1.1.2)  
Runs when user activated.  
 **Parameter:** `(int) $userID`

1. **Action Hook: _user_meta_user_deactivate_** (since 1.1.2)  
Runs when user deactivated.  
 **Parameter:** `(int) $userID`

### Email Verification

1. **Action Hook: _user_meta_email_verified_** (since 1.1.2)  
Runs when user verified their email.  
 **Parameter:** `(int) $userID`

### Redirection

1. **Filter Hook: _login_redirect_** (since 1.1.2)  
Can be used to change login redirection url.

1. **Filter Hook: _logout_redirect_** (since 1.1.2)  
Can be used to change login redirection url.

1. **Filter Hook: _registration_redirect_** (since 1.1.2)  
Can be used to change login redirection url.

### Messages

1. **Filter Hook: _user_meta_msg_** (since 1.1.3)  
Message text can be changed by this filter.  
 **Parameter:** `(string) $message, (string) $key`
