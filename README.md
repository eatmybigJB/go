```python
序号,配置规则名称 (Configuration Rule Name),风险等级,受影响资源具体名称 (Resource Name) & 环境
1,Azure OpenAI Jailbreak detection should be enabled and set to block,High,• Production: SCChatGPT_Content_Filter• Non-Prod: CustomContentFilter851
2,Azure OpenAI content filters should have Protected Material enabled for both code and text,Medium,• Production: SCChatGPT_Content_Filter
3,Azure OpenAI groundedness detection should be enabled,Low,"• Production: SCChatGPT_Content_Filter, Microsoft.DefaultV2, Microsoft.Default• Non-Prod: Microsoft.DefaultV2 (Dev & Staging), Microsoft.Default (Dev & Staging), CustomContentFilter210 (Dev), CustomContentFilter851 (Dev)"
4,Azure OpenAI RAI Policy Content Filters should be Enabled,Medium,• Production: SCChatGPT_Content_Filter
5,Azure OpenAI RAI Policy Content Filter should be Blocking,Low,"• Production: SCChatGPT_Content_Filter, Microsoft.DefaultV2• Non-Prod: Microsoft.DefaultV2 (Dev & Staging), CustomContentFilter851 (Dev), CustomContentFilter210 (Dev)"
6,OpenAI Service data storage for abuse monitoring should be disabled,Low,• Non-Prod: OpenAI-scgpt-sc-gpt-dev-uks
7,AI Service public network access should be disabled,Medium,"• Production: ContentSafety-cscgptprd-scb-chatgpt-production-uks• Non-Prod: ContentSafety-safechatgpt-scb-chatgpt-dev-uks (Dev), ContentSafety-cscgptstg-scb-chatgpt-production-uks (Staging)"
8,OpenAI Service public network access should be disabled,Medium,"• Production: OpenAI-scchatgpt-scb-chatgpt-production-uks• Non-Prod: OpenAI-scchatgpt-scb-chatgpt-production-uks (Staging), OpenAI-scchatgpt-scb-chatgpt-dev-uks (Dev), OpenAI-scgpt-sc-gpt-dev-uks (Dev)"
9,Azure AI Services resources should have key access disabled (disable local authentication),Medium,"• Production: ContentSafety-cscgptprd-scb-chatgpt-production-uks• Non-Prod: ContentSafety-safechatgpt-scb-chatgpt-dev-uks (Dev), ContentSafety-cscgptstg-scb-chatgpt-production-uks (Staging)"
10,OpenAI Service should use a managed identity,Medium,"• Production: OpenAI-scchatgpt-scb-chatgpt-production-uks• Non-Prod: OpenAI-scchatgpt-scb-chatgpt-dev-uks (Dev), OpenAI-scgpt-sc-gpt-dev-uks (Dev)"
11,AI Service should be configured with data loss prevention,Medium,"• Production: ContentSafety-cscgptprd-scb-chatgpt-production-uks• Non-Prod: ContentSafety-safechatgpt-scb-chatgpt-dev-uks (Dev), ContentSafety-cscgptstg-scb-chatgpt-production-uks (Staging)"
12,OpenAI Service should be configured with data loss prevention,Medium,"• Production: OpenAI-scchatgpt-scb-chatgpt-production-uks• Non-Prod: OpenAI-scchatgpt-scb-chatgpt-production-uks (Staging), OpenAI-scchatgpt-scb-chatgpt-dev-uks (Dev), OpenAI-scgpt-sc-gpt-dev-uks (Dev)"
