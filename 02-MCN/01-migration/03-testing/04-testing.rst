Test routing and review traffic visibility
##########################################

In order to make sure all is going to the correct endpoint we will need to relogin into the application and look at the relevant dashboards.

1. Open :ext_link:`http://$$namespace$$.spec-core.f5se.com` in a browser. You should see the Arcadia Crypto application login page.
2. Try to login with the following credentials:

.. table::
   :widths: auto

   ==========================================    ========================================================================================
   Object                                        Value
   ==========================================    ========================================================================================
   **Username**                                  satoshi@bitcoin.com
   **Password**                                  bitcoin
   ==========================================    ========================================================================================

3. The login will hang as there is no backend service to handle the request. This is expected as the backend services are still running in the on-premises environment and are not reachable from the AWS.