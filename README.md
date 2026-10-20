# Qwen Image Local — Skill 发布测试

这是一个用于验证 GitHub Skill 发布流程的小型项目，包含一个本地 Qwen 图像生成 Skill 和 PowerShell 参数包装脚本。

## 当前状态

- 已整理为可分发的 Skill 目录，去除原始安装中的个人电脑配置和历史偏好。
- 不包含模型、运行程序、密钥或用户图片。
- 实际图像生成尚未验证；本项目不承诺特定模型与运行时版本可直接配合使用。
- 适合 Windows PowerShell 环境；其他系统需要自行适配。

## 安装到 Codex

将 `skills/qwen-image-local` 整个文件夹复制到你自己的 Codex 用户技能目录（通常是 `~/.codex/skills/`），重新打开 Codex 后检查是否发现该技能。

示例请求：

> 使用 $qwen-image-local 检查我本地的 Qwen 图像生成环境。先检查缺少的组件，不下载模型，不执行推理。

## 目录

```text
skills/qwen-image-local/
  SKILL.md
  scripts/generate.ps1
```

## 手动检查参数

先安装兼容的 stable-diffusion.cpp 运行时与模型组件，再把下面的示例路径替换成你的实际路径。输出文件夹必须已经存在。

```powershell
& ./skills/qwen-image-local/scripts/generate.ps1 `
  -Executable 'D:\AI\sd-cli.exe' `
  -Denoiser 'D:\AI\models\denoiser.gguf' `
  -Encoder 'D:\AI\models\encoder.gguf' `
  -Vae 'D:\AI\models\vae.safetensors' `
  -Prompt 'A quiet garden in morning light' `
  -Output 'D:\AI\outputs\test.png' `
  -DryRun
```

`DryRun` 只验证路径并打印参数，不加载模型或生成图片。现有文件、路径或输出目录不满足要求时会报错。

本仓库未附加开源许可证；公开可见不代表授予任意再分发授权。模型与运行时的许可证请分别查看其来源仓库。
