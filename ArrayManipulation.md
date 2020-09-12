Starting with a 1-indexed array of zeros and a list of operations, for each operation add a value to each of the array element between two given indices, inclusive. Once all operations have been performed, return the maximum value in the array.

Example


Queries are interpreted as follows:

    a b k
    1 5 3
    4 8 7
    6 9 1
Add the values of  between the indices  and  inclusive:

index->	 1 2 3  4  5 6 7 8 9 10
	[0,0,0, 0, 0,0,0,0,0, 0]
	[3,3,3, 3, 3,0,0,0,0, 0]
	[3,3,3,10,10,7,7,7,0, 0]
	[3,3,3,10,10,8,8,8,1, 0]
The largest value is  after all operations are performed.

Function Description

Complete the function arrayManipulation in the editor below.

arrayManipulation has the following parameters:

int n - the number of elements in the array
int queries[q][3] - a two dimensional array of queries where each queries[i] contains three integers, a, b, and k.
Returns

int - the maximum value in the resultant array
Input Format

The first line contains two space-separated integers  and , the size of the array and the number of operations.
Each of the next  lines contains three space-separated integers ,  and , the left index, right index and summand.

Constraints

Sample Input

5 3
1 2 100
2 5 100
3 4 100
Sample Output

200
Explanation

After the first update the list is 100 100 0 0 0.
After the second update list is 100 200 100 100 100.
After the third update list is 100 200 200 200 100.

The maximum value is .

```javascript
// Complete the arrayManipulation function below.
function arrayManipulation(n, queries) {
    console.log('queries = ', queries)
    let startTime = new Date();
    let C = new Array(n).fill(0);
    let amounts = Array(n);
    let max2 = 0;
    for(let i = 0; i < queries.length; i++){
        let que = queries[i];
        let start = que[0];
        let end = que[1];
        let amount = que[2];
        amounts[start - 1] = amounts[start - 1] || 0;
        console.log('amount = ', amount)
        amounts[start - 1] = amounts[start - 1] + amount;
        console.log('amount = ', amount)
        console.log('amounts[', start,'] = ', amounts[start]);
        amounts[end ] = amounts[end ] || 0;
        amounts[end ] = amounts[end ] - amount;
        console.log('amounts[', end,'] = ', amounts[end]);
        console.log('amounts = ', amounts);
    }
    // console.log('amounts = ', amounts, 'amounts length = ', amounts.length);
    var current = 0;
    for (var i = 0; i < n; i++) {
        current += (amounts[i] || 0);
        if (current > max2) {
        max2 = current;
        }
    }
    // console.log(max2);
    let endtime2 = new Date();
    let exeTime2 = endtime2 - startTime;
    
    // console.log('execution time end = ', exeTime2 / 1000, 's');
    return max2;
}

 module.exports = arrayManipulation;
```
