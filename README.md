import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_csv("ventes.csv")

# Create revenue column
df["revenue"] = df["prix"] * df["qte"]

# -----------------------------
# a. Sales by Product (Quantity)
# -----------------------------
sales_product = df.groupby("produit")["qte"].sum()

plt.figure(figsize=(8,5))
sales_product.plot(
    kind="bar",
    color=["skyblue", "orange", "green"]
)

plt.title("Sales by Product", fontsize=14)
plt.xlabel("Product")
plt.ylabel("Quantity Sold")
plt.xticks(rotation=0)
plt.grid(axis="y", linestyle="--", alpha=0.7)
plt.show()

# -----------------------------
# b. Revenue by Product
# -----------------------------
revenue_product = df.groupby("produit")["revenue"].sum()

plt.figure(figsize=(8,5))
revenue_product.plot(
    kind="bar",
    color=["purple", "red", "gold"]
)

plt.title("Revenue by Product", fontsize=14)
plt.xlabel("Product")
plt.ylabel("Revenue")
plt.xticks(rotation=0)
plt.grid(axis="y", linestyle="--", alpha=0.7)
plt.show()
