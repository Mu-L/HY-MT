<p align="left">
   <a href="README.md">English</a>  ｜ 中文</a>&nbsp
</p>
<br><br>

<p align="center">
 <img src="imgs/hunyuanlogo.png" width="400"/> <br>
</p><p></p>


<p align="center">
    🤗&nbsp;<a href="https://huggingface.co/collections/tencent/hy-mt15"><b>Hugging Face</b></a>&nbsp;&nbsp;|&nbsp;&nbsp;
    <img src="https://avatars.githubusercontent.com/u/109945100?s=200&v=4" width="16"/>&nbsp;<a href="https://modelscope.cn/collections/Tencent-Hunyuan/HY-MT15"><b>ModelScope</b></a>&nbsp;&nbsp;|&nbsp;&nbsp;
</p>

<p align="center">
    🖥️&nbsp;<a href="https://hunyuan.tencent.com" style="color: red;"><b>Official Website</b></a>&nbsp;&nbsp;|&nbsp;&nbsp;
    🕹️&nbsp;<a href="https://hunyuan.tencent.com/chat/HunyuanDefault?from=modelSquare&modelId=hunyuan-mt-1.8b"><b>Demo</b></a>&nbsp;&nbsp;&nbsp;&nbsp;
</p>

<p align="center">
    <a href="https://github.com/Tencent-Hunyuan/HY-MT"><b>Github</b></a>
</p>


## 模型介绍

混元翻译模型1.5版本，包含一个1.8B翻译模型HY-MT1.5-1.8B和7B翻译模型HY-MT1.5-7B。两个模型均重点支持33语种互译，支持5种民汉/方言。其中HY-MT1.5-7B是我们WMT25冠军模型的升级版，优化解释性翻译和语种混杂情况，新增支持术语干预、上下文翻译、带格式翻译。HY-MT1.5-1.8B在参数量只有不到HY-MT-7B的三分之一情况下，翻译效果跟HY-MT1.5-7B相近，真正做到的速度又快效果又好。1.8B这个尺寸在经过量化后，能够支持端侧部署和实时翻译场景，应用面广泛。



### 核心特性与优势
- HY-MT1.5-1.8B同尺寸业界效果最优，超过大部分商用翻译API
- HY-MT1.5-1.8B支持端侧部署和实时翻译场景，应用面广泛
- HY-MT1.5-7B相比9月份开源版本，优化注释和语种混杂情况
- 两个模型均支持术语干预、上下文翻译、带格式翻译


## 新闻
<br>

* 2025.12.30 我们在Hugging Face开源了 **HY-MT1.5-1.8B**和**HY-MT1.5-7B**
* 2025.9.1 我们在Hugging Face开源了 **Hunyuan-MT-7B**和**Hunyuan-MT-Chimera-7B**。

## 效果
<div align='center'>
<img src="imgs/overall_performance.png" width = "100%" />
</div>

更多的实验效果和分析可以参考我们的[技术报告](./HY_MT1_5_Technical_Report.pdf)。

&nbsp;

## 模型链接
| 模型名  | 简介 | 下载链接 |
| ----------- | ----------- |-----------
| HY-MT1.5-1.8B  | 混元1.8B翻译模型 |🤗 [Model](https://huggingface.co/tencent/HY-MT1.5-1.8B)|
| HY-MT1.5-1.8B-FP8 | 混元1.8B翻译模型，fp8量化    | 🤗 [Model](https://huggingface.co/tencent/HY-MT1.5-1.8B-FP8)|
| HY-MT1.5-1.8B-GPTQ-Int4 | 混元1.8B翻译模型， int4 量化    | 🤗 [Model](https://huggingface.co/tencent/HY-MT1.5-1.8B-GPTQ-Int4)|
| HY-MT1.5-1.8B-GGUF | 混元1.8B翻译模型， llama.cpp    | 🤗 [Model](https://huggingface.co/tencent/HY-MT1.5-1.8B-GGUF)|
| HY-MT1.5-7B | 混元7B翻译模型    | 🤗 [Model](https://huggingface.co/tencent/HY-MT1.5-7B)|
| HY-MT1.5-7B-FP8 | 混元7B翻译模型，fp8量化     | 🤗 [Model](https://huggingface.co/tencent/HY-MT1.5-7B-FP8)|
| HY-MT1.5-7B-GPTQ-Int4 | 混元7B翻译模型， int4 量化     | 🤗 [Model](https://huggingface.co/tencent/HY-MT1.5-7B-GPTQ-Int4)|
| HY-MT1.5-7B-GGUF | 混元7B翻译模型， llama.cpp    | 🤗 [Model](https://huggingface.co/tencent/HY-MT1.5-7B-GGUF)|


## Prompts

*注意：下面的source_language和target_languge都使用语言的全称，中文使用中文全称，英文使用英文全称。*

### 中外互译prompt模板
---
```
将以下文本翻译为{target_language}，注意只需要输出翻译后的结果，不要额外解释：

{source_text}
```
---

### 外外互译prompt模板
---
```
Translate the following segment into {target_language}, without additional explanation.

{source_text}
```
---


### 术语干预模板
---
```
参考下面的翻译：
{source_term} 翻译成 {target_term}

将以下文本翻译为{target_language}，注意只需要输出翻译后的结果，不要额外解释：
{source_text}
```
---

### 上下文翻译模板
---
```
{context}
参考上面的信息，把下面的文本翻译成{target_language}，注意不需要翻译上文，也不要额外解释：
{source_text}

```
---

### 带格式翻译模板
---
```
将以下<source></source>之间的文本翻译为中文，注意只需要输出翻译后的结果，不要额外解释，原文中的<sn></sn>标签表示标签内文本包含格式信息，需要在译文中相应的位置尽量保留该标签。输出格式为：<target>str</target>

<source>{src_text_with_format}</source>
```
---

## 使用 transformers 推理
首先，需要安装最新版本的transformers，推荐v4.56.0及以上
```SHELL
pip install transformers==4.56.0
```

*!!! If you want to load fp8 model with transformers, you need to change the name"ignored_layers" in config.json to "ignore" and upgrade the compressed-tensors to compressed-tensors-0.11.0.*

以下代码片段展示了如何使用 transformers 库加载和使用模型。

```python
from transformers import AutoModelForCausalLM, AutoTokenizer
import os

model_name_or_path = "tencent/Hunyuan-MT-7B"

tokenizer = AutoTokenizer.from_pretrained(model_name_or_path)
model = AutoModelForCausalLM.from_pretrained(model_name_or_path, device_map="auto")  # You may want to use bfloat16 and/or move to GPU here
messages = [
    {"role": "user", "content": "Translate the following segment into Chinese, without additional explanation.\n\nGet something off your chest"},
]
tokenized_chat = tokenizer.apply_chat_template(
    messages,
    tokenize=True
    add_generation_prompt=False,
    return_tensors="pt"
)

outputs = model.generate(tokenized_chat.to(model.device), max_new_tokens=2048)
output_text = tokenizer.decode(outputs[0])
```


我们推荐使用下面这组参数进行推理。注意，我们的模型没有默认 system_prompt。

```json

{
  "top_k": 20,
  "top_p": 0.6,
  "repetition_penalty": 1.05,
  "temperature": 0.7
}
```

&nbsp;

支持的语种:
| Languages         | Abbr.   | Chinese Names   |
|-------------------|---------|-----------------|
| Chinese           | zh      | 中文            |
| English           | en      | 英语            |
| French            | fr      | 法语            |
| Portuguese        | pt      | 葡萄牙语        |
| Spanish           | es      | 西班牙语        |
| Japanese          | ja      | 日语            |
| Turkish           | tr      | 土耳其语        |
| Russian           | ru      | 俄语            |
| Arabic            | ar      | 阿拉伯语        |
| Korean            | ko      | 韩语            |
| Thai              | th      | 泰语            |
| Italian           | it      | 意大利语        |
| German            | de      | 德语            |
| Vietnamese        | vi      | 越南语          |
| Malay             | ms      | 马来语          |
| Indonesian        | id      | 印尼语          |
| Filipino          | tl      | 菲律宾语        |
| Hindi             | hi      | 印地语          |
| Traditional Chinese | zh-Hant| 繁体中文        |
| Polish            | pl      | 波兰语          |
| Czech             | cs      | 捷克语          |
| Dutch             | nl      | 荷兰语          |
| Khmer             | km      | 高棉语          |
| Burmese           | my      | 缅甸语          |
| Persian           | fa      | 波斯语          |
| Gujarati          | gu      | 古吉拉特语      |
| Urdu              | ur      | 乌尔都语        |
| Telugu            | te      | 泰卢固语        |
| Marathi           | mr      | 马拉地语        |
| Hebrew            | he      | 希伯来语        |
| Bengali           | bn      | 孟加拉语        |
| Tamil             | ta      | 泰米尔语        |
| Ukrainian         | uk      | 乌克兰语        |
| Tibetan           | bo      | 藏语            |
| Kazakh            | kk      | 哈萨克语        |
| Mongolian         | mn      | 蒙古语          |
| Uyghur            | ug      | 维吾尔语        |
| Cantonese         | yue     | 粤语            |


## 训练数据格式处理

如果需要微调我们的模型，建议将数据处理成以下格式。

```python
messages = [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "海水为什么是咸的" },
    {"role": "assistant", "content": "海水是咸的主要是因为其中含有许多溶解在水中的盐类和矿物质。这些盐类和矿物质来自于地球表面的岩石和土壤中的化学物质，随着时间的推移，它们被带到了海洋中。当海水蒸发时，水分蒸发掉了，但盐类和矿物质仍然留在水中，导致海水变得更加咸味。因此，海水的咸度是由其中的盐类和矿物质的含量决定的。"}
]

from transformers import AutoTokenizer
tokenizer = AutoTokenizer.from_pretrained("your_tokenizer_path", trust_remote_code=True)
train_ids = tokenizer.apply_chat_template(messages)
```

&nbsp;

## 使用 LLaMA-Factory 训练

我们将介绍如何使用`LLaMA-Factory`来进行微调混元模型。

### 安装环境

开始之前，确保你已经安装了以下代码库：
1. 使用[LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory)官方指导进行安装。
2. 使用[DeepSpeed](https://github.com/deepspeedai/DeepSpeed#installation)官方指导进行安装（可选）。
3. 安装配套的transformer库。当前混元提交的transformer代码正在评审中，需要获取配套的分支。
```
pip install git+https://github.com/huggingface/transformers@4970b23cedaf745f963779b4eae68da281e8c6ca
```

### 准备数据

我们需要准备自定义的数据集：

1. 请将您的数据以`json`格式进行组织，并将数据放入`LLaMA-Factory`的`data`目录中。当前使用的是`sharegpt`格式的数据集，需要遵循以下格式：
```
[
  {
    "messages": [
      {
        "role": "system",
        "content": "系统提示词（选填）"
      },
      {
        "role": "user",
        "content": "人类指令"
      },
      {
        "role": "assistant",
        "content": "模型回答"
      }
    ]
  }
]
```
可以参考前面章节中对[数据格式](#训练数据格式处理)的说明。

2. 在`data/dataset_info.json`文件中提供您的数据集定义，并采用以下格式：
```
"数据集名称": {
  "file_name": "data.json",
  "formatting": "sharegpt",
  "columns": {
    "messages": "messages"
  },
  "tags": {
    "role_tag": "role",
    "content_tag": "content",
    "user_tag": "user",
    "assistant_tag": "assistant",
    "system_tag": "system"
  }
}
```

### 训练

1. 将`llama_factory_support/example_configs`目录下的文件都拷贝到`LLaMA-Factory`的`example/hunyuan`目录下。
2. 修改配置文件`hunyuan_full.yaml`中的模型路径和数据集名称，其他的配置请根据需要进行修改。
  ```
  ### model
  model_name_or_path: [!!!add the model path here!!!]

  ### dataset
  dataset: [!!!add the data set name here!!!]
  ```
3. 执行训练命令
    * 运行单机训练
    请注意这里需要设置`DISABLE_VERSION_CHECK`环境变量，避免版本冲突。
    ```
    export DISABLE_VERSION_CHECK=1
    llamafactory-cli train examples/hunyuan/hunyuan_full.yaml
    ```
    * 运行多机训练
    在每个节点上执行以下命令。请注意将`torchrun`需要的`NNODES`、`NODE_RANK`、`MASTER_ADDR`和`MASTER_PORT`按照您运行的环境进行配置。
    ```
    export DISABLE_VERSION_CHECK=1
    FORCE_TORCHRUN=1 NNODES=${NNODES} NODE_RANK=${NODE_RANK} MASTER_ADDR=${MASTER_ADDR} MASTER_PORT=${MASTER_PORT} \
    llamafactory-cli train examples/hunyuan_full.yaml
    ```

&nbsp;

## 推理和部署

HunyuanLLM可以采用TensorRT-LLM, vLLM或sglang部署。为了简化部署过程HunyuanLLM提供了预构建docker镜像，详见一下章节。

镜像：https://hub.docker.com/r/hunyuaninfer/hunyuan-7b/tags

## 使用TensorRT-LLM推理
### Docker:

为了简化部署过程，HunyuanLLM提供了预构建docker镜像 (注意： 该镜像要求Host的Cuda版本为12.8以上）：

[hunyuaninfer/hunyuan-7b:hunyuan-7b-trtllm](https://hub.docker.com/r/hunyuaninfer/hunyuan-7b/tags) 。您只需要下载模型文件并用下面代码启动docker即可开始推理模型。
```shell
# 拉取
国内：
docker pull docker.cnb.cool/tencent/hunyuan/hunyuan-7b:hunyuan-7b-trtllm
国外：
docker pull hunyuaninfer/hunyuan-7b:hunyuan-7b-trtllm

# 启动
docker run --privileged --user root --name hunyuanLLM_infer --rm -it --ipc=host --ulimit memlock=-1 --ulimit stack=67108864 --gpus=all hunyuaninfer/hunyuan-7b:hunyuan-7b-trtllm
```

注: Docker容器权限管理。以上代码采用特权模式（--privileged）启动Docker容器会赋予容器较高的权限，增加数据泄露和集群安全风险。建议在非必要情况下避免使用特权模式，以降低安全威胁。对于必须使用特权模式的场景，应进行严格的安全评估，并实施相应的安全监控、加固措施。

### BF16部署

#### Step1：执行推理

#### 方式1：命令行推理

下面我们展示一个代码片段，采用`TensorRT-LLM`快速请求chat model：
修改 examples/pytorch/quickstart_advanced.py 中如下代码：


```python
def setup_llm(args):
    kv_cache_config = KvCacheConfig(
        enable_block_reuse=not args.disable_kv_cache_reuse,
        free_gpu_memory_fraction=args.kv_cache_fraction,
    )
    spec_config = None

    hf_ckpt_path="$your_hunyuan_model_path"
    tokenizer = AutoTokenizer.from_pretrained(hf_ckpt_path, trust_remote_code=True)
    llm = LLM(
        tokenizer=tokenizer,
        model=args.model_dir,
        backend='pytorch',
        disable_overlap_scheduler=args.disable_overlap_scheduler,
        kv_cache_dtype=args.kv_cache_dtype,
        kv_cache_config=kv_cache_config,
        attn_backend=args.attention_backend,
        use_cuda_graph=args.use_cuda_graph,
        cuda_graph_padding_enabled=args.cuda_graph_padding_enabled,
        cuda_graph_batch_sizes=args.cuda_graph_batch_sizes,
        load_format=args.load_format,
        print_iter_log=args.print_iter_log,
        enable_iter_perf_stats=args.print_iter_log,
        torch_compile_config=TorchCompileConfig(
            enable_fullgraph=args.use_torch_compile,
            enable_inductor=args.use_torch_compile,
            enable_piecewise_cuda_graph= \
                args.use_piecewise_cuda_graph)
        if args.use_torch_compile else None,
        moe_backend=args.moe_backend,
        enable_trtllm_sampler=args.enable_trtllm_sampler,
        max_seq_len=args.max_seq_len,
        max_batch_size=args.max_batch_size,
        max_num_tokens=args.max_num_tokens,
        enable_attention_dp=args.enable_attention_dp,
        tensor_parallel_size=args.tp_size,
        pipeline_parallel_size=args.pp_size,
        moe_expert_parallel_size=args.moe_ep_size,
        moe_tensor_parallel_size=args.moe_tp_size,
        moe_cluster_parallel_size=args.moe_cluster_size,
        enable_chunked_prefill=args.enable_chunked_prefill,
        speculative_config=spec_config,
        trust_remote_code=args.trust_remote_code,
        gather_generation_logits=args.return_generation_logits)

    sampling_params = SamplingParams(
        end_id=127960,
        max_tokens=args.max_tokens,
        temperature=args.temperature,
        top_k=args.top_k,
        top_p=args.top_p,
        return_context_logits=args.return_context_logits,
        return_generation_logits=args.return_generation_logits,
        logprobs=args.logprobs)
    return llm, sampling_params


def main():
    args = parse_arguments()
    prompts = args.prompt if args.prompt else example_prompts

    llm, sampling_params = setup_llm(args)
    new_prompts = []
    for prompt in prompts:
        messages = [{"role": "user", "content": f"{prompt}"}]
        new_prompts.append(
            llm.tokenizer.apply_chat_template(messages,
                                                tokenize=False,
                                                add_generation_prompt=True))
    prompts = new_prompts
    outputs = llm.generate(prompts, sampling_params)

    for i, output in enumerate(outputs):
        prompt = output.prompt
        generated_text = output.outputs[0].text
        print(f"[{i}] Prompt: {prompt!r}, Generated text: {generated_text!r}")
```

运行方式：

```shell
python3 quickstart_advanced.py --model_dir "HunyuanLLM模型路径" --tp_size 1
```

#### 方式2：服务化推理

下面我们展示使用`TensorRT-LLM`服务化的方式部署模型和请求。

以tencent/Hunyuan-7B-Instruct为例
准备配置文件：

```
cat >/path/to/extra-llm-api-config.yml <<EOF
use_cuda_graph: true
cuda_graph_padding_enabled: true
cuda_graph_batch_sizes:
- 1
- 2
- 4
- 8
- 16
- 32
print_iter_log: true
EOF
```

启动服务：

```shell
trtllm-serve \
  /path/to/HunYuan-7b \
  --host localhost \
  --port 8000 \
  --backend pytorch \
  --max_batch_size 32 \
  --max_num_tokens 16384 \
  --tp_size 1 \
  --kv_cache_free_gpu_memory_fraction 0.6 \
  --trust_remote_code \
  --extra_llm_api_options /path/to/extra-llm-api-config.yml
```

服务启动成功后, 使用 OpenAI API 进行模型推理调用：
```
curl -X POST "http://localhost:8000/v1/chat/completions" \
  -H "Content-Type: application/json" \
  --data '{
    "model": "HunYuan/HunYuan-7b",
    "messages": [
      {
        "role": "user",
        "content": "Write a short summary of the benefits of regular exercise"
      }
    ]
  }'
```

#### FP8/Int4量化模型部署：
目前 TensorRT-LLM 的 fp8 和 int4 量化模型正在支持中，敬请期待。


## 使用vLLM推理
### 版本要求:

请使用vLLM v0.10.0之后的版本进行部署和推理

需要安装指定版本的transformers，我们将在不久后完成对transformers主分支的合入
```SHELL
pip install git+https://github.com/huggingface/transformers@4970b23cedaf745f963779b4eae68da281e8c6ca
```
### BF16部署

以tencent/Hunyuan-7B-Instruct为例，已经通过上述的transformers获取了模型地址
```shell
export MODEL_PATH=PATH_TO_MODEL
```

#### Step1：执行推理

#### 方式1：命令行推理

下面我们展示一个代码片段，采用`vLLM`快速请求chat model：

注: vLLM组件远程代码执行防护。下列代码中vLLM组件的trust-remote-code配置项若被启用，将允许加载并执行来自远程模型仓库的代码，这可能导致恶意代码的执行。除非业务需求明确要求，否则建议该配置项处于禁用状态，以降低潜在的安全威胁。


```python
import os
from typing import List, Optional
from vllm import LLM, SamplingParams
from vllm.inputs import PromptType
from transformers import AutoTokenizer

model_path=os.environ.get('MODEL_PATH')
tokenizer = AutoTokenizer.from_pretrained(model_path, trust_remote_code=True)

llm = LLM(model=model_path,
        tokenizer=model_path,
        trust_remote_code=True,
        dtype='bfloat16',
        tensor_parallel_size=4,
        gpu_memory_utilization=0.9)

sampling_params = SamplingParams(
    temperature=0.7, top_p=0.8, max_tokens=4096, top_k=20, repetition_penalty=1.05)

messages = [
    {
        "role": "system",
        "content": "You are a helpful assistant.",
    },
    {"role": "user", "content": "Write a short summary of the benefits of regular exercise"},
]

tokenized_chat = tokenizer.apply_chat_template(messages, tokenize=True, add_generation_prompt=True, return_tensors="pt")

dummy_inputs: List[PromptType] = [{
    "prompt_token_ids": batch
} for batch in tokenized_chat.numpy().tolist()]

outputs = llm.generate(dummy_inputs, sampling_params)

# Print the outputs.
for output in outputs:
    prompt = output.prompt
    generated_text = output.outputs[0].text
    print(f"Prompt: {prompt!r}, Generated text: {generated_text!r}")
```

#### 方式2：服务化推理

下面我们展示使用`vLLM`服务化的方式部署模型并请求

我们启动服务，运行 :
```shell
python3 -m vllm.entrypoints.openai.api_server \
    --host 0.0.0.0 \
    --port 8000 \
    --trust-remote-code \
    --model ${MODEL_PATH} \
    --tensor-parallel-size 1 \
    --dtype bfloat16 \
    --quantization experts_int8 \
    --served-model-name hunyuan \
    2>&1 | tee log_server.txt
```

运行成功后, 运行请求脚本：
```shell
curl http://0.0.0.0:8000/v1/chat/completions -H 'Content-Type: application/json' -d '{
"model": "hunyuan",
"messages": [
    {
        "role": "system",
        "content": [{"type": "text", "text": "You are a helpful assistant."}]
    },
    {
        "role": "user",
        "content": [{"type": "text", "text": "请按面积大小对四大洋进行排序，并给出面积最小的洋是哪一个？直接输出结果。"}]
    }
],
"max_tokens": 2048,
"temperature":0.7,
"top_p": 0.6,
"top_k": 20,
"repetition_penalty": 1.05,
"stop_token_ids": [127960]
}'
```

### 量化模型部署：

本部分介绍采用vLLM部署量化后模型的流程。


#### Int8量化模型部署：
部署Int8-weight-only版本HunYuan-7B模型

我们启动Int8服务，运行：
```shell
python3 -m vllm.entrypoints.openai.api_server \
    --host 0.0.0.0 \
    --port 8000 \
    --trust-remote-code \
    --model ${MODEL_PATH} \
    --tensor-parallel-size 1 \
    --dtype bfloat16 \
    --served-model-name hunyuan \
    --quantization experts_int8 \
    2>&1 | tee log_server.txt
```

#### Int4量化模型部署：
部署Int4-weight-only版本HunYuan-7B模型，采用GPTQ方式：

```shell
export MODEL_PATH=PATH_TO_INT4_MODEL
```
接着我们启动Int4服务，运行：
```shell
python3 -m vllm.entrypoints.openai.api_server \
    --host 0.0.0.0 \
    --port 8000 \
    --trust-remote-code \
    --model ${MODEL_PATH} \
    --tensor-parallel-size 1 \
    --dtype bfloat16 \
    --served-model-name hunyuan \
    --quantization gptq_marlin \
    2>&1 | tee log_server.txt
```


#### FP8量化模型部署：
部署W8A8C8版本HunYuan-7B模型

我们启动FP8服务，运行：
```shell
python3 -m vllm.entrypoints.openai.api_server \
    --host 0.0.0.0 \
    --port 8000 \
    --trust-remote-code \
    --model ${MODEL_PATH} \
    --tensor-parallel-size 1 \
    --dtype bfloat16 \
    --served-model-name hunyuan \
    --kv-cache-dtype fp8 \
    2>&1 | tee log_server.txt
```

## 使用sglang推理

### BF16部署

#### Step1: 拉取镜像


```
docker pull lmsysorg/sglang:latest
```

- 启动 API server:

```
docker run --entrypoint="python3" --gpus all \
    --shm-size 32g \
    -p 30000:30000 \
    --ulimit nproc=10000 \
    --privileged \
    --ipc=host \
     lmsysorg/sglang:latest \
    -m sglang.launch_server --model-path hunyuan/huanyuan_7B --tp 1 --trust-remote-code --host 0.0.0.0 --port 30000
```

#### Step2：执行推理

#### 方式1：命令行推理

下面我们展示一个代码片段，采用`sglang`快速请求chat model：


```python
import sglang as sgl
from transformers import AutoTokenizer

model_path=os.environ.get('MODEL_PATH')


tokenizer = AutoTokenizer.from_pretrained(model_path, trust_remote_code=True)

messages = [
    {
        "role": "system",
        "content": "You are a helpful assistant.",
    },
    {"role": "user", "content": "Write a short summary of the benefits of regular exercise"},
]
prompts = []
prompts.append(tokenizer.apply_chat_template(
    messages,
    tokenize=False,
    add_generation_prompt=True
))
print(prompts)

llm = sgl.Engine(
    model_path=model_path,
    tp_size=1,
    trust_remote_code=True,
    mem_fraction_static=0.7,
)

sampling_params = {"temperature": 0.7, "top_p": 0.8, "top_k": 20, "max_new_tokens": 4096}
outputs = llm.generate(prompts, sampling_params)
for prompt, output in zip(prompts, outputs):
    print(f"Prompt: {prompt}\nGenerated text: {output['text']}")
```

#### 方式2：服务化推理

下面我们展示使用`sglang`服务化的方式部署模型和请求。

```shell
model_path="HunyuanLLM模型路径"
python3 -u -m sglang.launch_server \
    --model-path $model_path \
    --tp 4 \
    --trust-remote-code
```

服务启动成功后, 运行请求脚本：
```python
import openai
client = openai.Client(
    base_url="http://localhost:30000/v1", api_key="EMPTY")

response = client.chat.completions.create(
    model="default",
    messages= [
        {"role": "user", "content": "Write a short summary of the benefits of regular exercise"},
    ],
    temperature=0.7,
    max_tokens=4096,
    extra_body={"top_p": 0.8, "top_k": 20}
)
print(response)
```

Citing HY-MT1.5:

```bibtex
@misc{hy-mt1.5,
      title={HY-MT1.5 Technical Report}, 
      author={Mao Zheng and Zheng Li and Tao Chen and Mingyang Song and Di Wang},
      year={2025},
      eprint={2512.24092},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2512.24092}, 
}
```

## 联系我们
如果你想给我们的研发和产品团队留言，欢迎联系我们腾讯混元LLM团队。你可以通过邮件（hunyuan_opensource@tencent.com）联系我们。
