Configure the Web Application Firewall
######################################

Create the Web Application Firewall
=======================================
 
Click **Web App & API Protection -> App Firewall (1)-> Add App Firewall (2)**
   .. image:: ../pictures/app-firewall.png
      :align: center

Fill the bellow data and click **Add App Firewall (3)**
   .. table:: Waf Policy
      :widths: auto

      ==============================    ========================================================================================
      Object                            Value
      ==============================    ========================================================================================
      **Name (1)**                          arcadia-crypto-waf
      
      **Enforcement Mode (2)**              blocking
      ==============================    ========================================================================================


   .. image:: ../pictures/app-firewall-details-1.png
      :align: center

Attach the Web Application Firewall to the HTTP Load Balancer
============================================================================

a) Click **Web App & API Protection -> Load Balancers (1) -> HTTP Load Balancer (1) -> Click the ... (3) in the created load balancer row**

   .. image:: ../pictures/lb-list.png

b) Click **Manage Configuration (1)** in the appeared menu

   .. image:: ../pictures/lb-list-manage.png
      :align: center

c) In the appeared page click **Edit Configuration (1)**

   .. image:: ../pictures/lb-list-edit.png
      :align: center

d) In the appeared page scroll to the **Web Application Firewall (1)** section, select **Enable (2)** for **Web Application Firewall (WAF)** and select the created WAF ``$$namespace$$/arcadia-crypto-waf`` **(3)**. Click **Save Http Load Balancer (4)** to apply the changes.

   .. image:: ../pictures/lb-waf-assign.png
      :align: center
   