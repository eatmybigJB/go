```python
A.1 生产环境 (Production)
1. Azure OpenAI 服务: OpenAI-scchatgpt-scb-chatgpt-production-uks
类型： Azure OpenAI Account 违规项清单：

OpenAI Service public network access should be disabled (公网访问应禁用)

OpenAI Service should use a managed identity (应使用托管身份)

OpenAI Service should be configured with data loss prevention (应配置数据防泄漏 DLP)

2. 内容过滤策略 (OpenAI 子资源): SCChatGPT_Content_Filter
类型： RAI Policy (Content Filters) 归属： OpenAI-scchatgpt-scb-chatgpt-production-uks 违规项清单（高危）：

Azure OpenAI Jailbreak detection should be enabled and set to block (越狱检测未阻断)

Azure OpenAI content filters should have Protected Material enabled for both code and text (版权保护未完全开启)

Azure OpenAI groundedness detection should be enabled (接地性/幻觉检测未开启)

Azure OpenAI RAI Policy Content Filters should be Enabled (RAI 基础过滤器未全部启用)

Azure OpenAI RAI Policy Content Filter should be Blocking (RAI 基础过滤器未设置为阻断)

3. 内容安全服务: ContentSafety-cscgptprd-scb-chatgpt-production-uks
类型： Azure AI Services (Content Safety) 违规项清单：

AI Service public network access should be disabled (公网访问应禁用)

Azure AI Services resources should have key access disabled (disable local authentication) (应禁用本地 Key 认证)

AI Service should be configured with data loss prevention (应配置数据防泄漏 DLP)

A.2 非生产环境 (Non-Production / Staging / Dev)
4. Azure OpenAI 服务 (Dev): OpenAI-scgpt-sc-gpt-dev-uks
类型： Azure OpenAI Account 违规项清单：

OpenAI Service data storage for abuse monitoring should be disabled (滥用监控存储应禁用 - 隐私合规)

OpenAI Service public network access should be disabled

OpenAI Service should use a managed identity

OpenAI Service should be configured with data loss prevention

5. 内容过滤策略 (Dev): CustomContentFilter851
类型： RAI Policy 归属： OpenAI-scgpt-sc-gpt-dev-uks 违规项清单：

Azure OpenAI Jailbreak detection should be enabled and set to block

Azure OpenAI groundedness detection should be enabled

Azure OpenAI RAI Policy Content Filter should be Blocking

6. Azure OpenAI 服务 (Dev): OpenAI-scchatgpt-scb-chatgpt-dev-uks
类型： Azure OpenAI Account 违规项清单：

OpenAI Service public network access should be disabled

OpenAI Service should use a managed identity

OpenAI Service should be configured with data loss prevention

7. 内容安全服务 (Dev): ContentSafety-safechatgpt-scb-chatgpt-dev-uks
类型： Azure AI Services 违规项清单：

AI Service public network access should be disabled

Azure AI Services resources should have key access disabled

AI Service should be configured with data loss prevention

8. 内容安全服务 (Staging): ContentSafety-cscgptstg-scb-chatgpt-production-uks
类型： Azure AI Services 违规项清单：

AI Service public network access should be disabled

Azure AI Services resources should have key access disabled

AI Service should be configured with data loss prevention
