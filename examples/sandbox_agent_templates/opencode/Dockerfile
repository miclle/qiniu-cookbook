# opencode CLI sandbox template
# 基于 agents-base 模板叠加 opencode CLI。
# 运行时通过 ANTHROPIC_API_KEY / OPENAI_API_KEY / GEMINI_API_KEY 等环境变量注入认证信息
#
# 使用 qshell 的 from_template + dockerfile 构建能力时，真实 base 来自
# qshell.sandbox.toml 中的 from_template；这里的 FROM 仅用于 Dockerfile 解析。
FROM scratch

# opencode CLI
# 说明：统一使用 @latest，保证每次 rebuild 拿到最新能力
RUN npm install -g opencode-ai@latest \
    && npm cache clean --force

# 默认工作目录：继承 agents-base / e2bdev/base 约定
WORKDIR /home/user

# 构建期简单验证（失败不阻断构建，仅做冒烟检查）
RUN opencode --version || true \
    && gh --version || true \
    && node --version \
    && python3 --version
