# API Check List

#### ■Basic

- [ ] 使用RESTful API设计规范

- [ ] 接入swagger

- [ ] 使用HTTPS，沒有使用请提案

- [ ] 核心业务逻辑的判断应该由API决策后返回结果,前端不能处理

- [ ] 一个 API 只为一个业务功能服务

      比如，“用户信息更新 API” 只应该被用来更新用户信息。

- [ ] 确认提示信息是前端负责，还是 API 负责

#### ■About API URL

- [ ] 如果是独立的API服务，使用专用的子域名

      https://api.example.com
      

- [ ] 如果是与其他 Web 服务混合在一起的，通过 URL 标记加以区别
 
      https://www.example.com/api/

- [ ] 应将API的版本号放入URL,或将版本号放在HTTP头信息中，Github采用的后者



#### ■About response

- [ ] 服务器返回的数据格式使用JSON

- [ ] 返回的response包含字段满足需要

- [ ] 返回的response无无用字段

- [ ] 字段没有拼写错误，统一为驼峰或者下划线，下划线的前端应使用humps转换为camelizeKeys使用

#### ■安全
- [ ] 确认API有没有对被“非法”访问、调用的防御
- [ ] 确认API的身份认证，推荐使用OAuth  http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html

- [ ] API的具体网址中不能有动词，只能有名词，而且所用的名词往往与数据库的表格名对应

- [ ] API中的名词也应该使用复数

      https://api.example.com/v1/zoos
      https://api.example.com/v1/animals
      https://api.example.com/v1/employees
      
- [ ] 对于资源的具体操作类型，由HTTP动词表示

      GET（SELECT）：从服务器取出资源（一项或多项）
      POST（CREATE）：在服务器新建一个资源
      PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）
      PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）
      DELETE（DELETE）：从服务器删除资源

- [ ] API应该提供参数，过滤返回结果 

    - 参数的设计允许存在冗余，即允许API路径和URL参数偶尔有重复。比如，GET /zoo/ID/animals 与 GET /animals?zoo_id=ID 的含义是相同的


      ?limit=10：指定返回记录的数量
      ?offset=10：指定返回记录的开始位置。
      ?page=2&per_page=100：指定第几页，以及每页的记录数。
      ?sortby=name&order=asc：指定返回结果按照哪个属性排序，以及排序顺序。
      ?animal_type_id=1：指定筛选条件
      
- [ ] 返回正确使用状态码

      200 OK - [GET]
      201 CREATED - [POST/PUT/PATCH]：用户新建或修改数据成功
      202 Accepted - [*]：表示一个请求已经进入后台排队（异步任务）
      204 NO CONTENT - [DELETE]：用户删除数据成功
      ---
      400 INVALID REQUEST - [POST/PUT/PATCH]：用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的
      401 Unauthorized - [*]：表示用户没有权限（令牌、用户名、密码错误）
      403 Forbidden - [*] 表示用户得到授权（与401错误相对），但是访问是被禁止的
      404 NOT FOUND - [*]：用户发出的请求针对的是不存在的记录，服务器没有进行操作，该操作是幂等的
      406 Not Acceptable - [GET]：用户请求的格式不可得（比如用户请求JSON格式，但是只有XML格式）
      410 Gone -[GET]：用户请求的资源被永久删除，且不会再得到的
      422 Unprocesable entity - [POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误
      ---
      500 INTERNAL SERVER ERROR - [*]：服务器发生错误，用户将无法判断发出的请求是否成功
 
- [ ] 如果状态码是4xx，应该返回错误信息

      {
          error: "Invalid API key"
      }
    
- [ ] 返回的response符合以下规范
      
      格式：
      
      {
      status:0,
      data:{}||[],
      code:1000,
      msg:ʼʼ }
        
      內容：
      GET /zoos：列出所有动物园 -------- 返回资源对象的列表（数组）
      GET /zoos/ID：获取某个指定动物园的信息 -------- 返回单个资源对象
      POST /zoos：新建一个动物园 -------- 返回新生成的资源对象
      ----
      PUT /zoos/ID：更新某个指定动物园的信息（提供该动物园的全部信息）-------- 返回完整的资源对象
      PATCH /zoos/ID：更新某个指定动物园的信息（提供该动物园的部分信息）-------- 返回完整的资源对象 
      DELETE /zoos/ID：删除某个动物园 -------- 返回一个空文档
      ----
      GET /zoos/ID/animals：列出某个指定动物园的所有动物 -------- 返回资源对象的列表（数组）
      DELETE /zoos/ID/animals/ID：删除某个指定动物园的指定动物 -------- 返回一个空文档



    

## References

公司内部API规范

http://www.ruanyifeng.com/blog/2014/05/restful_api.html

https://codeplanet.io/principles-good-restful-api-design/

https://bourgeois.me/rest/

https://developer.github.com/v3/media/#request-specific-version