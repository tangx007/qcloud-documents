## 1. 接口描述

本接口（ModifyLocalSourceIPPortTranslationAclRule）用于修改本端IP端口转换 ACL 策略。
接口请求域名：vpc.api.qcloud.com


## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，详情请参见<a href="https://cloud.tencent.com/document/product/215/4772" title="公共请求参数"> 公共请求参数 </a>页面。其中，此接口的 Action 字段为 ModifyLocalSourceIPPortTranslationAclRule。

| 参数名称 | 必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 是 | String | 系统分配的私有网络 ID，例如 vpc-dfg5445。|
| directConnectGatewayId | 是 | String | 系统分配的专线网关 ID，例如 dcg-4d545d。|
| translationIPPool | 是 | String | 映射后 IP 池。|
| aclRules.n | 是 | Array | ACL 策略信息。|
| aclRules.n.aclRuleId | 是 | Int | ACL 规则 ID，例如25。|
| aclRules.n.protocol | 是 | String | 协议：TCP、UDP 或 ALL。|
| aclRules.n.sourceCidr | 是 | String | 访问的源 IP，支持 IP、IP 段（CIDR 格式），如果不填写指所有IP。 |
| aclRules.n.sourcePort | 是 | String | 访问的源端口，支持xx-xx范围，不填或者填0或者0-0都表示不限端口。 |
| aclRules.n.destinationCidr | 是 | String | 访问的目的 IP，支持 IP、IP 段（CIDR 格式），如果不填写指所有IP。|
| aclRules.n.destinationPort | 是 | String | 访问的目的端口，支持xx-xx范围，不填或者填0或者0-0都表示不限端口。|

## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 公共错误码, 0表示成功，其他值表示失败。详见错误码页面的<a href="https://cloud.tencent.com/document/product/215/4781#.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81" title="公共错误码"> 公共错误码</a>。|
| message | String | 模块错误信息描述，与接口相关。|

 ## 4. 错误码表
  以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="https://cloud.tencent.com/doc/api/245/4924" title="VPC错误码"> VPC 错误码</a>。
 
| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的 VPC，VPC 资源不存在。请再次核实您输入的资源信息是否正确。可调用<a href="https://cloud.tencent.com/doc/api/245/%e5%88%9b%e5%bb%ba%e7%a7%81%e6%9c%89%e7%bd%91%e7%bb%9c?viewType=preview" title="查询私有网络列表"> 查询私有网络列表</a>（DescribeVpcEx）接口查询。|
| InvalidDirectConnectGateway.NotFound | 无效的专线网关，专线网关资源不存在。请再次核实您输入的资源信息是否正确。可调用<a href="https://cloud.tencent.com/doc/api/245/%e6%9f%a5%e8%af%a2%e4%b8%93%e7%ba%bf%e7%bd%91%e5%85%b3?viewType=preview" title="查询专线网关"> 查询专线网关</a>（DescribeDirectConnectGateway）接口查询。|
| InvalidLocalSourceIPPortTranslation.NotFound | 无效的本端 IP 端口转换规则，本端 IP 端口转换规则不存在。请再次核实您输入的资源信息是否正确。|
| InvalidLocalSourceIPPortTranslationAcl.Conflict | 本端 IP 端口转换规则 ACL 策略冲突，同一个专线网关下不同本端 IP 端口转换规则之前的 ACL 策略不能冲突。|

## 5. 示例
输入
<pre>
https://vpc.api.qcloud.com/v2/index.php?Action=ModifyLocalSourceIPPortTranslationAclRule
&<公共请求参数>
&vpcId=vpc-dfgg190
&directConnectGatewayId=dcg-ddf14d
&translationIPPool=138.0.0.11-138.0.0.111
&aclRules.0.aclRuleId=26
&aclRules.0.protocol=tcp
&aclRules.0.sourceCidr=111.0.0.1/18
&aclRules.0.sourcePort=80
&aclRules.0.destinationCidr=10.0.0.2/18
&aclRules.0.destinationPort=90
</pre>
输出
```
{
    "code":"0",
    "message":""
}
```

