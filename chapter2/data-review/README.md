# Understanding Your Data Review

Here are the key points to carry forward:

- Businesses store data in separate tools, which creates data silos. Silos block any question that spans more than one system.

- Data integration joins those separate sources into one unified platform so they can be analyzed together.

- Before connecting anything, build a data source inventory: what each source is, where it comes from, its shape, and its risks.

- The inventory is where you spot differences between similar datasets, find shared keys that bridge sources, and document quality risks like missing IDs.

- Uploaded CSVs land in SPICE, a fast in-memory engine. SPICE holds up to two terabytes, but manual uploads cap at one gigabyte. Larger data needs a cloud or database connector.

- After connecting, verify the result: fix any wrong data types, and confirm the row count matches the original file.