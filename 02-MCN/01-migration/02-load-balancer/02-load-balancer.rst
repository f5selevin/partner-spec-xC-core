Route Application Traffic to the Frontend Service in AWS
########################################################

Update the F5 Distributed Cloud HTTP Load Balancer to use the AWS origin pool. This directs application traffic for the configured domain to the frontend service running in AWS.

1. Navigate to **Web App & API Protection > Load Balancers (1) > HTTP Load Balancers (2)**. In the row for the created load balancer, click the **Actions** menu (3).

   .. image:: ../pictures/lb-list.png
      :align: center

2. In the **Actions** menu, click **Manage Configuration (1)**.

   .. image:: ../pictures/lb-list-manage.png
      :align: center

3. On the load balancer configuration page, click **Edit Configuration (1)**.

   .. image:: ../pictures/lb-list-edit.png
      :align: center

4. In the **Origins** section, click **Edit (1)**.

   .. image:: ../pictures/lb-op-edit.png
      :align: center

5. Update  the **Origin Pool** to just created origin pool: ``$$namespace$$/arcadia-aws-endpoint`` **(1)**. Click **Apply (2)** to save the changes.

   .. image:: ../pictures/lb-op-edit-details-1.png
      :align: center

6. Verify that ``arcadia-aws-endpoint`` appears in the **Origin Pools** list, and then click **Save HTTP Load Balancer (1)**.

   .. image:: ../pictures/lb-op-edit-details-2.png
      :align: center