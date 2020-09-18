# How to leverage Data Science and Optimization for Economical Supply Chain Network Design!!!
This work explains how OR and ML in tandem can help us making a cost efficient decisions. I have used a Supply Chain Network Design use case to explain benefits of ML+OR together.

## Problem Statement
Comapny __A__ sell the __Finished Good (FG)__ to its customers. The FG is made of __Part-1__ and __Part-2__. Part-1 is manufactured at location LOC and Part-2 is sourced from a supplier. Then Part-1 & Part-2 is assembled, this assembly of the products involve certain cost.
<br>


Once the product is assembled, it is shipped to the customers using parcel delivery. Now the company __A__ is looking to establish the Distribution Centres(DCs) to benefit from the economies of scale shippment to DC and different assembly costs at different DC. The main objective is to idetify the number and location of DCs to located across the country at a minimum total cost. The total cost includes the operating cost of DC, assembly cost, and shipment costs.

## CodeFile
This file explains the mathematical modeling and executeable python script. Please note that the fundamental data has not been shared to avoid any conflicts. However I have defined below how you can prepare the data to execute the scripts.


1. __Demand Data__: Please prepare the demand data as below
 > __df_demand__: This is a dataframe for the demand of the customers. It should have Columns in the order <font color=blue>['Customer ID', 'Latitude', 'Longitude', 'Demand']</font>.

2. __Distribution Centres Data__:
 > __df_DC__: This is a dataframe for the data related to Distribution Centres. It shall have columns in the order of <font color=blue>['DC ID', 'Latitude', 'Longitude', 'Assemb', 'Fixed', 'q0', 'c0', 'q1_old', 'c1', 'q2_old', 'c2']</font>  where:
  > * DC ID, Latitude, Longitude: Represent the ID and geographical coordinates for each of the Distributed Centre location.
  > * Assemb: Unit Assembly Cost of a FG at each DC
  > * Fixed: Represent the fixed cost of operating the DC having initial capacity __q0__
  > * c0, c1, c2: Unit Cost of exceeding the capacities q0, q1_old, q2_old respectively where q2_old > q1_old > q0.
