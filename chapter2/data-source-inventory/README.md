# Data Source Inventory In Action

Let's walk through the habit that prevents most broken dashboards: building a data source inventory before you connect a single file. We'll use a small online retailer as the example.

Start by cataloging what you have
A **data source inventory** is a structured document that forces you to write down what each source is, where it comes from, what shape it's in, and what's risky about it. Here's a starter inventory for our retailer:

| Source | Origin | Data shape | Quality risks |
|--------|--------|------------|---------------|
| Online transactions | E-commerce export (CSV) | ~500K rows of invoices, products, quantities, prices | 25% of rows have no Customer ID; cancellations mixed in with sales |
| Product category lookup | Reference table (CSV) | ~200 rows mapping stock codes to categories | May not cover every stock code |
| Second retailer sales | Sample dataset (CSV) | ~10K rows, includes profit and discount columns | Different columns than the main export |

Filling this in takes minutes, and it already surfaces three things you would otherwise learn the hard way.

#### Look closer than "they both have sales"
Two datasets can look identical and answer completely different questions. Our main export tracks revenue, but the second retailer's file also carries profit and discount. If someone asks "what's our margin?", only one of these sources can answer. The inventory is where you catch that difference before you build on the wrong file.

#### Hunt for the shared key
The inventory is also where you find the bridges between sources. Our transaction file logs each sale by stock code, and the product lookup defines categories by that same stock code. That common column is a ***shared key***, and it's what lets you connect the two files later.

#### Document the risks now
The most valuable column is "quality risks." Writing down "25% of Customer IDs are missing" today saves a stressful investigation next week when a customer count doesn't add up.

#### Connect, then verify
With the inventory done, you can bring the files in. When you upload a CSV into Amazon Quick, it imports automatically into ***SPICE***, a fast in-memory engine. Your dashboards query that quick copy, not the original file. Two limits matter. SPICE can hold up to two terabytes, but a manual file upload caps at one gigabyte. A sample file fits easily. Real daily exports can pass one gigabyte fast, and at that point you switch to a cloud storage or database connector instead.

Before you move on, check two things the system often gets wrong:

- **Data types**. The platform guesses each column's type, and sometimes it guesses wrong. An invoice date read as plain text can't power a trend line until you change its type to a date.

- **Row count**. Compare the row count in Amazon Quick against your original file. When the numbers match, the data came in cleanly.

Ten minutes of inventory, key-checking, and risk-noting is what lets you answer "where did this number come from?" with confidence when an executive asks.