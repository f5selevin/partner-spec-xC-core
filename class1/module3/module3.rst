Parameter Inspection
####################

F5 Distributed Cloud Services can inspect request parameters and enforce matching criteria through service policies.

A service policy evaluates request attributes against configured match conditions and applies the specified action. Ordered service policies can enforce positive security for a specific application operation while preserving access to other application resources.

In this module, you will allow POST requests to **/v1/login** only when the **email** parameter matches the specified email address pattern. Any other POST request to **/v1/login** is denied. A final default allow policy explicitly permits traffic to all other URLs and request types.


**Module 3 - All sections**

.. toctree::
   :maxdepth: 1
   :glob:

   lab*/lab*
