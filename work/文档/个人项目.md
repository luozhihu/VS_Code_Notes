---
title: 个人项目
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
code_clipboard: true
highlight_theme: darkula
headingLevel: 2
generator: "@tarslib/widdershins v4.0.23"

---

# 接口文档

Base URLs:

# Authentication

# 学生管理系统/管理员用户

## POST 登录

POST /User/doLogin

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|username|query|string| 是 |none|
|password|query|string| 是 |none|

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "登录成功",
  "data": null
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||状态码|
|» msg|string|true|none||说明|
|» data|null|true|none||数据|

## GET 查询自己资料

GET /User/profile

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "查询成功",
  "data": {
    "password": "sed ullamco sit",
    "role": "anim Duis consequat qui",
    "title": null,
    "email": "w.wiqtn@qq.com",
    "phoneNumber": "70",
    "department": null,
    "major": null,
    "userid": null,
    "gender": null,
    "age": null,
    "username": "孟勇"
  }
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|object|true|none||none|
|»» password|string|true|none||none|
|»» role|string|true|none||none|
|»» title|null|true|none||none|
|»» email|string|true|none||none|
|»» phoneNumber|string|true|none||none|
|»» department|null|true|none||none|
|»» major|null|true|none||none|
|»» userid|null|true|none||none|
|»» gender|null|true|none||none|
|»» age|null|true|none||none|
|»» username|string|true|none||none|

## GET 查询所有用户信息

GET /User/selectAllUser

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "查询成功",
  "data": [
    {
      "userName": "AliceStudent",
      "password": "123456",
      "role": "Student",
      "email": "alice@example.com",
      "phoneNumber": "123-456-7890",
      "userID": 1
    },
    {
      "userName": "BobTeacher",
      "password": "123456",
      "role": "Teacher",
      "email": "bob@example.com",
      "phoneNumber": "098-765-4321",
      "userID": 2
    },
    {
      "userName": "CharlieAdmin",
      "password": "123456",
      "role": "Admin",
      "email": "charlie@example.com",
      "phoneNumber": "555-1234",
      "userID": 3
    },
    {
      "userName": "DianaStudent",
      "password": "654321",
      "role": "Student",
      "email": "diana@example.com",
      "phoneNumber": "678-901-2345",
      "userID": 4
    },
    {
      "userName": "EvanTeacher",
      "password": "123456",
      "role": "Teacher",
      "email": "evan@example.com",
      "phoneNumber": "789-012-3456",
      "userID": 5
    },
    {
      "userName": "FrankAdmin",
      "password": "123456",
      "role": "Admin",
      "email": "frank@example.com",
      "phoneNumber": "890-123-4567",
      "userID": 6
    },
    {
      "userName": "GraceStudent",
      "password": "123456",
      "role": "Student",
      "email": "Grace@example.com",
      "phoneNumber": "901-234-5678",
      "userID": 7
    },
    {
      "userName": "HannahTeacher",
      "password": "123456",
      "role": "Teacher",
      "email": "hannah@example.com",
      "phoneNumber": "012-345-6789",
      "userID": 8
    },
    {
      "userName": "IanAdmin",
      "password": "123456",
      "role": "Admin",
      "email": "ian@example.com",
      "phoneNumber": "111-222-3333",
      "userID": 9
    },
    {
      "userName": "JasmineStudent",
      "password": "123456",
      "role": "Student",
      "email": "jasmine@example.com",
      "phoneNumber": "222-333-4444",
      "userID": 10
    },
    {
      "userName": "LuoStudent",
      "password": "luozhihu123",
      "role": "Student",
      "email": "Luo@example.com",
      "phoneNumber": "231-069-7151",
      "userID": 15
    },
    {
      "userName": "TangTeacher",
      "password": "tang123",
      "role": "Teacher",
      "email": "Tang@example.com",
      "phoneNumber": "666-666-6666",
      "userID": 16
    }
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|[object]|true|none||none|
|»» userName|string|true|none||none|
|»» password|string|true|none||none|
|»» role|string|true|none||none|
|»» email|string|true|none||none|
|»» phoneNumber|string|true|none||none|
|»» userID|integer|true|none||none|

## PUT 更新用户信息

PUT /User/updateProfile

> Body 请求参数

```json
{
  "password": "123456",
  "role": "Student",
  "title": null,
  "email": "luox@example.com",
  "phoneNumber": "333-4567",
  "department": null,
  "major": "New Computer Science",
  "userid": 1,
  "gender": "Male",
  "age": 26,
  "username": "LuoxStudent"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» password|body|string| 是 |none|
|» role|body|string| 是 |none|
|» title|body|null| 是 |none|
|» email|body|string| 是 |none|
|» phoneNumber|body|string| 是 |none|
|» department|body|null| 是 |none|
|» major|body|null| 是 |none|
|» userid|body|null| 是 |none|
|» gender|body|null| 是 |none|
|» age|body|null| 是 |none|
|» username|body|string| 是 |none|

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "更新成功",
  "data": null
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|null|true|none||none|

## POST 新增用户(学生)

POST /User/addUser

> Body 请求参数

```json
{
  "password": "123456",
  "role": "Student",
  "title": null,
  "email": "luox@example.com",
  "phoneNumber": "333-4567",
  "department": null,
  "major": "Computer Science",
  "userid": null,
  "gender": "Male",
  "age": 26,
  "username": "LuoxStudent"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» password|body|string| 是 |none|
|» role|body|string| 是 |none|
|» title|body|null| 是 |none|
|» email|body|string| 是 |none|
|» phoneNumber|body|string| 是 |none|
|» department|body|null| 是 |none|
|» major|body|string| 是 |none|
|» userid|body|null| 是 |none|
|» gender|body|string| 是 |none|
|» age|body|integer| 是 |none|
|» username|body|string| 是 |none|

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "新增成功",
  "data": 20
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|integer|true|none||none|

## DELETE 删除用户（学生）

DELETE /User/deleteUser

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|userid|query|integer| 否 |none|

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "删除成功",
  "data": null
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|null|true|none||none|

## GET 查询所有课程

GET /User/queryAllCourse

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "查询成功",
  "data": [
    {
      "courseID": 1,
      "teacherID": 2,
      "teacherName": "BobTeacher",
      "courseName": "数据库系统",
      "credits": 4
    },
    {
      "courseID": 2,
      "teacherID": 5,
      "teacherName": "EvanTeacher",
      "courseName": "算法设计与分析",
      "credits": 3
    },
    {
      "courseID": 3,
      "teacherID": 8,
      "teacherName": "HannahTeacher",
      "courseName": "计算机网络",
      "credits": 4
    },
    {
      "courseID": 4,
      "teacherID": 2,
      "teacherName": "BobTeacher",
      "courseName": "操作系统",
      "credits": 4
    },
    {
      "courseID": 5,
      "teacherID": 2,
      "teacherName": "BobTeacher",
      "courseName": "编译原理",
      "credits": 3
    }
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|[object]|true|none||none|
|»» courseID|integer|true|none||none|
|»» teacherID|integer|true|none||none|
|»» teacherName|string|true|none||none|
|»» courseName|string|true|none||none|
|»» credits|integer|true|none||none|

## POST 新增课程

POST /User/addCourse

> Body 请求参数

```json
{
  "courseID": null,
  "teacherID": 2,
  "teacherName": "BobTeacher",
  "courseName": "数据库系统",
  "credits": 4
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» courseID|body|integer¦null| 是 |none|
|» teacherID|body|integer| 是 |none|
|» teacherName|body|string| 是 |none|
|» courseName|body|string| 是 |none|
|» credits|body|integer| 是 |none|

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "新增成功",
  "data": 8
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|integer|true|none||none|

## DELETE 删除课程

DELETE /User/deleteCourse

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|CourseID|query|integer| 否 |none|

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

## PUT 修改课程

PUT /User/updateCourse

> Body 请求参数

```json
{
  "courseID": 1,
  "teacherID": 2,
  "teacherName": "BobTeacher",
  "courseName": "新大学英语",
  "credits": 4
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» courseID|body|integer| 是 |none|
|» teacherID|body|integer| 是 |none|
|» teacherName|body|string| 是 |none|
|» courseName|body|string| 是 |none|
|» credits|body|integer| 是 |none|

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "修改成功",
  "data": null
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|null|true|none||none|

# 学生管理系统/老师用户

## GET 查询登录状态

GET /User/isLogin

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "是否登录：true",
  "data": null
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|null|true|none||none|

## POST 登出

POST /User/logout

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

## GET 查询所有讲授课程

GET /Teacher/selectAllCourses

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "查询成功",
  "data": [
    {
      "teacherID": 2,
      "teacherName": "BobTeacher",
      "courseID": 1,
      "credits": 4,
      "courseName": "数据库系统"
    },
    {
      "teacherID": 2,
      "teacherName": "BobTeacher",
      "courseID": 4,
      "credits": 4,
      "courseName": "操作系统"
    },
    {
      "teacherID": 2,
      "teacherName": "BobTeacher",
      "courseID": 5,
      "credits": 4,
      "courseName": "大学英语"
    }
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|[object]|true|none||none|
|»» teacherID|integer|true|none||none|
|»» teacherName|string|true|none||none|
|»» courseID|integer|true|none||none|
|»» credits|integer|true|none||none|
|»» courseName|string|true|none||none|

## GET 根据课程id查询所有学生的成绩

GET /Teacher/selectGradesByCoursesId

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|CoursesId|query|string| 否 |none|

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "查询成功",
  "data": [
    {
      "studentID": 7,
      "courseID": 4,
      "gradeID": 4,
      "score": 99.99
    }
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|[object]|true|none||none|
|»» studentID|integer|true|none||none|
|»» courseID|integer|true|none||none|
|»» gradeID|integer|true|none||none|
|»» score|integer¦null|true|none||none|

## PUT 修改或录入成绩

PUT /Teacher/updateGrades

> Body 请求参数

```json
{
  "studentID": 1,
  "courseID": 4,
  "gradeID": 4,
  "score": 100
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» studentID|body|integer| 是 |none|
|» courseID|body|integer| 是 |none|
|» gradeID|body|integer| 是 |none|
|» score|body|integer| 是 |none|

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "修改、录入成功",
  "data": null
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|null|true|none||none|

# 学生管理系统/学生用户

## GET 查询成绩

GET /Student/queryGrade

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "查询成功",
  "data": [
    {
      "gradeID": 1,
      "studentID": 1,
      "score": 88.5,
      "courseID": 2
    },
    {
      "gradeID": 2,
      "studentID": 1,
      "score": 92,
      "courseID": 3
    },
    {
      "gradeID": 7,
      "studentID": 1,
      "score": null,
      "courseID": 1
    }
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|[object]|true|none||none|
|»» gradeID|integer|true|none||none|
|»» studentID|integer|true|none||none|
|»» score|number¦null|true|none||none|
|»» courseID|integer|true|none||none|

## GET 查询所有课程

GET /Student/queryCourse

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "查询成功",
  "data": [
    {
      "teacherID": 2,
      "teacherName": "BobTeacher",
      "courseID": 1,
      "courseName": "数据库系统",
      "credits": 4
    },
    {
      "teacherID": 5,
      "teacherName": "EvanTeacher",
      "courseID": 2,
      "courseName": "算法设计与分析",
      "credits": 3
    },
    {
      "teacherID": 8,
      "teacherName": "HannahTeacher",
      "courseID": 3,
      "courseName": "计算机网络",
      "credits": 4
    },
    {
      "teacherID": 2,
      "teacherName": "BobTeacher",
      "courseID": 4,
      "courseName": "操作系统",
      "credits": 4
    },
    {
      "teacherID": 2,
      "teacherName": "BobTeacher",
      "courseID": 5,
      "courseName": "大学英语",
      "credits": 4
    }
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|[object]|true|none||none|
|»» teacherID|integer|true|none||none|
|»» teacherName|string|true|none||none|
|»» courseID|integer|true|none||none|
|»» courseName|string|true|none||none|
|»» credits|integer|true|none||none|

## POST 学生选课

POST /Student/addGrade

> Body 请求参数

```json
{
  "studentID": 1,
  "courseID": 1,
  "score": null,
  "gradeID": null
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» studentID|body|integer| 是 |none|
|» courseID|body|integer| 是 |none|
|» score|body|null| 是 |none|
|» gradeID|body|null| 是 |none|

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "选课成功",
  "data": null
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|integer|true|none||none|

## DELETE 学生退课

DELETE /Student/deleteGrade

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|gradeId|query|string| 否 |none|

> 返回示例

> 成功

```json
{
  "code": 200,
  "msg": "退课成功",
  "data": null
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|null|true|none||none|

# 数据模型

