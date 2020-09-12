```javascript
var fs = require('fs');
var filename = 'array_manipulation_test8.txt';
var test = require('./array_manipulation');


async function readTestFile(filename){
    // var text = fs.readFileSync(filename).toString('utf-8').split('\r\n');
    var fullText = fs.createReadStream(filename).on('data', function (chunk) {
        // console.log(chunk.toString().split('\r\n'));
        let text = chunk.toString().split('\r\n')
        // console.log('text = ', text, 'text length = ', text.length);
    
    // console.log('text = ', text, 'text length ', text.length);
    // console.log('N = ', N);
    let A = [];
    let N = parseInt(text[0]);
    // console.log('N = ', N)
    for(let i = 1; i < text.length; i++){
        // console.log('text[',i,'] = ', text[i], 'text[',i,'] length = ' , text[i].length);
        // console.log('parseInt(text[',i,'])', parseInt(text[i]));
        let line = text[i];
        let str = '';
        let lineArr = [];
        for(let k = 0; k < line.length; k++){
            // console.log('text[',i,'][',k,'] = ',text[i][k]);
            str += text[i][k];
            if(text[i][k] === ' '){
                // console.log('empty!')
                let temp = parseInt(str);
                str = '';
                lineArr.push(temp);
            }
            if(k === line.length - 1){
                let temp = parseInt(str);
                str = '';
                lineArr.push(temp);
            }
        }
        A.push(lineArr);
    }
    // console.log('arrayManipulation(N, A) = ', arrayManipulation(N, A))
    let max = test(N , A);
    console.log(max);
});
}

readTestFile(filename)
.catch(err => console.log('this is error'))

```
