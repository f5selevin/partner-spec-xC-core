Service Policies for Parameter Validation
#########################################

An F5 Distributed Cloud (F5 XC) service policy contains an ordered list of rules. Each rule matches request attributes—such as the HTTP method, path, or query parameters—and applies an action. F5 XC evaluates the rules in order and applies the action from the first matching rule.

In this lab, you will configure the following behavior for **POST /v1/login**:

1. Allow a request when its **email** query parameter matches the configured email-address pattern.
2. Deny all other requests to the login path.
3. Allow requests to other application paths through a separate catch-all service policy.

Default Allow Service Policy
============================

1. In the F5 Distributed Cloud Console, navigate to **Web App & API Protection > Service Policies (1) > Service Policies (2)** and click **Add Service Policy (3)**.

   .. image:: ../pictures/sp-add.png
      :align: center

2. Configure the catch-all policy with the following values, and then click **Add Service Policy (3)**. This policy allows requests that are not matched by the parameter-inspection policy.

   .. table::
      :widths: auto

      =============================  ==================
      Object                         Value
      =============================  ==================
      **Name (1)**                   default-allow
      **Select Policy Rules (2)**    Allow All Requests
      =============================  ==================

   .. image:: ../pictures/sp-default-allow-all.png
      :align: center

Parameter Inspection Service Policy
===================================

The **arcadia-parameter-inspection** service policy contains both login rules. The allow rule must be first, followed by the deny rule, so that a valid login request is allowed before the broader login-path rule is evaluated.

Create the Policy and Allow Rule
--------------------------------

1. Click **Add Service Policy**. Enter **arcadia-parameter-inspection** for **Name (1)**. In the **Rules** section, next to **Custom Rule List**, click **Configure (2)**.

   The screenshot highlights the policy name, **Custom Rule List**, and the **Configure** control used to open the rule list.

   .. image:: ../pictures/sp-parameter-details-1.png
      :align: center

2. In the empty **Rules** list, click **Add Item (1)**.

   .. image:: ../pictures/sp-parameter-details-2.png
      :align: center

3. Configure the allow rule as follows:

   .. table::
      :widths: auto

      ===================  =============
      Object               Value
      ===================  =============
      **Name (1)**         email
      **Action (2)**       Allow
      **HTTP Method (3)**  POST
      ===================  =============

   In the **Request Match** section, click **Configure (4)** for **HTTP Path**.

   The numbered callouts identify the rule name, **Allow** action, **POST** method, **HTTP Path** configuration control, and **Argument Matchers > Add Item** control.

   .. image:: ../pictures/sp-parameter-details-3.png
      :align: center

4. In the dialog that appears, under **Prefix Values**, click **Add Item (1)**, enter **/v1/login (2)**, and click **Apply (3)**.

   .. image:: ../pictures/sp-parameter-details-4.png
      :align: center

5. The **HTTP Path** dialog closes. Click **Show Advanced Fields (5)** in the **Request Match** section.

6. In the expanded section, locate **Argument Matchers** and click **Add Item (1)**. For POST requests, parameters extracted from the JSON body are evaluated by **Argument Matchers**.

   .. image:: ../pictures/sp-parameter-details-5.png
      :align: center

7. Specify **Argument Name (1)** and click **Add Item (2)**. Configure the argument matcher with the following values:

   .. table::
      :widths: auto

      ======================================  =================================================
      Object                                  Value
      ======================================  =================================================
      **Argument Name (1)**                   email
      **Regex Values (3)**                    [A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}
      ======================================  =================================================

   Click **Apply (4)** to save the argument matcher.

   .. image:: ../pictures/sp-parameter-details-5a.png
      :align: center

8. Verify that **HTTP Path** is configured and that the **Argument Matchers** table contains the **email** matcher. Click **Apply (1)** to save the rule.

   .. image:: ../pictures/sp-parameter-details-6.png
      :align: center

9. The **email** rule is first in the **Rules** list. Click **Add Item** to create the fallback deny rule.

   .. image:: ../pictures/sp-parameter-details-7.png
      :align: center

Add the Fallback Deny Rule
--------------------------

1. Configure the second rule as follows:

   .. table::
      :widths: auto

      ===================  =============
      Object               Value
      ===================  =============
      **Name (1)**         deny-others
      **Action (2)**       Deny
      **HTTP Method (3)**  POST
      ===================  =============

   Under **HTTP Path**, click **Configure**, add **/v1/login** to **Prefix Values**, and click **Apply**. Do not add an argument matcher to this rule. Click **Apply (5)** to save the rule.

   .. image:: ../pictures/sp-parameter-details-8.png
      :align: center

Verify the Rule Order
---------------------

1. The order of the rules is important. The **arcadia-parameter-inspection** service policy must contain the following rules in this order:

   1. **email** — allows matching login requests.
   2. **deny-others** — denies the remaining login requests.

   The screenshot shows both rules in the required evaluation order. If necessary, reorder them before continuing.

   .. image:: ../pictures/sp-parameter-details-9.png
      :align: center      

2. Click **Apply (1)** to return to the service policy form.

3. Click **Add Service Policy (1)** to save the service policy.

   .. image:: ../pictures/sp-parameter-details-10.png
      :align: center

4. On the **Service Policies** page, verify that both **arcadia-parameter-inspection** and **default-allow** are listed. The **Rule Count** for **arcadia-parameter-inspection** should be **2**.

   .. image:: ../pictures/sp-res.png
      :align: center