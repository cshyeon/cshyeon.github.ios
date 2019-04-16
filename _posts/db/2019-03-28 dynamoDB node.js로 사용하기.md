---
layout: post
title: "dynamoDB node.js로 사용하기"
slug: "dynamoDB-with-nodejs"
date: 2019-02-28 14:26:28 +0900
categories: jekyll update
---

aws에서 node.js를 사용하여 dynamoDb를 사용하는 방법을 정리해 봅니다.


### 테이블 생성
```javascript
/* create table params
var params = {
    TableName : "Movies",
    KeySchema: [       
        { AttributeName: "year", KeyType: "HASH"},  //Partition key
        { AttributeName: "title", KeyType: "RANGE" }  //Sort key
    ],
    AttributeDefinitions: [       
        { AttributeName: "year", AttributeType: "N" },
        { AttributeName: "title", AttributeType: "S" }
    ],
    ProvisionedThroughput: {       
        ReadCapacityUnits: 10, 
        WriteCapacityUnits: 10
    }
}; */
function createTable(params) {
  return new Promise((resolve, reject) => {
    db.createTable(params, function(err, data) {
      if (err) {
        // console.error("Unable to create table. Error JSON:", JSON.stringify(err, null, 2));
        reject(err);
      } else {
        // console.log("Created table. Table description JSON:", JSON.stringify(data, null, 2));
        resolve(data);
      }
    });
  });  
}
```

### 테이블 삭제
```javascript
/* delete table params
  var deleteTableParams = {
    TableName : "practice"
  };
*/
function deleteTable(params) {
  return new Promise((resolve, reject) => {
    db.deleteTable(params, function(err, data) {
      if (err) {        
        reject(err);
      } else {        
        resolve(data);
      }
    });
  });
}
```

### batchWriteItem
- 한번에 리퀘스트로 여러 아이템들에대한 쓰기 작업을 진행한다. (최대 아이탬 갯수: 약 25 ~ 30)

```javascript
function batchWriteItem(tableName, dataArr) {
  return new Promise((resolve, reject) => {
    const batchWriteParams = {
      RequestItems: {
        [tableName]: makePutRequest(dataArr)
      }
    };
  
    db.batchWriteItem(batchWriteParams, function(err, data) {
      if (err) {
        reject(err);
      } else {
        resolve(data);
      }
    }); 
  });   
}

function makePutRequest(dataArr) {
  const requests = [];
  dataArr.forEach(data => {
    const item = {};
    Object.keys(data).forEach(key => {
      item[key] = { [getDataType(data[key])]: String(data[key]) };  // "KEY": { "N": "KEY_VALUE" },
    });   
    requests.push({PutRequest: {Item: item}});
  });
  
  return requests;
}

function getDataType(data) {
  const type = typeof data;  

  switch(type) {
    case "string": return 'S';
    case "number": return 'N';
    case "boolean": return 'BOOL';
    // TODO: 다른 타입의 case도 추가 필요
  }
}
```