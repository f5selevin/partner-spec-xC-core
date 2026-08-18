Configure an On-Premises Origin Pool
#####################################

Create an origin pool for the Arcadia service in the on-premises environment. The origin pool associates the service's private IP address with the on-premises F5 Distributed Cloud Customer Edge (CE) site, enabling the F5 Distributed Cloud Global Network to route application traffic to the service without exposing the origin to the public Internet.

1. In **Web App & API Protection**, select **Manage** -> **Load Balancers (1)** -> **Origin Pools (2)**, and then click **Add Origin Pool (3)**.

   .. image:: ../pictures/op-onprem-add.png
      :align: center

2. Enter the origin pool name and port, and then click **Add Item (3)** under **Origin Servers**.

   .. table::
      :widths: auto

      ==============================  =========================
      Parameter                       Value
      ==============================  =========================
      **Name (1)**                    arcadia-onprem-endpoint
      **Port (2)**                    80
      ==============================  =========================

   .. image:: ../pictures/op-onprem-details-1.png
      :align: center

3. Configure the origin server to use the private IP address reachable through the on-premises CE site. Enter the following values, and then click **Apply (5)**.

   .. table::
      :widths: auto

      =============================================  =========================================
      Parameter                                      Value
      =============================================  =========================================
      **Type of Origin Server (1)**                  IP address of Origin Server on given Sites
      **IP (2)**                                     10.1.1.6
      **Site (3)**                                   system/smsv2-$$namespace$$
      **Network (4)**                                Outside Network
      =============================================  =========================================

   .. image:: ../pictures/op-onprem-details-2.png
      :align: center

4. Verify that the origin server appears in the **Origin Servers** list, and click **Add Origin Pool (2)**.

   .. image:: ../pictures/op-onprem-details-3.png
      :align: center

The ``arcadia-onprem-endpoint`` origin pool now directs requests to ``10.1.1.6`` through the selected on-premises CE site.

.. note::
   The UDF deployment component ``Arcadia Crypto - OnPrem - K8S``is the backend service for the Arcadia application. It is deployed in an on-premises Kubernetes cluster and is not directly accessible from the public Internet.