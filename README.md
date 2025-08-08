<div id="toc" align="center" style="margin-bottom: 0;">
  <ul style="list-style: none; margin: 0; padding: 0;">
    <a href="https://stagehand.dev">
      <picture>
        <source media="(prefers-color-scheme: dark)" srcset="media/dark_logo.png" />
        <img alt="Stagehand" src="media/light_logo.png" width="200" style="margin-right: 30px;" />
      </picture>
    </a>
  </ul>
</div>
<p align="center">
  <strong>The AI Browser Automation Framework</strong><br>
  <a href="https://docs.stagehand.dev">Read the Docs</a>
</p>

<p align="center">
  <a href="https://github.com/browserbase/stagehand/tree/main?tab=MIT-1-ov-file#MIT-1-ov-file">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="media/dark_license.svg" />
      <img alt="MIT License" src="media/light_license.svg" />
    </picture>
  </a>
  <a href="https://join.slack.com/t/stagehand-dev/shared_invite/zt-38khc8iv5-T2acb50_0OILUaX7lxeBOg">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="media/dark_slack.svg" />
      <img alt="Slack Community" src="media/light_slack.svg" />
    </picture>
  </a>
</p>

<p align="center">
	<a href="https://trendshift.io/repositories/12122" target="_blank"><img src="https://trendshift.io/api/badge/repositories/12122" alt="browserbase%2Fstagehand | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>
</p>

<p align="center">
If you're looking for the Python implementation, you can find it 
<a href="https://github.com/browserbase/stagehand-python"> here</a>
</p>

<div align="center" style="display: flex; align-items: center; justify-content: center; gap: 4px; margin-bottom: 0;">
  <b>Vibe code</b>
  <span style="font-size: 1.05em;"> Stagehand with </span>
  <a href="https://director.ai" style="display: flex; align-items: center;">
    <span>Director</span>
  </a>
  <span> </span>
  <picture>
    <img alt="Director" src="media/director_icon.svg" width="25" />
  </picture>
</div>

## 为什么选择 Stagehand？

现有的大多数浏览器自动化工具要么要求您在 Selenium、Playwright 或 Puppeteer 等框架中编写底层代码，要么使用在生产环境中可能不可预测的高级代理。通过让开发者自主选择何时编写代码或自然语言指令，Stagehand 成为生产环境浏览器自动化的理想选择。

1. **自由选择编码或自然语言**：面对陌生页面时使用 AI 导航，明确需求时直接编写代码（通过 [Playwright](https://playwright.dev/) 实现）。

2. **预览与缓存操作**：Stagehand 允许在执行前预览 AI 生成的操作，并可轻松缓存可重复操作以节省时间和 token 消耗。

3. **一行代码集成先进模型**：只需一行代码即可将 OpenAI 和 Anthropic 的最新型号整合至浏览器环境。

## 示例

以下演示如何使用 Stagehand 构建浏览器自动化示例：

<div align="center">
  <div style="max-width:300px;">
    <img src="/media/github_demo.gif" alt="See Stagehand in Action">
  </div>
</div>

```typescript
// Use Playwright functions on the page object
const page = stagehand.page;
await page.goto("https://github.com/browserbase");

// Use act() to execute individual actions
await page.act("click on the stagehand repo");

// Use Computer Use agents for larger actions
const agent = stagehand.agent({
    provider: "openai",
    model: "computer-use-preview",
});
await agent.execute("Get to the latest PR");

// Use extract() to read data from the page
const { author, title } = await page.extract({
  instruction: "extract the author and title of the PR",
  schema: z.object({
    author: z.string().describe("The username of the PR author"),
    title: z.string().describe("The title of the PR"),
  }),
});
```

## 文档

访问 [docs.stagehand.dev](https://docs.stagehand.dev) 查看完整文档。

## 快速开始

通过一行代码开始使用 Stagehand，或查阅我们的[快速入门指南](https://docs.stagehand.dev/get_started/quickstart)获取更多信息：

```bash
npx create-browser-app
```

<div align="center">
    <a href="https://www.loom.com/share/f5107f86d8c94fa0a8b4b1e89740f7a7">
      <p>Watch Anirudh demo create-browser-app to create a Stagehand project!</p>
    </a>
    <a href="https://www.loom.com/share/f5107f86d8c94fa0a8b4b1e89740f7a7">
      <img style="max-width:300px;" src="https://cdn.loom.com/sessions/thumbnails/f5107f86d8c94fa0a8b4b1e89740f7a7-ec3f428b6775ceeb-full-play.gif">
    </a>
  </div>

### 从源码构建运行

```bash
git clone https://github.com/browserbase/stagehand.git
cd stagehand
pnpm install
pnpm playwright install
pnpm run build
pnpm run example # run the blank script at ./examples/example.ts
pnpm run example 2048 # run the 2048 example at ./examples/2048.ts
```

当您拥有 LLM 供应商的 API 密钥和 Browserbase 凭证时，Stagehand 能发挥最佳性能。运行以下命令将这些配置加入项目：

```bash
cp .env.example .env
nano .env # Edit the .env file to add API keys
```

## 参与贡献

> [!NOTE]  
> 我们非常重视对 Stagehand 的贡献！如有问题或需要支持，请加入我们的 [Slack 社区](https://join.slack.com/t/stagehand-dev/shared_invite/zt-38khc8iv5-T2acb50_0OILUaX7lxeBOg)。

总体而言，我们按优先级顺序专注于提升可靠性、速度和成本效益。如果您有意贡献代码，我们强烈建议在开始前通过 [Slack 社区](https://join.slack.com/t/stagehand-dev/shared_invite/zt-38khc8iv5-T2acb50_0OILUaX7lxeBOg)联系 [Miguel Gonzalez](https://x.com/miguel_gonzf) 或 [Paul Klein](https://x.com/pk_iv)，以确保您的贡献符合我们的目标。

更多信息请参阅我们的 [贡献指南](https://docs.stagehand.dev/examples/contributing)。

## 致谢

本项目深度依赖 [Playwright](https://playwright.dev/) 作为自动化网页操作的可靠基础。同时，我们也受益于 [tarsier](https://github.com/reworkd/tarsier)、[gemini-zod](https://github.com/jbeoris/gemini-zod) 和 [fuji-web](https://github.com/normal-computing/fuji-web) 的优秀技术与发现。

我们要感谢以下人员对 Stagehand 的重大贡献：

- [Paul Klein](https://github.com/pkiv)
- [Anirudh Kamath](https://github.com/kamath)  
- [Sean McGuire](https://github.com/seanmcguire12)  
- [Miguel Gonzalez](https://github.com/miguelg719)  
- [Sameel Arif](https://github.com/sameelarif)  
- [Filip Michalsky](https://github.com/filip-michalsky)  
- [Jeremy Press](https://x.com/jeremypress)  
- [Navid Pour](https://github.com/navidpour)

## 许可协议

基于 MIT 许可证授权。

版权所有 © 2025 Browserbase, Inc.