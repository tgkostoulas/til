# We detected that your site is not verifying reCAPTCHA solutions. (Solution)

**Google reCAPTCHA console**:  
We detected that your site is not verifying reCAPTCHA solutions. This is required for the proper use of reCAPTCHA on your site. Please see <a target="_blank" href="https://developers.google.com/recaptcha/docs/verify#api-request">our developer site</a> for more information.

`PHP Warning:  file_get_contents(): https:// wrapper is disabled in the server configuration by allow_url_fopen=0`  
`PHP Warning:  file_get_contents(https://www.google.com/recaptcha/api/siteverify?secret=... : failed to open stream: no suitable wrapper could be found in...`  

**SOLUTION**  

You should **enable** `allow_url_fopen` in the **php.ini** file:  

`allow_url_fopen = 'On'`

**Notice**:  
`allow_url_fopen` can be used to retrieve data from remote servers or websites. However, if incorrectly used, this function can compromise the security of your site ( http://phpsec.org/projects/phpsecinfo/tests/allow_url_fopen.html ).
