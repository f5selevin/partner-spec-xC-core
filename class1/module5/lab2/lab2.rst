Test Malicious User Detection
#############################

Generate Malicious Traffic
==========================

In order to test we will behave as a bad actor.

.. danger::
   Generate this malicious traffic only against the website assigned to you for this lab. Verify the target URL before running the script, and do not use it to attack or test any other website.

1. Browse to the app :ext_link:`http://$$namespace$$.spec-core.f5se.com/` and login

   .. table::
      :widths: auto

      ==========================================    ========================================================================================
      Object                                        Value
      ==========================================    ========================================================================================
      **Username**                                  satoshi@bitcoin.com   
      **Password**                                  bitcoin
      ==========================================    ========================================================================================


2. Now we have access to authenticated APIs that we can try to break. Copy and paste the JavaScript code below into your browser console.
   The code attacks internal APIs that can only be accessed after authentication. It logs the HTTP status of each request and continues until you reload the page.

   .. code::
        // A helper function to delay execution
        function sleep(ms) {
            return new Promise(resolve => setTimeout(resolve, ms));
        }

        async function runRequests() {
            const requests = [                
                {url: '/v1/stockt', method: 'POST', data: '{"symbol":"<script","transactionType":"buy","amount":1}' },
                {url: '/v1/stockt', method: 'POST', data: '{"symbol":"ltc","transactionType":"SELECT ItemName FROM Items WHERE ItemNumber = 999; DROP TABLE USERS ","amount":1}' },
                {url: '/v1/stockt', method: 'POST', data: '{"symbol":"/etc/passwd","transactionType":"buy","amount":1}' },
                {url: '/v1/fuzzingattack', method: 'GET'},
            ];

            while(true) { // infinite loop to start over when all requests have been processed
                for(let i = 0; i < requests.length; i++) { // process each request
                    let item = requests[i];
                    let headers = { 'Authorization': `Bearer ${JSON.parse(sessionStorage.getItem('authUser')).jwt}` };

                    let requestOptions = {
                        method: item.method,
                        headers: headers,
                    };

                    if(item.method === 'POST') {
                        headers['Content-Type'] = 'application/json';
                        requestOptions.body = item.data;
                    }

                    try {
                        const response = await fetch(location.origin + item.url, requestOptions);
                        console.log(`${item.method} ${item.url}: HTTP ${response.status}`);
                    } catch (error) {
                        console.error(`${item.method} ${item.url} failed:`, error);
                    }

                    await sleep(1000); // Wait for 1 second before the next request
                }
            }
        }

        console.log('Starting requests. Reload the page to stop.');
        void runRequests();

3. Monitor the browser console until the malicious ``POST`` requests to ``/v1/stockt`` return **HTTP 403 Forbidden**. This confirms that the requests are being blocked.

   .. image:: ../pictures/block-403.png
      :align: center

Review the Detected Malicious Activity
======================================

1. In the F5 Distributed Cloud Console, navigate to **Web App & API Protection > Overview > Security**. On the **Dashboard** tab, verify that security events are displayed and that ``/v1/stockt`` and ``/v1/fuzzingattack`` appear under **Top Attacked Paths**.

   .. image:: ../pictures/security-dashboard.png
      :align: center

2. Click the **Malicious Users (2)** tab and review the **Attacked Delivery Resources** map for the detected malicious-user activity.

   .. image:: ../pictures/security-malicious-users-dashboard.png
      :align: center
