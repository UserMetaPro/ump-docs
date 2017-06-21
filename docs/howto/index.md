# How To.. ?

## Use field title as placeholder

To use, field title as a placeholder, put following code to your `functions.php`

```
add_filter( 'user_meta_field_config', 'titleAsPlaceholder', 10, 3 );
function titleAsPlaceholder( $field, $fieldID, $formName ) {
    if ( !empty( $field['field_title'] ) )
        $field['placeholder'] = $field['field_title'];

    return $field;
}
```

## Build custom login form

Any form can be used as login form. Create a new form for login, add Username and Password field to the form, for “Remember me” add a checkbox with

Meta Key: `remember`  
Field Options: `1=Remember me`

## Category as options for dropdown/select/multiselect

```
add_filter( 'user_meta_field_config', 'user_meta_field_config_populate_categories', 10, 3 );
function user_meta_field_config_populate_categories( $field, $fieldID, $formName ){

    if( $fieldID != 'Your_Field_ID' ) // Put your desired field id here
        return $field;

    $output = null;
    $cats = get_categories();
    foreach( $cats as $cat ):
        $output .= $cat->term_id.'='.$cat->name.',';
    endforeach;
    $output = ',' . trim( $output, ',' );

    $field['options'] = $output;

    return $field;
}
```


## Add red asterisk(`*`) to all required fields

```
add_filter( 'user_meta_field_config', 'user_meta_field_config_add_asterisk', 10, 3 );
function user_meta_field_config_add_asterisk( $field, $fieldID, $formName ){     
    if( !empty($field['required']) || in_array($field['field_type'], array('user_login', 'user_email')) ){
        if( !empty( $field['field_title'] ) )
            $field['field_title'] .= '<span class="um_required">*</span>';
    }

    return $field;
}
```

## Add custom required class to all required fields

```
add_filter( 'user_meta_field_config', 'user_meta_field_config_add_class', 10, 3 );
function user_meta_field_config_add_class( $field, $fieldID, $formName ){     
    if( !empty($field['required']) || in_array($field['field_type'], array('user_login', 'user_email')) ){
        $field['field_class'] = 'your_required_class '; // leave an empty space after classname
    }

    return $field;
}
```

## Change resetpass page

To change default “resetpass” to “verify” put following codes to your `functions.php`

```
add_filter('user_meta_front_execution_page', create_function('','return "verify";'));
```

## Customize label for login form

To customize default label for login form, edit and put following code to your `functions.php` file:

```
add_filter( 'user_meta_default_login_form', 'user_meta_default_login_form_function' );
function user_meta_default_login_form_function( $config ){
    $config['login_label']  = "Your desire text for login input";
    $config['pass_label']   = "Your desire text for password input";
    $config['remember_label'] = "Your desire text for rember me checkbox";
    $config['button_value'] = "Your desire text for login button";

    return $config;
}
```

## Redirection after profile update

Put following code to `functions.php` for redirecting user after profile update.

```
add_action( 'user_meta_after_user_update', 'user_meta_after_user_update_function' );
function user_meta_after_user_update_function( $response ){
    global $userMeta;
    echo $userMeta->jsRedirect( 'http://example.com' );
}
```

## Extend date range

To extend date range from default one use following hooks:

```
add_filter( 'user_meta_field_config', 'user_meta_field_config_function', 10, 3 );
function user_meta_field_config_function( $field, $fieldID, $formName ){
    if( $fieldID != 0 ) // Replace 0 with your filed id
        return $field;
    $field['field_options'] = array( "yearRange"=>"1900:c" );
    return $field;
}
```

Please note, you need to change field id in this example, or you can use any other algorithm to filter your field.
You can pass more options to control the datepicker through `$field[‘field_options’]` as an array.

## Use non-ajax file upload field

If for any case, ajax file upload solution is not working for you, you can switch to non-ajax solution.
To choose non-ajax file upload, follow those steps:

1. Go to `User Meta >> Shared Fields`, expand your file upload field (or avatar field) and check `Disable AJAX upload` checkbox, save your change.

2. Go to `User Meta >> Forms`, expand your form and check `Do not use AJAX submit` checkbox and save your change.

## Export file url with user export

By default, UMP export relative path of file for exporting users into a csv file. To export file url, put following codes to `functions.php`.

```
add_filter('user_meta_user_export_fields', function ($userData, $user) {
    global $userMeta;

    if (!empty($userData['user_avatar'])) {
        $file = $userMeta->determinFileDir($userData['user_avatar']);

        if ($file) {
            $userData['user_avatar'] = $file['url'];
            // For full path, use:
            // $userData['user_avatar'] = $file['path'];
        }
    }

    return $userData;
}, 10, 2);
```

**Note:** Required version 1.2 or above.
