# How to leverage Data Science and Optimization for Economical Supply Chain Network Design!!!
This work explains how OR and ML in tandem can help us making cost-efficient decisions. I have used a Supply Chain Network Design use case to explain benefits of ML+OR together.

## Problem Statement
Comapny __A__ sell the __Finished Good (FG)__ to its customers. The FG is made of __Part-1__ and __Part-2__. Part-1 is manufactured at location LOC and Part-2 is sourced from a supplier. Then Part-1 & Part-2 is assembled, this assembly of the products involve certain cost.
<br>


Once the product is assembled, it is shipped to the customers using parcel delivery. Now the company __A__ is looking to establish the Distribution centers (DCs) to benefit from economies of scale shippment to DC and different assembly costs at different DC. The main objective is to idetify the number and location of DCs to located across the country at a minimum total cost. The total cost includes the operating cost of DC, assembly cost, and shipment costs.

## CodeFile
This file explains the mathematical modelling using python script. Please note that the data has been anonymized for confidential reasons. However I have defined the guidelines and description how to prepare the data for execution of the script.


1. __Demand Data__: Please prepare the demand data as below
 > __df_demand__: This is a dataframe for the demand of the customers. It should have Columns in the order <font color=blue>['Customer ID', 'Latitude', 'Longitude', 'Demand']</font>.
 
  > * __Customer ID__: Defines the identifcation of each of the customer e.g. C0001. Customer ID is a `string` data type.
  
  > * __Latitude/Longitude__: Geographical coordinates for locations of customers. Geographical coordinates shall be in degrees and must have `float` data type.
  
  > * __Demand__: Demand of the FG for each of the customer. Demand must be of positive `int` data type
  
  
2. __Distribution Centres Data__: A DC is a facility that is usually smaller than a firm's main warehouse and is used for receipt, temporary storage, and redistribution of goods according to the customer orders as they are received. The DC has a capacity upto which it can receive the maximum number of units. This is also a decision variable as what shall be the capacity of a DC. Further, to operate the DC, company incurs some cost recognised as the operating cost. Operating costs usually consist of a fixed cost and variable cost. The fixed cost is applicable upto a certain capacity called as initial capacity. For any capacity exceeding the initial capacity, marginal operating costs are applied. Below I describe how to prepare the data file for DCs.  

Read more about distribution center here: https://en.wikipedia.org/wiki/Distribution_center
 > __df_DC__: This is a dataframe for the data related to DCs. It shall have columns in the order of <font color=blue>['DC ID', 'Latitude', 'Longitude', 'Assemb', 'Fixed', 'q0', 'c0', 'q1_old', 'c1', 'q2_old', 'c2']</font>  where: 
 
  > * __DC ID, Latitude, Longitude__: Attributes similar to customers data for each of the locations for DC.
  > * __Assemb__: Cost of assembling the Part-1 and Part-2 at each of the DC. It can have `float` or `int` data type.
  > * __Fixed__: Fixed cost of a DC. The fixed cost is applied to initial capacity `q0`. Different DCs can have different `Fixed` cost and `q0` initial capacity. Both can have `float` or `int` data type.
  > * c0, c1, c2: Unit Cost of exceeding the capacities q0, q1_old, q2_old respectively where q2_old > q1_old > q0.
