Configure IP Intelligence
#############################


1. Navigate to **Web App & API Protection > Load Balancers (1) > HTTP Load Balancer (2)**. Click the **... (3)** button for **arcadia-crypto-lb**.

   .. image:: ../pictures/lb-list.png
      :align: center


2. Click **Manage Configuration (1)**.

   .. image:: ../pictures/lb-manage-config.png
      :align: center

3. Click **Edit Configuration (1)**.

   .. image:: ../pictures/lb-edit-config.png
      :align: center

4. Navigate to **Common Security Controls (1)**, enable **IP Reputation (2)**, and select **Spam Sources** and **Anonymous Proxies (3)** from the list of IP threat categories. Click **Save HTTP Load Balancer (4)**.

   .. image:: ../pictures/lb-ip-reputation.png
      :align: center

   .. table::
      :widths: auto

      ==========================================    ========================================================================================
      Object                                        Value
      ==========================================    ========================================================================================
      **IP Reputation**                             Enable
   
      **List of IP Threat Categories to choose**    Spam Sources, Anonymous Proxies
      ==========================================    ========================================================================================