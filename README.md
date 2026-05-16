<h1>Data Model</h1>
<h2>Conceptual Data Model</h2>
- reference - https://www.quest.com/learn/conceptual.aspx
<h1>Terminlogies used in Data WareHousing.</h1>
  - Reference - https://seattledataguy.substack.com/p/data-warehousing-essentials-a-precursor


<h2>Fact Tables</h2>
<p>A fact table is the primary table in a dimensional model where the numerical performance measurements of the business are stored.” -Ralph <p>
These tables contain the quantitative data for analysis and are typically transactional. For example, these transactions often represent sales, shipments, calls made, clicks, etc. If you’re keeping to a very strict data warehouse approach(most data warehouses I see don’t) then fact tables generally have two types of columns: measures and foreign keys to dimension tables. 

Measures are the numerical data (such as quantity sold, revenue, etc.) that analysts want to sum, average, or perform other calculations on. The foreign keys are the connections to the dimension tables.

<h2>Dimension Tables</h2>
<p>Dimension attributes serve as the primary source of query constraints, groupings, and report labels. In a query or report request, attributes are identified as the by words. For example, when a user states that he or she wants to see dollar sales by week by brand, week and brand must be available as dimension attributes.” -Ralph Kimball<p>
  
<p>These tables are descriptive attributes related to fact data. They provide context to the data in the fact tables, such as time, location, product details, customer information, etc.<p>

Dimension tables are often denormalized, meaning they might contain redundancy and usually include a wide variety of attributes to allow for flexible analysis. For example, a product dimension table might include not just an ID and name but also category, size, color, and other attributes that could be useful for analysis.

<h2>Bridge Tables (or Link Tables)</h2>
These are used in “many-to-many relationships” between dimensions. For instance, if you have a scenario where multiple products can be in different promotions at the same time, a bridge table would be used to manage this relationship.  -Ralph Kimball
Another common example used in most articles and in Kimballs’ books is healthcare and a patient’s diagnosis, which can have more than one diagnosis at a time. In turn, you’ll often see a bridge table used (See the model below).




Many data modelers try to avoid implementing too many bridge table situations as they can add a lot of risk in terms of miscounting or joining across the tables.

<h2>Role-Playing Dimension Tables</h2>
“Role-playing in a data warehouse occurs when a single dimension simultaneously appears several times in the same fact table.” -Ralph Kimball
A single physical dimension can be referenced multiple times in a fact table, playing different roles. For instance, a date dimension might be used in one fact table as the order date, shipping date, and delivery date. This is likely the most common example of a role playing dimension and honestly most people probably still just reference it as a dimension table.

