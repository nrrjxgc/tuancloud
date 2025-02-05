# 订阅 ChatGPT 和 DALLE-3 是否比使用 API 更经济？

OpenAI 提供的 ChatGPT 和 DALLE-3 是生成文本和图像的强大工具。但是，使用这些服务的成本如何？是通过订阅 ChatGPT Plus 还是直接使用 API 更划算呢？本文将为您详细分析。

## OpenAPI API 的成本基础

OpenAI API 的费用与使用的令牌数量相关，令牌数量大致与查询中的单词数量成正比。通常，10 个单词对应约 13 个令牌。接下来，我们将分别分析 DALLE-3 和 ChatGPT 的成本。

## DALLE-3 的成本分析

### 订阅 ChatGPT Plus

通过订阅 ChatGPT Plus，每月支付 20 美元，您可以访问 DALLE-3 生成高质量图像。目前的限制是每三小时 40 条消息。这意味着，如果每月生成 500 张图像，每张图像的成本约为 0.04 美元。

### 使用 DALLE-3 API

使用 DALLE-3 API，您可以通过以下 Python 代码生成 1024 x 1024 的图像：

python
from openai import OpenAI
import sys

client = OpenAI(api_key='在这里输入API KEY')

msg="."

if (len(sys.argv)>1):
    msg=str(sys.argv[1])

try:
  response = client.images.generate(model="dall-e-3", prompt=msg,
              size="1024x1024", quality="standard", n=1,)

  print(f"<img src="https://www.ababai.cn/detail/%7Bresponse.data%5B0%5D.url%7D">")

except Exception as e:
  print("发生错误:", str(e))


每张图像的费用为 0.03 美元。例如，生成了 99 张图像，费用为 4.04 美元，即每张图像成本约为 0.04 美元。

## ChatGPT API 的成本分析

对于 ChatGPT API，费用如下：

- **gpt-4**：每千个令牌 $0.03
- **gpt-3.5-turbo-0125**：每千个令牌 $0.0005

以下是一个示例代码：

python
from openai import OpenAI
import sys

client = OpenAI(api_key='API KEY HERE')

msg="."

if (len(sys.argv)>1):
    msg=str(sys.argv[1])

try:
  completion = client.chat.completions.create(messages=[{ "role": "user",  
                "content": msg, } ],model="gpt-3.5-turbo",)
  str = completion.choices[0].message.content
  print(str)

except Exception as e:
  print("发生错误:", str(e))


在 2024 年 3 月 4 日，生成了 120 个 API 调用，费用为 $0.03。每次调用的费用约为 $0.00025。这意味着，20 美元的订阅可以进行 80,000 个 API 调用。

## 结论

如果您每月生成的 ChatGPT 查询不超过千次，并且生成的图像少于 100 张，那么选择 API 方式会更划算。

👉 [WildCard | 一分钟注册，轻松订阅海外线上服务](https://bbtdd.com/WildCard)