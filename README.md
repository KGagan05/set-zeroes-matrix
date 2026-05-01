🔍 Step-by-Step Explanation
✅ Step 1: Initialization
m, n = len(matrix), len(matrix[0])
col0 = 1
* m, n → dimensions
* col0 → tells if first column needs to be zeroed
🔁 Step 2: Mark rows & columns
for i in range(m):
    if matrix[i][0] == 0:
        col0 = 0
    for j in range(1, n):
        if matrix[i][j] == 0:
            matrix[i][0] = 0
            matrix[0][j] = 0
  What’s happening?
Whenever you find a 0:
* Mark its row → matrix[i][0] = 0
* Mark its column → matrix[0][j] = 0
🧪 Example
Input:
1 1 1
1 0 1
1 1 1

After marking:
1 0 1
0 0 1
1 1 1

👉 First row & column now act like a memory board
🔁 Step 3: Traverse backwards and fill zeros
for i in range(m - 1, -1, -1):
    for j in range(n - 1, 0, -1):
        if matrix[i][0] == 0 or matrix[0][j] == 0:
            matrix[i][j] = 0
Why reverse traversal?

👉 To avoid overwriting markers too early
Logic:
If:
* row is marked (matrix[i][0] == 0)
* OR column is marked (matrix[0][j] == 0)
👉 then set matrix[i][j] = 0
🔁 Step 4: Handle first column separately
Why needed?
Because:
* matrix[0][0] is shared for both row & column
* So we use col0 to independently track first column
