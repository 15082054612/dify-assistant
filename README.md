# Dify 助手应用（DSL）

这是从 [Dify](https://dify.ai) 导出的应用工作流 DSL 文件，用于对该应用的编排逻辑做版本管理。

## 文件说明

| 文件 | 说明 |
| --- | --- |
| `assistant.yml` | Dify 应用导出的 DSL，包含工作流编排、节点、变量与依赖插件声明 |

导出的关键元信息：

- `kind: app`，`version: 0.7.0`
- 应用名：助手
- 模式：`advanced-chat`
- 依赖插件：`langgenius/deepseek`、`langgenius/gaode`、`langgenius/openai`

## 如何导入到 Dify

1. 打开 Dify 控制台，进入「工作室 / 应用」。
2. 选择 **导入 DSL**，上传 `assistant.yml`。
3. 按提示安装缺失的插件（deepseek、高德地图、openai）。
4. 导入后重新填写各节点的 **API Key 与凭证**（导出文件不含密钥）。

## 如何更新这个仓库

每次在 Dify 中修改完工作流：

1. 在 Dify 里重新导出 DSL。
2. 用它覆盖本仓库的 `assistant.yml`。
3. 提交并推送：

   ```bash
   git add assistant.yml
   git commit -m "update workflow: <改动说明>"
   git push
   ```

这样每次改动都能通过 `git diff` 看清工作流具体变了哪些节点。

## 安全提示

DSL 导出文件可能包含明文的应用描述、节点提示词、模型参数以及已填写的 API Key。
仓库已设置为 **私有**，且 `.gitignore` 已忽略 `.env`、`secrets.yml` 等凭证文件。
推送前请再次确认文件内是否含有真实密钥；如果有，请先在 Dify 中改为使用环境变量引用。
