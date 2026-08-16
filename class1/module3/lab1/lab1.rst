Service Policies for Parameter Validation
#########################################

A service policy is an ordered set of rules that matches HTTP request attributes, such as method, path, client, or parameter, and applies an action, such as allow or deny. F5 Distributed Cloud Services evaluates service policies in the order in which they are applied.

This configuration applies positive security to **POST /v1/login**:

1. Allow requests with an **email** parameter that matches the configured pattern.
2. Deny all other **POST /v1/login** requests.
3. Allow traffic to all other URLs.

Default Allow Service Policy
============================

1. Create the catch-all policy that will allow traffic not matched by either login policy. In the F5 Distributed Cloud Console, navigate to **Web App & API Protection > Service Policies (1) > Service Policies (2)**, and then click **Add Service Policy (3)**. 
   .. image:: ../pictures/sp-add.png      
      :align: center



2. In the appeared page fill the following values and click **Add Service Policy (3)**:
   .. table::
      :widths: auto

      ==============================    ========================================================================================
      Object                            Value
      ==============================    ========================================================================================
      **Name (1) **                     default-allow      
      **Select Policy Rules (2)**       Allow All Requests
      ==============================    ========================================================================================


   .. image:: ../pictures/sp-default-allow-all.png
      :align: center

Allow Policy for Valid Login Requests
=====================================

1. Click **Add Service Policy** to create a new service policy that allows POST requests to **/v1/login** only when the **email** parameter matches the specified email address pattern. Configure the following values:

2. For the *Name* enter **arcadia-parameter-inspection**. 
   .. image:: ../pictures/sp-parameter-details-1.png
      :align: center

   .. image:: ../pictures/sp-parameter-details-2.png
      :align: center

   .. image:: ../pictures/sp-parameter-details-3.png
      :align: center

   .. image:: ../pictures/sp-parameter-details-4.png
      :align: center

   .. image:: ../pictures/sp-parameter-details-5.png
      :align: center

   .. image:: ../pictures/sp-parameter-details-6.png
      :align: center

   .. image:: ../pictures/sp-parameter-details-7.png
      :align: center

   .. image:: ../pictures/sp-parameter-details-8.png
      :align: center

   .. image:: ../pictures/sp-parameter-details-9.png
      :align: center

   .. image:: ../pictures/sp-parameter-details-10.png
      :align: center

   .. image:: ../pictures/sp-res.png
      :align: center

   .. table::
      :widths: auto

      ==============================    ========================================================================================
      Object                            Value
      ==============================    ========================================================================================
      **Name**                          arcadia-parameter-inspection

      **Action**                        Allow
      ==============================    ========================================================================================
2. Create a specific **allow service policy** for login requests with an email parameter that matches the approved format. Navigate to **Web App & API Protection > Service Policies > Service Policies**, click **Add Service Policy**, and configure the following values:

   .. table::
      :widths: auto

      ==============================    ========================================================================================
      Object                            Value
      ==============================    ========================================================================================
      **Name**                          arcadia-parameter-inspection

      **Action**                        Allow
      ==============================    ========================================================================================

3. Under **Rules**, click **Configure > Add Item**, and configure the following values:

   .. table::
      :widths: auto

      ==============================    ========================================================================================
      Object                            Value
      ==============================    ========================================================================================
      **Name**                          email
      
      **HTTP Method**                   POST
      ==============================    ========================================================================================

4. Under **HTTP Path**, click **Configure**. Under **Exact Values**, click **Add Item**, enter the following value, and click **Apply**:

   .. table::
      :widths: auto

      ================================    ========================================================================================
      Object                              Value
      ================================    ========================================================================================
      **Input box that just appeared**    /v1/login   
      ================================    ========================================================================================

5. Under **Request Match**, enable **Show Advanced Fields**. Under **Argument Matchers**, click **Add Item** and configure the following value:

   .. table::
      :widths: auto

      ===============================    ========================================================================================
      Object                             Value
      ===============================    ========================================================================================
      **Argument Name**                  email
      ===============================    ========================================================================================

6. Under **Regex Values**, click **Add Item** and configure the following values. Click **Apply** on each open configuration form, and then click **Save and Exit**:

   .. table::
      :widths: auto

      ================================    ========================================================================================
      Object                              Value
      ================================    ========================================================================================
      **Input box that just appeared**    .. code::

                                             [A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}  

      **Invert Matcher**                  Unchecked
      ================================    ========================================================================================

   .. raw:: html   

    <script>c1m3l1b();</script>  

Deny Policy for Other Login Requests
====================================

7. Create a service policy that denies POST requests to **/v1/login** that were not allowed by the valid-login policy. Navigate to **Web App & API Protection > Service Policies > Service Policies**, click **Add Service Policy**, and configure the following values:

   .. table::
      :widths: auto

      ==============================    ========================================================================================
      Object                            Value
      ==============================    ========================================================================================
      **Name**                          arcadia-login-deny

      **Action**                        Deny
      ==============================    ========================================================================================

8. Under **Rules**, click **Configure > Add Item**, and configure the following values:

   .. table::
      :widths: auto

      ==============================    ========================================================================================
      Object                            Value
      ==============================    ========================================================================================
      **Name**                          deny-other-login-requests

      **HTTP Method**                   POST
      ==============================    ========================================================================================

9. Under **HTTP Path**, click **Configure**. Under **Exact Values**, click **Add Item**, enter **/v1/login**, and click **Apply**. Do not configure an argument matcher for this rule. Click **Apply** on each open configuration form, and then click **Save and Exit**.