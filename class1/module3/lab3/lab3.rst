Apply the Service Policies
==========================

11. Apply the **service policies** to the **HTTP load balancer**.

a. Navigate to **Web App & API Protection > Load Balancers > HTTP Load Balancer**. Open the actions menu for **arcadia-re-lb**, click **Manage Configuration > Edit Configuration**, and configure the following value:


   .. table::
      :widths: auto

      ==================================    ========================================================================================
      Object                                Value
      ==================================    ========================================================================================
      **Service Policies**                  Apply Specified Service Policies
      ==================================    ========================================================================================

b. Under **Policies**, click **Configure > Add Item**. Add the policies in the following order, click **Apply**, and then click **Save and Exit**:

   .. table::
      :widths: auto

      ==================================    ========================================================================================
      Object                                Value
      ==================================    ========================================================================================
      **First policy**                      $$namespace$$/arcadia-parameter-inspection

      **Second policy**                     $$namespace$$/arcadia-login-deny

      **Third policy**                      $$namespace$$/default-allow
      ==================================    ========================================================================================


   .. raw:: html   

      <script>c1m3l1c();</script>
