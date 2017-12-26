1.下载接口,并放入根目录

2.修改config/routes.php 在
>    // Run Slim Routes for App
>    $app->run();
之前加入以下代码
>$app->group('/user',function(){
>    $this->get("/payjs","App\Utils\WePayjs:route_home");
>    $this->post("/payjs","App\Utils\WePayjs:handel");
>})->add(new Auth());
>$app->group("/payjs",function(){
>    $this->post("/callback/wepay","App\Utils\WePayjs:handel_callback");
>    $this->post("/status","App\Utils\WePayjs:status");
>});
3. 修改模板 /resources/views/material/user/main.tpl
><li>
>	<a href="/user/code">
>		<i class="icon icon-lg">code</i>&nbsp;充值
>	</a>
></li>

改成

><li>
>	<a href="/user/payjs">
>		<i class="icon icon-lg">code</i>&nbsp;充值
>	</a>
></li>
4. 修改配置文件 app/Utils/WePayjs.php中
>  'mchid' => 1511606484,   // 商户号
>   'token' => "IWDxq5wILmuWZEQKj1hEFFsHXBAotsD8" // 安全验证码

