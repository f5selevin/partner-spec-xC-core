Configure AWS Origin Pool
#############################

Create an origin pool that represents the Arcadia frontend service running on the AWS site. The origin is addressed by its private IP, so F5 Distributed Cloud sends traffic to it through the site rather than through the public Internet.

1. **Open the origin-pool form (1--3).** In **Web App & API Protection**, select **Manage** -> **Load Balancers** -> **Origin Pools (2)**, and then click **Add Origin Pool (3)**.

   .. image:: ../pictures/op-list-add.png
      :align: center

2. **Set the pool name and add an origin (1--3).** Enter the pool metadata, leave **Health Checks** and **TLS** unconfigured, and click **Add Item (3)** under **Origin Servers**.

   .. table::
      :widths: auto

      ==============================  ============================
      Parameter                       Value
      ==============================  ============================
      **Name (1)**                    arcadia-aws-endpoint
      **Health Checks**               Not configured
      **TLS**                         Not configured
      ==============================  ============================

   .. image:: ../pictures/op-details-1.png
      :align: center

3. **Configure the private origin (1--5).** Select a private-IP origin, enter the Arcadia frontend service IP, and bind the origin to the AWS site and its outside network.

   .. table::
      :widths: auto

      =============================================  =========================================
      Parameter                                      Value
      =============================================  =========================================
      **Type of Origin Server (1)**                  IP address of Origin Server on given Sites
      **Private IP Type (2)**                        IP
      **IP (3)**                                     10.0.149.75
      **Site Type (4)**                              Site
      **Site (5)**                                   system/$$awsSiteName$$
      **Network**                                    Outside Network
      **SNAT Pool Configuration**                    Default
      =============================================  =========================================

   Click **Apply** to add the origin to the pool.

   .. image:: ../pictures/op-details-2.png
      :align: center

4. **Configure pool traffic handling (1--6).** Verify that the private origin is present, set the service port and traffic-selection parameters, and then click **Add Origin Pool (6)**.

   .. table::
      :widths: auto

      ==============================================  ================================
      Parameter                                       Value
      ==============================================  ================================
      **Origin Servers (1)**                          Private IP 10.0.149.75
      **Origin Server Port Type (2)**                 Port
      **Port (3)**                                    80
      **Upstream Connection Pool Reuse (4)**          Enable Connection Pool Reuse
      **Port Used for Health Check**                  Endpoint port
      **Load Balancer Algorithm (5)**                 Load Balancer Override
      **Endpoint Selection**                          Local Endpoints Preferred
      ==============================================  ================================

   ``Local Endpoints Preferred`` selects an origin on the local site when one is available. ``Load Balancer Override`` permits the load balancer's origin-selection configuration to override the pool algorithm.

   .. image:: ../pictures/op-details-3.png
      :align: center

5. **Verify the created pool (1).** Confirm that ``arcadia-aws-endpoint`` appears in the **Origin Pools** list in the current namespace. The list should now contain both ``arcadia-aws-endpoint`` and the existing ``op1-arcadia-crypto`` pool.

   .. image:: ../pictures/op-add-res.png
      :align: center