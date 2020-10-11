# Unrestricted File Upload

## Prerequisite
Make the following settings in /var/www/html/xvwa/php.ini
```
file_uploads = on
allow_url_fopen = on
allow_url_include = on
```

Create directory uploads inside /var/www/html/xvwa/img.  It does not exist
```mkdir -p /var/www/html/xvwa/img/uploads```

Change the owner and group of /var to www-data
```chown -R www-data:www-data /var```

## Testing (PARTIAL)

Input: Upload File `info.php` as image
Output: There was an error uploading the file, please try again!

Now get the uploaded file via URL address
`http://<<ip address>>/xvwa/img/uploads/info.php`


## References:
https://github.com/rudSarkar/xvwa-solution/blob/master/unrestricted-file-upload-xvwa.md
