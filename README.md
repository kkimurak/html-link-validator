# html link validator

This simple script provides function to validate internal link in html that generated by asciidoc(tor).  

## usage

1. Download this script
1. Import
1. Just use.  
    Here's a example usage.

    ```sh
    $ git clone https://github.com/kkimurak/html-link-validator.git

    $ cd html-link-validator

    $ tree
    .
    ├── html-link-validator.sh
    ├── README.md
    └── test
        └── sample.html

    1 directory, 3 files

    $ html-link-validator.sh test/sample.html

    $ echo $?
    4
    ```

    Note that offset is added to returning value if at least one invalid link found, to avoid conflict with other error message (e.g. 2 means "no such file").  
    Please refer variable `validation_return_offset`.  

    You can set VALIDATOR_DEBUG=true to see debug message  

    ```sh
    $ VALIDATOR_DEBUG=true

    $ html-link-validator.sh test/sample.html
    link invalid_link is invalid
    1 invalid link found
    ```

    If you want to import function using `source`, set `VALIDATOR_USE_AS_FUNCTION` to `true` and then do that.  
    `source` is not specified in POSIX, so I'm not sure if it works for you.  
    It works on my Fedora, but not works on Travis.

    ```sh
    $ VALIDATOR_USE_AS_FUNCTION=true

    $ source html-link-validator.sh && validate_internal_link_in_html test/sample.html

    $ echo $?
    4
    ```

## author

k.kimura ([@kkimurak](https://github.com/kkimurak))
