Configure AWS Origin Pool
#############################

Create an origin pool that represents the Arcadia frontend service running on the AWS site. The origin is addressed by its private IP, so F5 Distributed Cloud sends traffic to it through the site rather than through the public Internet.

1. In **Web App & API Protection**, select **Manage** -> **Load Balancers (1)** -> **Origin Pools (2)**, and then click **Add Origin Pool (3)**.

   .. image:: ../pictures/op-list-add.png
      :align: center

2. Enter the pool metadata, and click **Add Item (3)** under **Origin Servers**.

   .. table::
      :widths: auto

      ==============================  ============================
      Parameter                       Value
      ==============================  ============================
      **Name (1)**                    arcadia-aws-endpoint
      **Port (2)**                    80
      ==============================  ============================

   .. image:: ../pictures/op-details-1.png
      :align: center

3. Make Origin pool to point to Secure Mesh Site v2. Select the  **IP address of Origin Server on given Sites** for **Type of Origin Server**. Fill the appeared fields as in the table below:

   .. table::
      :widths: auto

      =============================================  =========================================
      Parameter                                      Value
      =============================================  =========================================
      **Type of Origin Server (1)**                  IP address of Origin Server on given Sites
      **IP (2)**                                     10.0.149.75
      **Site (3)**                                   system/spec-core-aws-frontend
      **Network (4)**                                Outside Network
      =============================================  =========================================

   Click **Apply (5)** to add the origin to the pool.

   .. image:: ../pictures/op-details-2.png
      :align: center

.. note::
   The Arcadia frontend service is deployed inside a dedicated AWS VPC and is not exposed directly to the public Internet. The address ``10.0.149.75`` is the private IP address assigned to the deployed frontend service within that VPC. An F5 Distributed Cloud Customer Edge (CE) site provides connectivity to the VPC, enabling F5 Distributed Cloud to reach the frontend service at this private address.

4. Back to **Origin Pool** config page. Verify that the origin server is added to the pool and click **Add Origin Pool (1)**.

   .. image:: ../pictures/op-details-3.png
      :align: center

5. The new ``arcadia-aws-endpoint`` pool appears in the **Origin Pools** list:

   .. image:: ../pictures/op-add-res.png
      :align: center