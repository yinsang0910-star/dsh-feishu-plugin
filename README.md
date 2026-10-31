# @yisang0910/plugin

DeepSeek Harness 设置面板里的「飞书连接」页：四步向导，把飞书接进 DSH。

**主仓库在 [yinsang0910-star/dsh-feishu](https://github.com/yinsang0910-star/dsh-feishu)**
——25 个 MCP 工具、长连接机器人、卡片网关都在那边。这个仓库只是为了能被插件目录收录，
由主仓库的 scripts/publish-plugin-repo.ps1 单向同步生成，**请勿直接在此提交代码**。

## 装

`ash
dsh plugin --profile <profile> add github:yinsang0910-star/dsh-feishu-plugin#<commit>
`

然后重启 DSH，设置面板左栏会出现「飞书连接」。

## 它做什么

- **建应用**：给开放平台直达链接和 11 项权限清单，可一键复制
- **填凭据**：可以扫码直接创建一个飞书自建应用（RFC 8628 设备授权），凭据只写本机、不经过浏览器；也可以手填
- **选会话**：扫描机器人所在的群并点选，不用手抄 32 位 chat_id
- **自检**：九项逐个真调飞书接口（凭据 / 机器人身份 / 会话列表 / 目标群 / 读历史 / 上传文件 / 云空间 / MCP 挂载 / 凭据文件），失败项直接给出该开通的 scope

自检不往聊天里发东西：读历史只读 1 条，上传探测文件只 20 字节且不发送。

## 依赖

需要 DSH 的 @deepseek-ai/dsh-client-ui-primitives 与 @deepseek-ai/dsh-client-ui-slots
（随 DSH 提供，不需要单独安装）。

## License

MIT