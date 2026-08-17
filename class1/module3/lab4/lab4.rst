Test the Application After Enabling the WAF Rules
##################################################

1. Let's see what have changed first let's make sure the good login is working

   .. code-block:: none
      curl \
        -H "Content-Type: application/json;charset=UTF-8" \
        --data-raw '{"email":"satoshi@bitcoin.com","password":"bitcoin"}' \
        http://$$namespace$$.spec-core.f5se.com/v1/login

2. Now let's do the same but with the invalid email parameter. This time the request will get blocked.

   .. code-block:: none
      curl \
        -H "Content-Type: application/json;charset=UTF-8" \
        --data-raw '{"email":"11223344","password":"bitcoin"}' \
        http://$$namespace$$.spec-core.f5se.com/v1/login

The response will be a 403 Forbidden error with the message like the following:

   .. code-block:: none
      <html><head><title>Error Page</title></head>
      <body>
      The requested URL was rejected. Please consult with your administrator.<br/><br/>
      Your support ID is 78928f6d-f0cb-4ffa-abc5-4191586d3a68
      <h2>Error 403 - Forbidden</h2>F5 site: wes-sea<br/><br/>
      <a href='javascript:history.back();'>[Go Back]</a>
      </body>
      </html>