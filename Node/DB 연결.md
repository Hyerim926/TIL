# DB 연결

> MongoDB

- mongoose 설치 `npm install mongoose --save`

> index.js

```javascript
const mongoose = require("mongoose");

mongoose
  .connect(
    "mongodb+srv://youtube:youtube@youtubeclone.nlzoz.mongodb.net/myFirstDatabase?retryWrites=true&w=majority",
    { useNewUrlParser: true, useUnifiedTopology: true }
  )
  .then(() => console.log("MongoDB Connected..."))
  .catch((err) => console.log(err));
```

- 위의 형식은 DB 계정 및 암호가 노출되어있어 소스 공유 시 보안에 있어 문제가 될 수 있음

  > 해결책

  - 계정 정보가 담긴 파일을 생성해 분리해주자
  - `config\dev.js` , URI 정보
    ```javascript
    module.exports = {
      mongoURI:
        "mongodb+srv://youtube:youtube@youtubeclone.nlzoz.mongodb.net/myFirstDatabase?retryWrites=true&w=majority",
    };
    ```
  - `config\keys.js` , 개발/배포 버전 분리
    ```javascript
    if (process.env.NODE_ENV === "production") {
      module.exports = require("./prod"); //배포 시 쓸 파일
    } else {
      module.exports = require("./dev"); //개발 시 쓸 파일
    }
    ```
  - `config\prod.js`, 배포 시 쓸 파일 설정
    ```javascript
    module.exports = {
      mongoURI: process.env.MONGO_URI,
    };
    ```
  - `index.js` , key.js 정보 import

    ```javascript
    const config = require("./config/key");

    const mongoose = require("mongoose");
    mongoose
      .connect(config.mongoURI, {
        useNewUrlParser: true,
        useUnifiedTopology: true,
      })
      .then(() => console.log("MongoDB Connected..."))
      .catch((err) => console.log(err));
    ```

    - `.gitignore`에 추가하여 push해주기
