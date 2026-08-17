Test IP Intelligence
####################

Use an external open proxy to send a request from an IP address categorized as an anonymous proxy and verify that IP Intelligence blocks the request.

.. danger::
   Open proxies are untrusted. Use the proxy only for this lab request. Do not send credentials, cookies, tokens, or sensitive information through it.

1. In the UDF environment, locate the **Client (1)** component. Click **Access**, and then click **FIREFOX (2)** to open Firefox.

   .. image:: ../pictures/udf-client-ff.png
      :align: center

2. In Firefox, navigate to https://hide.me/en/proxy. The URL is also available in the bookmarks.

3. Enter ``http://$$namespace$$.spec-core.f5se.com`` in the proxy URL field and click **Go**.

4. The request will be blocked with a **403 Forbidden** response.

