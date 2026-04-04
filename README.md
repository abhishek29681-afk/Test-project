# Test-project
#This project is related to extracting #values from a given data and storing it 

import pandas as pd

data = {
    "order_id": [1,2,3,4,5,6,7,8,9,10],
    "customer_id": [101,102,103,101,104,102,105,106,101,107],
    "product": ["Laptop","Phone","Tablet","Laptop","Headphones","Phone","Laptop","Tablet","Phone","Headphones"],
    "category": ["Electronics","Electronics","Electronics","Electronics","Accessories","Electronics","Electronics","Electronics","Electronics","Accessories"],
    "price": [60000,20000,15000,60000,2000,20000,60000,15000,20000,2000],
    "quantity": [1,2,1,1,3,1,2,1,1,2],
    "region": ["North","South","East","North","West","South","East","North","West","South"],
    "date": ["2024-01-01","2024-01-01","2024-01-03","2024-01-04","2024-01-03","2024-01-03","2024-01-07","2024-01-01","2024-01-09","2024-01-1"]
}

df = pd.DataFrame(data)
df["date"]= pd.to_datetime(df["date"],format= '%Y-%d-%m')
df['revenue']= df["price"]
mean= df["price"].mean()
new_mean= df.groupby('product')['price'].mean()
unique_cust=df['customer_id'].unique()
freq= df['customer_id'].nunique()
best_prod = df.groupby('product')['quantity'].sum()
sorted = best_prod.sort_values(ascending=False)
regions= df.groupby('region')['price'].sum()
Worst_region= regions.idxmin()
Best_region= regions.idxmax()
#print(Worst_region,regions.min())
#print(Best_region,regions.max())
Best_customer= df.groupby('customer_id')['price'].sum()
B_customer= Best_customer.sort_values(ascending=False)
#print(B_customer.head(1))
df['monthly_sales']= df['date'].dt.month
month_sale = df.groupby('monthly_sales')['revenue'].sum()
Best_avg = df.groupby('product')['revenue'].mean()
Sorted_prod= Best_avg.sort_values(ascending=False)
best_prod= Best_avg.idxmax()
#print('BEST_AVG_PRODUCT',best_prod,Sorted_prod.iloc[0])

