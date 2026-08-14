Publish and test the application
########################################

In this exercise, you will publish the Arcadia Crypto application with an F5 Distributed Cloud HTTP load balancer. The load balancer will distribute requests across the three origin pools by using the round-robin algorithm.

Create the HTTP load balancer
=============================

1. In the F5 Distributed Cloud Console, go to **Web App & API Protection** -> **Load Balancers** -> **HTTP Load Balancers**.

2. Click **Add HTTP Load Balancer** and configure the following values:

   .. table::
      :widths: auto

      ====================================    =========================================================
      Object                                  Value
      ====================================    =========================================================
      **Name**                                arcadia-re-lb
      **Domains**                             $$namespace$$.spec-core.f5se.com
      **Load Balancer Type**                  HTTP
      **Automatically Manage DNS Records**    Enable
      ====================================    =========================================================

.. Screenshot placeholder: basic HTTP load balancer configuration.

Add the origin pools
====================

1. In the load balancer's **Origin Pools** section, click **Add Item**.

2. Add the following three origin pools:

   * ``$$namespace$$/arcadia-origin-pool-1``
   * ``$$namespace$$/arcadia-origin-pool-2``
   * ``$$namespace$$/arcadia-origin-pool-3``

3. Set the load-balancing algorithm to **Round Robin**.

4. Give each origin pool the same weight and priority, if those fields are displayed.

5. Click **Apply**, and then click **Save and Exit**.

.. Screenshot placeholder: all three origin pools configured with Round Robin.

Test round-robin distribution
=============================

1. Wait for the load balancer configuration and managed DNS record to become active.

2. Browse to :ext_link:`http://$$namespace$$.spec-core.f5se.com`.

3. Note the origin pool name displayed in the page header and footer.

.. Screenshot placeholder: application response from the first origin pool.

4. Refresh the page several times. Confirm that the header and footer rotate among:

   * **Arcadia Crypto Origin Pool 1**
   * **Arcadia Crypto Origin Pool 2**
   * **Arcadia Crypto Origin Pool 3**

.. Screenshot placeholder: responses showing the other origin pool names.

.. note:: A browser or intermediary may reuse an existing connection. If the displayed origin does not change, perform additional refreshes or open the URL in a new private browsing window.

.. warning:: Some service providers retain recursive DNS responses for several minutes. If the domain does not resolve after the load balancer becomes active, try a resolver such as ``1.1.1.1`` or ``8.8.8.8``.

Verify your configuration
=========================

The exercise is complete when:

* ``$$namespace$$.spec-core.f5se.com`` loads the Arcadia Crypto application.
* Repeated requests display more than one origin pool name.
* All three origin pool names appear after multiple requests.

