Examples of action or filter hooks

## user_meta_field_config (filter)

This filter hook can be use to modify fields data.

**Since:** 1.1.3  
**Parameter:** `(array) $formData, (int) $fieldID, (string) $formName`

**Supported array key for $formData:**

__field_title__ – Field Title.  
__field_type__ – Type of html input (e.g. checkbox, text, hidden, select).  
__field_name__ – Name of the field.  
__field_value__ – Retrieved value of the field.  
__default_value__ – Assign a default value when field_value is empty.  
__title_position__ – Supported value: top, left, right, inline, hidden (default: top).  
__description__ – Description of the field.  
__meta_key__ – Should use only for extra fields.  
__options__ – (string | array) Populate options for dropdown, checkbox and radio field.  
__max_char__ – Allowed maximim character.  
__field_size__ – Field size in pixel (e.g. 200px).  
__before__ – Content before field.  
__after__ – Content after field.  
__required__ – Indicate field as required.  
__unique__ – Indicate field as unique.  
__admin_only__ – If set, the field is accessible only for admin.  
__non_admin_only__ – Only viewable for non-admin  
__read_only__ – If set, read only for all user.  
__read_only_non_admin__ – If set, the field will be read only for non-admin user.  
__css_class__ – Css class for field container.  
__css_style__ – Inline css style for field container.  
__input_id__ – Input id for field itself.  
__field_class__ – Assign class to field itself.  
__field_style__ – Assign inline css stye for field itself.  
__label_id__ – Label ID.  
__label_class__ – Assign class to field label.  
__description_id__ – ID attribute for description paragraph.  
__description_class__ – Assign class to field description.  
__description_style__ – Assign inline css style for field description.  

**Examples:**

Assign css class to field:

```
add_filter( 'user_meta_field_config', 'user_meta_field_config_function', 10, 3 );
function user_meta_field_config_function( $field, $fieldID, $formName ){    
    if( $fieldID != 'Enter field id that you need to control' )
        return $field;

    $field['field_class'] = 'class1 class2';

    return $field;
}
```

Use comma in option:

```
add_filter( 'user_meta_field_config', 'user_meta_field_config_function', 10, 3 );
function user_meta_field_config_function( $field, $fieldID, $formName ){        
    if( $fieldID != 'Your field id here' )
        return $field;

    $field['options'] = "yes=Yes, Agree, no=No, Disagree";

    return $field;
}
```

_Note_: Use ascii code of comma where you want to appear it. [asciitable](http://www.asciitable.com/)

## User Registration

### user_meta_pre_user_register (filter)

**Since:** 1.1.2  

More validation before user registration:

```
add_filter( 'user_meta_pre_user_register', 'user_meta_pre_user_register_function' );
function user_meta_pre_user_register_function( $userData ){
    // Write your code for more validation before user register.
    // return WP_Error object if there are any error or validation failed.

    return $userData;
}
```

Add more extra data to usermeta table:

```
add_filter( 'user_meta_pre_user_register', 'user_meta_pre_user_register_function' );
function user_meta_pre_user_register_function( $userData ){
    // You can add some conditionl metadata
    $userData[ 'new_meta_key' ] = 'New Meta Value';

    return $userData;
}
```

### user_meta_after_user_register (action)

**Since:** 1.1.2

Example:

```
add_action( 'user_meta_after_user_register', 'user_meta_after_user_register_function' );
function user_meta_after_user_register_function( $response ){
    $userID = $response->ID;
    // Your code goes here
}
```

## User Export

### user_meta_user_export_filename (filter)

**Since:** 1.2

Changing file name:

```
add_filter( 'user_meta_user_export_filename', function( $fileName ) {
    return 'test.csv';
});
```

### user_meta_user_export_csv_delimiter (filter)

**Since:** 1.2

Changing csv delimiter to `|`:

```
add_filter( 'user_meta_user_export_csv_delimiter', function() {
    return '|';
});
```

### user_meta_user_export_csv_enclosure (filter)

**Since:** 1.2

Changing csv delimiter to `!`:

```
add_filter( 'user_meta_user_export_csv_enclosure', function() {
    return '!';
});
```

### user_meta_user_export_label (filter)

**Since:** 1.2

Changing label of field name:

```
add_filter( 'user_meta_user_export_label', function ($fields) {
    $fields['user_login'] = 'Renamed Username';

    return $fields;
});
```

### user_meta_user_export_fields (filter)

**Since:** 1.2

Changing field value:

```
add_filter( 'user_meta_user_export_fields', function ( $userData, $user ) {
    $userData['user_login'] = 'Renamed' . $user->ID;

    return $userData;
}, 10, 2);
```
