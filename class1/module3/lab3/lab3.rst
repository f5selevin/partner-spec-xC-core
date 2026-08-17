Apply the Service Policies
##########################

In order to protect the Arcadia application, apply the created service policies to the **arcadia-crypto-lb** HTTP load balancer.


1. Navigate to **Web App & API Protection > Load Balancers (1) > HTTP Load Balancer (2)**. Click the **... (3)** button for **arcadia-crypto-lb**.

   .. image:: ../pictures/lb-list.png
      :align: center


2. Click **Manage Configuration (1)**.

   .. image:: ../pictures/lb-manage-config.png
      :align: center

3. Click **Edit Configuration (1)**.

   .. image:: ../pictures/lb-edit-config.png
      :align: center

4. Navigate to the **Common Security Controls (1)** section.

   .. image:: ../pictures/lb-common-security-controls.png
      :align: center

5. Select **Apply Specified Service Policies (1)** for **Service Policies**, and click the **Configure (2)** link.

   .. image:: ../pictures/lb-enable-service-policy.png
      :align: center


6. Click **Add Item (1)**, select ``$$namespace$$/arcadia-parameter-inspection`` for **(2)** and ``$$namespace$$/default-allow`` for **(3)**. Click **Apply (4)**.

   .. image:: ../pictures/lb-enable-service-policy-2.png
      :align: center

.. warning::
   Make sure that the order of policies is correct, the **arcadia-parameter-inspection** policy should be first and the **default-allow** policy should be second.


7. Click **Save HTTP Load Balancer (1)**.

   .. image:: ../pictures/lb-enable-service-policy-save.png
      :align: center