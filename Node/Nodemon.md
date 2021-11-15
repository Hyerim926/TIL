# Nodemon

> Nodemon이란?

- 소스 변경 시 그걸 감지해서 자동으로 서버를 재시작해주는 tool, 서버를 일일히 재시작할 필요없음
- `npm install nodemon --save-dev`
- package.json
  ```javascript
  "scripts": {
  "backend": "nodemon server/index.js"
  ```
- `npm run backend`로 서버 실행
