Yii-pug
========
Yii's extension for Pug template system

## Instructions

### Installation

Install yii-pug with composer. Because it is not in the standard composer
repositories, you will need to add the repository to your composer.json file as
well:

    ```
    "repositories": [
        {
            "url": "https://github.com/greenhost/yii-pug",
            "type": "vcs"
        }
    ]    
    "require": {
        "greenhost/yii-pug": "dev-dev@dev",
    },

    ```

### Configuration


To enable yii-pug, add this to your 'config/main.php' file:
    
    ```php
    'components'=>array(
        ...
        'viewRenderer'=>array(
            'class' => 'ext.yii-pug.CPugViewRenderer',
        ),
        ...
    ```

You may want to add the following line, so the compiled templates will have passed data to a template in the main var list


   ```php
            'prepend' => array('<?php extract((array)$data); ?>'),
   ```

It is possible to configure other variables: check the class variables in
`CPugViewRenderer.php`. Each public variable can be configured in your main.php
yii configuration file, e.g.:

    ```php
    'components'=>array(
        ...
        'viewRenderer'=>array(
            'class' => 'ext.yii-pug.CPugViewRenderer',
            'filePermission' => '775',
        ),
        ...
    ```

sets the file permissions of all the files yii-pug creates to 775. Note that
this is applied to the compiled templates with `chmod`, so this overrides the
umask you set in PHP. Also note that this does *not* override any permissions of
directories that are automatically created.
