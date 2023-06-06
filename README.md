# [灵心（SoulChat）]((https://github.com/scutcyr/SoulChat))
<p align="center">
    <img src="./ProactiveHealthGPT.png" width=900px/>
</p>
<p align="center">
    <a href="./LICENSE"><img src="https://img.shields.io/badge/license-Apache%202-red.svg"></a>
    <a href="support os"><img src="https://img.shields.io/badge/os-linux%2C%20win%2C%20mac-pink.svg"></a>
    <a href=""><img src="https://img.shields.io/badge/python-3.8+-aff.svg"></a>
    <a href="https://github.com/scutcyr/SoulChat/graphs/contributors"><img src="https://img.shields.io/github/contributors/scutcyr/SoulChat?color=9ea"></a>
    <a href="https://github.com/scutcyr/SoulChat/commits"><img src="https://img.shields.io/github/commit-activity/m/scutcyr/SoulChat?color=3af"></a>
    <a href="https://github.com/scutcyr/SoulChat/issues"><img src="https://img.shields.io/github/issues/scutcyr/SoulChat?color=9cc"></a>
    <a href="https://github.com/scutcyr/SoulChat/stargazers"><img src="https://img.shields.io/github/stars/scutcyr/SoulChat?color=ccf"></a>
</p>

基于主动健康的主动性、预防性、精确性、个性化、共建共享、自律性六大特征，华工未来技术学院-广东省数字孪生人重点实验室开源了中文领域生活空间主动健康大模型基座ProactiveHealthGPT，包括：
* 经过千万规模中文健康对话数据指令微调的[生活空间健康大模型扁鹊（BianQue）](https://github.com/scutcyr/BianQue)    
* 经过百万规模心理咨询领域中文长文本指令与多轮共情对话数据联合指令微调的[心理健康大模型灵心（SoulChat）](https://github.com/scutcyr/SoulChat)   

我们期望，**生活空间主动健康大模型基座ProactiveHealthGPT** 可以帮助学术界加速大模型在慢性病、心理咨询等主动健康领域的研究与应用。本项目为 **生活空间健康大模型扁鹊（BianQue）** 。


## 最近更新
- 👏🏻  2023.06.06: 【预告】扁鹊-2.0模型即将开源。
- 👏🏻  2023.06.06: 灵心SoulChat模型即将开源，详情见：[灵心健康大模型SoulChat：通过长文本咨询指令与多轮共情对话数据集的混合微调，提升大模型的“共情”能力 ](https://huggingface.co/scutcyr/SoulChat)。
- 👏🏻  2023.04.22: 基于扁鹊-1.0模型的医疗问答系统Demo，详情访问：[https://huggingface.co/spaces/scutcyr/BianQue](https://huggingface.co/spaces/scutcyr/BianQue)
- 👏🏻  2023.04.22: 扁鹊-1.0版本模型发布，详情见：[扁鹊-1.0：通过混合指令和多轮医生问询数据集的微调，提高医疗聊天模型的“问”能力（BianQue-1.0: Improving the "Question" Ability of Medical Chat Model through finetuning with Hybrid Instructions and Multi-turn Doctor QA Datasets）](https://huggingface.co/scutcyr/BianQue-1.0)


## 简介
   我们调研了当前常见的心理咨询平台，发现，用户寻求在线心理帮助时，通常需要进行较长篇幅地进行自我描述，然后提供帮助的心理咨询师同样地提供长篇幅的回复（见[figure/single_turn.png](./figure/single_turn.png)），缺失了一个渐进式的倾诉过程。但是，在实际的心理咨询过程当中，用户和心理咨询师之间会存在多轮次的沟通过程，在该过程当中，心理咨询师会引导用户进行倾诉，并且提供共情，例如：“非常棒”、“我理解你的感受”、“当然可以”等等（见下图）。
<p align="center">
    <img src="./figure/multi_turn.png" width=900px/>
</p>

   考虑到当前十分欠缺多轮共情对话数据集，我们一方面，构建了超过15万规模的 **单轮长文本心理咨询指令与答案（SoulChatCorpus-single_turn）** ，回答数量超过50万（指令数是当前的常见的心理咨询数据集 [PsyQA](PsyQA. https://github.com/thu-coai/PsyQA) 的6.7倍），并利用ChatGPT与GPT4，生成总共约100万轮次的 **多轮回答数据（SoulChatCorpus-multi_turn）** 。特别地，我们在预实验中发现，纯单轮长本文驱动的心理咨询模型会产生让用户感到厌烦的文本长度，而且不具备引导用户倾诉的能力，纯多轮心理咨询对话数据驱动的心理咨询模型则弱化了模型的建议能力，因此，我们混合SoulChatCorpus-single_turn和SoulChatCorpus-multi_turn构造成超过120万个样本的 **单轮与多轮混合的共情对话数据集SoulChatCorpus** 。所有数据采用“用户：xxx\n心理咨询师：xxx\n用户：xxx\n心理咨询师：”的形式统一为一种指令格式。

