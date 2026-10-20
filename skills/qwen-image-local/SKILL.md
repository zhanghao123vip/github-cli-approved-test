---
name: qwen-image-local
description: Configure or run local AtomicChat Qwen-Image-2.1-Turbo GGUF text-to-image generation with stable-diffusion.cpp and the bundled PowerShell wrapper.
---

# Qwen Image Local

This skill packages instructions and a PowerShell wrapper only. It does not include model weights or an inference runtime. Do not claim image generation is ready until the installed components and an actual generation have been verified.

## Check components

Locate or configure the following components, verifying current filenames, compatibility and license terms at their original repositories:

- Modified encoder: https://huggingface.co/AtomicChat/Qwen-Image-2.1-Turbo-Uncensored-GGUF
- Turbo denoiser: https://huggingface.co/AtomicChat/Qwen-Image-2.1-Turbo-GGUF
- VAE: https://huggingface.co/Comfy-Org/Qwen-Image-2.1
- Runtime: https://github.com/leejet/stable-diffusion.cpp

Check the runtime help for Qwen Image 2.1 support and supported offloading flags. Check the target machine's RAM and VRAM rather than assuming the pipeline fits. Ask before large model downloads unless already authorized.

## Generate

Use `scripts/generate.ps1` with absolute paths for `Executable`, `Denoiser`, `Encoder`, `Vae` and `Output`, plus a `Prompt`. The output must be a new PNG inside an existing directory.

`DryRun` validates paths and prints arguments without running inference; it still requires existing component files. Use it to inspect the bundled eight-step Turbo schedule. Supply `ExtraArgs` only for options verified against the installed executable. This wrapper supports text-to-image only.

Run actual inference only after compatibility checks. Inspect the resulting image and report its actual output path. If the runtime, weights or memory are insufficient, report the concrete missing component or error. A successful dry run does not establish successful generation.

## Distribution

Model weights and the runtime are separate dependencies with their own licenses. Verify those terms before downloading or redistributing them. Do not include credentials, local machine paths or private inputs in shared examples.
