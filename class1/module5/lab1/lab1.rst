Configure Malicious User Detection
#######################################

Enable Malicious User Detection on the HTTP Load Balancer
=========================================================

1. Navigate to **Web App & API Protection > Load Balancers (1) > HTTP Load Balancers (2)**. In the row for the created load balancer, click the **Actions** menu (3).

   .. image:: ../pictures/lb-list.png
      :align: center

2. In the **Actions** menu, click **Manage Configuration (1)**.

   .. image:: ../pictures/lb-list-manage.png
      :align: center

3. On the load balancer configuration page, click **Edit Configuration (1)**.

   .. image:: ../pictures/lb-list-edit.png
      :align: center

4. Select **Common Security Controls (1)** and configure the highlighted fields as follows:

   .. table::
      :widths: auto

      ==================================  ==========================
      Object                              Value
      ==================================  ==========================
      **Malicious User Detection (2)**    Enable
      **User Identifier (3)**             User Identification Policy
      ==================================  ==========================

   Open the **User Identification Policy (4)** selector to choose a policy.

   .. image:: ../pictures/lb-malicious-users-details-1.png
      :align: center

5. Open **User Identification Policy** and click **Add Item (1)** to create one.

   .. image:: ../pictures/lb-malicious-users-details-2.png
      :align: center

6. Configure the new user identification policy with the following value, and then click **Configure (2)** under **User Identification Rules**.

   .. table::
      :widths: auto

      ==================  ======================================
      Object              Value
      ==================  ======================================
      **Name (1)**        arcadia-crypto-user-identification
      ==================  ======================================

   .. image:: ../pictures/lb-malicious-users-details-3.png
      :align: center

7. The **User Identification Rules** list is initially empty. Click **Add Item (1)**.

   .. image:: ../pictures/lb-malicious-users-details-4.png
      :align: center

8. Configure the user identification rule with the following value, and then click **Apply (2)**.

   .. table::
      :widths: auto

      =========================  =================
      Object                     Value
      =========================  =================
      **Identifier Type (1)**    Client IP Address
      =========================  =================

   .. image:: ../pictures/lb-malicious-users-details-5.png
      :align: center

9. Verify that the rules list contains one rule with **Identifier Type** set to **IP Address**, and then click **Apply (1)**.

   .. image:: ../pictures/lb-malicious-users-details-6.png
      :align: center

10. Verify that **User Identification Rules** is shown as **Configured**, and then click **Add User Identification (1)** to create the policy.

    .. image:: ../pictures/lb-malicious-users-details-7.png
       :align: center

11. Back under **Common Security Controls** and click **Save HTTP Load Balancer (1)**.

    .. image:: ../pictures/lb-malicious-users-details-8.png
       :align: center