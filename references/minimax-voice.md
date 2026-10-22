# MiniMax 音色复刻与语音生成

仅在用户选择 MiniMax 配音时读取。此流程只生成旁白音频；画面仍由代码制作。平台套餐、模型、价格和接口可能变化，实际调用前核对当时的官方页面和当前账户，不把“Coding Plan 支持语音生成”推断为“音色复刻免费”。

## 调用前核对

1. 区分当前账号的 Coding/Token/M Plan **订阅 Key** 与普通**按量计费 API Key**。查询当前套餐的语音能力、剩余额度、复刻音色的单独费用及超额扣费路径；不得静默切换到按量 Key 或购买积分。官方 [套餐说明](https://platform.minimax.cn/docs/m-plan/faq)、[定价](https://platform.minimax.cn/docs/pricing/overview) 与账号用量页为准。
2. 音色复刻需要账户认证，并且只能使用用户本人或已明确授权的声音。检查用户指定的样本、用途和授权范围；未提供样本或授权不清时停在准备步骤，不从旧视频、网络采访或聊天语音中自行提取。样本上传属于将个人声音交给第三方，按当次用户授权执行；敏感原音频不写入交付包或公开仓库。
3. 检查当前区域、接口、模型和音频规范。国内账号按国内官方文档接入，不猜测不同区域的域名与 Key 是否通用。Key 仅在运行时从安全凭据来源读取，不以明文写入本 Skill 的任何文件，也不打印或写入命令、源码、日志、交付物。

## 音频制作

官方流程是：[上传复刻音频](https://platform.minimax.cn/docs/api-reference/voice-cloning-uploadcloneaudio)取得 `file_id` → [快速复刻](https://platform.minimax.cn/docs/api-reference/voice-cloning-clone)取得 `voice_id` → 用该音色进行[同步语音合成](https://platform.minimax.cn/docs/api-reference/speech-t2a-http)或[异步长文本合成](https://platform.minimax.cn/docs/api-reference/speech-t2a-async-create)。按当前[音色复刻指南](https://platform.minimax.cn/docs/guides/speech-voice-clone)核对样本时长、格式和大小。不要把复刻预览当成已经生成整支视频的最终旁白。

先用已确认逐字稿的一小段试听，覆盖情绪开场、DeepInfer 等中英混读术语及普通解释句。比较相似度、自然度、情绪、断句和发音；必要时只调整语速、停顿、发音词典或换模型，不暗改已确认稿。用户认可音色后再生成全稿。长稿分段生成时检查音色、响度、语速和段落衔接，保存最终音频及非敏感的模型/音色 ID/参数记录。按实际音频重新测时长并对齐字幕和镜头；API 自带字幕也要抽查，不能直接视作精确同步。
