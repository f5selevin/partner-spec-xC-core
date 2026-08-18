Route Application Traffic Between AWS and On-Premises Services
###############################################################

Configure an F5 Distributed Cloud HTTP Load Balancer route for the Arcadia application. The load balancer continues to send frontend requests to the AWS origin pool, while requests with the ``/v1/`` path prefix are sent through the F5 Distributed Cloud Global Network to the on-premises origin pool.

1. In **Web App & API Protection**, select **Manage** -> **Load Balancers (1)** -> **HTTP Load Balancers (2)**. In the row for the created load balancer, click the **Actions** menu (3).

   .. image:: ../pictures/lb-list.png
      :align: center

2. In the **Actions** menu, click **Manage Configuration (1)**.

   .. image:: ../pictures/lb-list-manage.png
      :align: center

3. On the load balancer configuration page, click **Edit Configuration (1)**.

   .. image:: ../pictures/lb-list-edit.png
      :align: center

4. Click on **Routes (1)** section, and then click **Configure (2)**.

   .. image:: ../pictures/lb-routes.png
      :align: center

5. Click **Add Item (1)** to create a route.

   .. image:: ../pictures/lb-routes-details-1.png
      :align: center

6. Configure the route with the following values, and then click **Add Item (3)** under **Origin Pools**.

   .. table::
      :widths: auto

      ==========================  ======================
      Parameter                   Value
      ==========================  ======================      
      **HTTP Method (1)**         ANY
      **Prefix (2)**              /v1/      
      ==========================  ======================

   .. image:: ../pictures/lb-routes-details-2.png
      :align: center

7. Select ``$$namespace$$/arcadia-onprem-endpoint`` in the **Origin Pools (1)** list, and click **Apply (2)**.

   .. image:: ../pictures/lb-routes-details-3.png
      :align: center

8. Back to **Http Load Balancer** settings page. Verify the origin pool is added and click **Apply (1)**.

   .. image:: ../pictures/lb-routes-details-4.png
      :align: center

9. Verify that the route list contains a simple route for the ``/v1/`` path prefix with ``arcadia-onprem-endpoint`` as its origin pool. Click **Apply**.

   .. image:: ../pictures/lb-routes-details-5.png
      :align: center

10. **Routes** are configured. Click **Save HTTP Load Balancer (1)** button.

    .. image:: ../pictures/lb-routes-details-6.png
       :align: center

The HTTP load balancer now uses path-based routing to send ``/v1/`` API requests to the private Arcadia service through the on-premises Customer Edge site. Requests that do not match this route continue to use the AWS frontend origin pool.