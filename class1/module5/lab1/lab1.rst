Configure Malicious User Detection
#######################################

Open the HTTP Load Balancer Configuration
==========================================

1. Navigate to **Web App & API Protection > Load Balancers (1) > HTTP Load Balancers (2)**. In the row for the created load balancer, click the **Actions** menu (3).

   .. image:: ../pictures/lb-list.png
      :align: center

2. In the **Actions** menu, click **Manage Configuration (1)**.

   .. image:: ../pictures/lb-list-manage.png
      :align: center

3. On the load balancer configuration page, click **Edit Configuration (1)**.

   .. image:: ../pictures/lb-list-edit.png
      :align: center

Enable Malicious User Detection and Mitigation
==============================================

4. Select **Common Security Controls (1)**. Configure the fields in the order shown in the interface:

   .. table::
      :widths: auto

      =================================================  ==========================
      Object                                             Value
      =================================================  ==========================
      **Malicious User Detection (2)**                   Enable      
      **User Identifier (3)**                            User Identification Policy
      =================================================  ==========================

   Open the **User Identification Policy (4)** selector.

   .. image:: ../pictures/lb-malicious-users-details-1.png
      :align: center

Create the User Identification Policy
=====================================

5. In opened **User Identification Policy** click **Add Item (1)** to create one.

   .. image:: ../pictures/lb-malicious-users-details-2.png
      :align: center

6. Set **Name (1)** to ``arcadia-crypto-user-identification``, and then click **Configure (2)**.

   .. table::
      :widths: auto

      ==================  ======================================
      Object              Value
      ==================  ======================================
      **Name (1)**        arcadia-crypto-user-identification
      ==================  ======================================

   .. image:: ../pictures/lb-malicious-users-details-3.png
      :align: center

Configure the User Identification Rules
=======================================

7. The **User Identification Rules** list is initially empty. Click **Add Item (1)**.

   .. image:: ../pictures/lb-malicious-users-details-4.png
      :align: center

8. Select ``Client IP Address`` for **Identifier Type (1)**, and then click **Apply (2)**.

   .. table::
      :widths: auto

      =========================  =================
      Object                     Value
      =========================  =================
      **Identifier Type (1)**    Client IP Address
      =========================  =================

   .. image:: ../pictures/lb-malicious-users-details-5.png
      :align: center

9. Click **Add Item** to configure another identification rule.

   .. image:: ../pictures/lb-malicious-users-details-6.png
      :align: center

10. Configure the second user identification rule with the following values, and then click **Apply**.

    .. table::
       :widths: auto

       =========================  =================
       Object                     Value
       =========================  =================
       **Identifier Type (1)**    HTTP Header Name
       **HTTP Header Name (2)**   Authorization
       =========================  =================

    .. image:: ../pictures/lb-malicious-users-details-6a.png
       :align: center

11. Verify that the rules list contains the two identification rules in the following order, and then click **Apply**:

    * **HTTP Header** with the key **Authorization**
    * **IP Address**

    .. image:: ../pictures/lb-malicious-users-details-6b.png
       :align: center

12. Click **Add User Identification (1)** to create the policy.

    .. image:: ../pictures/lb-malicious-users-details-7.png
       :align: center

Create a Custom Mitigation Policy Without CAPTCHA
=================================================

13. Back under **Common Security Controls**. Set **Malicious User Mitigation Settings (1)** to **Custom (2)**, and then open the **Custom (3)** policy selector.

   .. image:: ../pictures/lb-malicious-users-details-8.png
       :align: center

14. In the **Custom** policy selector, click **Add Item (1)** to create a malicious user mitigation policy.

    .. image:: ../pictures/lb-malicious-users-details-9.png
       :align: center

15. Set **Name (1)** to ``block-no-captcha``, and then click **Add Item (2)** under **Rules**.

    .. table::
       :widths: auto

       ============  ==================
       Object        Value
       ============  ==================
       **Name (1)**  block-no-captcha
       ============  ==================

    .. image:: ../pictures/lb-malicious-users-details-10.png
       :align: center

16. Configure the mitigation rule, and then click **Apply (3)**.

    .. table::
       :widths: auto

       ==================     =================
       Object                 Value
       ==================     =================
       **Threat Level (1)**   Low
       **Action (2)**         Block Temporarily
       ==================     =================

    .. image:: ../pictures/lb-malicious-users-details-11.png
       :align: center

17. Verify that the rules list contains the **Low** threat-level rule with the **Block Temporarily** mitigation action. Click **Add Malicious User Mitigation (1)** to create the policy.

    .. image:: ../pictures/lb-malicious-users-details-12.png
       :align: center

Apply and Save the Configuration
================================

18. Back under **Common Security Controls**, verify the following settings, and then click **Save HTTP Load Balancer**:

    * **User Identification Policy** is set to ``arcadia-crypto-user-identification``.
    * **Malicious User Detection** is set to **Enable**.
    * **Malicious User Mitigation And Challenges** is set to **Enable**.
    * **Malicious User Mitigation Settings** is set to **Custom**.
    * **Custom** is set to ``block-no-captcha``.

    .. image:: ../pictures/lb-malicious-users-details-13.png
       :align: center