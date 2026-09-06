# Demo Mapping and Connecting Your First Data Source

## Video Summary
This video is basically a walkthrough of connecting a first data source in Amazon Quick and mapping it so the platform can use it correctly. The main point is to show the practical flow: choose the source, bring the data in, match fields/columns, and make sure the structure looks right before moving on.

What you should get from it:
- how a raw source becomes usable inside Quick
- why field mapping matters for later analysis
- what to check before treating the connection as “done”

So if you’re wondering whether it’s skippable: it’s useful if you want to actually follow the platform workflow, not just know the idea in theory. It’s more of a hands-on process demo than a big new concept lesson.

If you want, I can also give you a super-short “30 second version” or a step-by-step summary of the exact actions shown.

## Key Steps
1. Open the two source files, the Online Retail II transaction export and the Product Category Lookup, in a spreadsheet. Scan the columns, the row counts, and the obvious gaps. Notice that both files carry a stock code column, which is the shared key that can join them later.

2. In Amazon Quick, open the Data page and upload the transaction CSV as a new dataset.

3. Review the upload preview. Check the auto-detected data types, the column names, and a few sample rows.

4. Confirm the file imported into SPICE, then compare the reported row count against what you expected from the file.

5. Note at least two data issues that are already visible in the preview, such as missing customer IDs or a date column read as text.

## Why It Works
Auditing the files first is what separates a reliable dashboard from a misleading one. A quick look reveals the shared key you'll join on and the risks you'll have to manage, like missing IDs. Uploading through the Data page imports the file into SPICE automatically, so your future dashboards query a fast in-memory copy instead of the original file. Matching the row count is the simple proof that every record made it in.

One thing to carry forward: a file upload always lands in SPICE, and the upload caps at one gigabyte. A sample file like this fits easily, but a real daily export can pass that limit fast. When it does, you connect through cloud storage or a database instead of uploading.

## Files Used
This demo uses no code. The files are provided in the course workspace:

- **Online Retail II transaction export (CSV):** the dataset you upload into Amazon Quick.
- **Product Category Lookup (CSV):** a reference table that shares the stock code key.

The uploaded dataset is saved into SPICE.

## Related Resources
[Amazon Quick Dataset page and SPICE import reference](https://docs.aws.amazon.com/quick/latest/userguide/working-with-datasets.html). Use this when you want the details on how file uploads import into SPICE.