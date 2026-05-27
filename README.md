# Pyspark-DSL
Pyspark prerequisite code for google colab
!wget -q https://github.com/saiadityaus1/test1/raw/main/dt.txt -O dt.txt
!wget -q https://github.com/saiadityaus1/test1/raw/main/state.txt -O state.txt
!wget -q https://github.com/saiadityaus1/test1/raw/main/usdata.csv -O usdata.csv
!pip install -q pyspark
from pyspark import SparkConf
from pyspark import SparkContext
from pyspark.sql import SparkSession
conf = SparkConf().setAppName("pyspark").setMaster("local[*]").set("spark.driver.host","localhost").set("spark.driver.allowMultipleContexts","true")
sc = SparkContext(conf=conf)
spark = SparkSession.builder.config("spark.driver.allowMultipleContexts","true").getOrCreate()
print("DONE==== START YOUR WORK👇")

data = [
    (0, "06-26-2011", 300.4, "Exercise", "GymnasticsPro", "cash"),
    (1, "05-26-2011", 200.0, "Exercise Band", "Weightlifting", "credit"),
    (2, "06-01-2011", 300.4, "Exercise", "Gymnastics Pro", "cash"),
    (3, "06-05-2011", 100.0, "Gymnastics", "Rings", "credit"),
    (4, "12-17-2011", 300.0, "Team Sports", "Field", "cash"),
    (5, "02-14-2011", 200.0, "Gymnastics", None, "cash"),
    (6, "06-05-2011", 100.0, "Exercise", "Rings", "credit"),
    (7, "12-17-2011", 300.0, "Team Sports", "Field", "cash"),
    (8, "02-14-2011", 200.0, "Gymnastics", None, "cash")
]

df = spark.createDataFrame(data, ["id", "tdate", "amount", "category", "product", "spendby"])
df.show()




data2 = [
    (4, "12-17-2011", 300.0, "Team Sports", "Field", "cash"),
    (5, "02-14-2011", 200.0, "Gymnastics", None, "cash"),
    (6, "02-14-2011", 200.0, "Winter", None, "cash"),
    (7, "02-14-2011", 200.0, "Winter", None, "cash")
]

df1 = spark.createDataFrame(data2, ["id", "tdate", "amount", "category", "product", "spendby"])
df1.show()






data4 = [
    (1, "raj"),
    (2, "ravi"),
    (3, "sai"),
    (5, "rani")
]



cust = spark.createDataFrame(data4, ["id", "name"])
cust.show()

data3 = [
    (1, "mouse"),
    (3, "mobile"),
    (7, "laptop")
]

prod = spark.createDataFrame(data3, ["id", "product"])
prod.show()
