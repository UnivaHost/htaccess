## Stop directory browsing
> Options All -Indexes

## SSL Https active Force non-www
``
> <IfModule mod_rewrite.c> <br/>
>   RewriteEngine on <br/>
>   RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC] <br/>
>    RewriteRule ^(.*)$ https://%1/$1 [R=301,L] <br/>
>    RewriteCond %{HTTPS} !=on <br/>
>    RewriteRule ^(.*)$ https://%{HTTP_HOST}/$1 [R=301,L] <br/>
> </IfModule> <br/>
``

## SSL Https Active Force www in a Generic Way
> <IfModule mod_rewrite.c> <br/>
>    RewriteEngine on <br/>
>    RewriteCond %{HTTP_HOST} !^$ <br/>
>    RewriteCond %{HTTP_HOST} !^www\. [NC] <br/>
>    RewriteCond %{HTTPS}s ^on(s)| <br/>
>    RewriteRule ^ https://www.%{HTTP_HOST}%{REQUEST_URI} [R=301,L] <br/>
> </IfModule>

## AIOWPS_PREVENT_IMAGE_HOTLINKS_START
> <IfModule mod_rewrite.c> <br/>
>     RewriteEngine On <br/>
>     RewriteCond %{HTTP_REFERER} !^$ <br/>
>     RewriteCond %{REQUEST_FILENAME} -f <br/>
>     RewriteCond %{REQUEST_FILENAME} \.(gif|jpe?g?|png)$ [NC] <br/>
>     RewriteCond %{HTTP_REFERER} !^http(s)?://univahost\.com [NC] <br/>
>     RewriteRule \.(gif|jpe?g?|png)$ - [F,NC,L] <br/>
> </IfModule> <br/>



## Text FIle access
> <files file.txt> <br/>
>     order allow,deny <br/>
>     deny from all <br/>
> </files> <br/>


## Block double extensions from being uploaded or accessed, including htshells
> <FilesMatch ".*\.([^.]+)\.([^.]+)$"> <br/>
>     Order Deny,Allow <br/>
>     Deny from all <br/>
> </FilesMatch> <br/>

## secure uploads directory
> <FilesMatch "\.(jpg|jpeg|jpe|gif|png|tif|tiff)$"> <br/>
>     Order Deny,Allow <br/>
>     Allow from all <br/>
> </FilesMatch> <br/>


## Block shell uploaders, htshells, and other baddies
> RewriteCond %{REQUEST_URI} ((php|my|bypass)?shell|remview.*|phpremoteview.*|sshphp.*|pcom|nstview.*|c99|c100|r57|webadmin.*|phpget.*|phpwriter.*|fileditor.*|locus7.*|storm7.*)\.(p?s?x?htm?l?|txt|aspx?|cfml?|cgi|pl|php[3-9]{0,1}|jsp?|sql|xml) [NC,OR] <br/>
> RewriteCond %{REQUEST_URI} (\.exe|\.php\?act=|\.tar|_vti|afilter=|algeria\.php|chbd|chmod|cmd|command|db_query|download_file|echo|edit_file|eval|evil_root|exploit|find_text|fopen|fsbuff|fwrite|friends_links\.|ftp|gofile|grab|grep|htshell|\ -dump|logname|lynx|mail_file|md5|mkdir|mkfile|mkmode|MSOffice|muieblackcat|mysql|owssvr\.dll|passthru|popen|proc_open|processes|pwd|rmdir|root|safe0ver|search_text|selfremove|setup\.php|shell|ShellAdresi\.TXT|spicon|sql|ssh|system|telnet|trojan|typo3|uname|unzip|w00tw00t|whoami|xampp) [NC,OR] <br/>
> RewriteCond %{QUERY_STRING} (\.exe|\.tar|act=|afilter=|alter|benchmark|chbd|chmod|cmd|command|cast|char|concat|convert|create|db_query|declare|delete|download_file|drop|edit_file|encode|environ|eval|exec|exploit|find_text|fsbuff|ftp|friends_links\.|globals|gofile|grab|insert|localhost|logname|loopback|mail_file|md5|meta|mkdir|mkfile|mkmode|mosconfig|muieblackcat|mysql|order|passthru|popen|proc_open|processes|pwd|request|rmdir|root|scanner|script|search_text|select|selfremove|set|shell|sql|sp_executesql|spicon|ssh|system|telnet|trojan|truncate|uname|union|unzip|whoami) [NC] <br/>
> RewriteRule .* - [F] <br/>




## Follow symbolic links in this directory.
> Options +FollowSymLinks <br/>

## Set the default handler.
> DirectoryIndex index.php index.html index.htm <br/>

## Set the default handler.
> DirectoryIndex index.php index.html index.htm <br/>

## Override PHP settings that cannot be changed at runtime. See
## sites/default/default.settings.php and drupal_environment_initialize() in
## includes/bootstrap.inc for settings that can be changed at runtime.

## PHP 5, Apache 1 and 2.
> <IfModule mod_php5.c> <br/>
>   php_flag magic_quotes_gpc                 off <br/>
>   php_flag magic_quotes_sybase              off <br/>
>   php_flag register_globals                 off <br/>
>   php_flag session.auto_start               off <br/>
>   php_value mbstring.http_input             pass <br/>
>   php_value mbstring.http_output            pass <br/>
>   php_flag mbstring.encoding_translation    off <br/>
> </IfModule> <br/>

## Default Carset
> AddDefaultCharset utf-8 <br/>
> DirectoryIndex index.html index.htm index.php <br/>

## File Control
> <FilesMatch ".(flv|gif|jpg|jpeg|png|ico|swf|js|css|pdf)$"> <br/>
>   Header set Cache-Control "max-age=2592000" <br/>
> </FilesMatch> <br/>

## Htaccess File Security
> <Files .htaccess> <br/>
>   order allow,deny <br/>
>   deny from all <br/>
> </Files> <br/>
