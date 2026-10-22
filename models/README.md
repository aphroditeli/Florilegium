# 花材真模型目录（GLB）

把下载好的 GLB 模型放进本目录，**同名即生效**，无需改代码：

## 命名规则

| 文件名 | 作用 |
| --- | --- |
| `<物种id>.glb` | 该物种所有花色共用（如 `rosa_hybrida.glb`） |
| `<物种id>.<花色id>.glb` | 品种级模型，优先级更高（如 `rosa_hybrida.pink.glb`） |

每个物种 JSON 的 `3d.model_url` 字段已指向本目录约定文件；也可以把它改成任何
https 远程地址（摄影测量托管链接等），加载器同样支持。

## 批量拉取（Meshy / 任何直链）

```bash
node scripts/fetch-models.mjs --check   # 看当前 20 种花材的模型状态
node scripts/fetch-models.mjs           # 按 scripts/model-sources.json 的直链批量下载
```

把各物种的 GLB 直链填进 `scripts/model-sources.json`（Meshy 画廊登录后可复制 CC0
模型的下载直链；Pixabay 3D、Sketchfab CC0 等任何来源的 .glb 直链均可），脚本会下载
到本目录、校验 GLB 二进制头并打印 20 种花材的覆盖报告。本地已手动下载的文件直接按
命名规则放进本目录即可，不必走脚本。

## 行为

- 模型加载成功：自动替换程序化花头，按物种的**真实花径**（植物学数据）自动缩放对齐。
- 模型缺失/加载失败：继续使用程序化花头（杯形曲面版本），应用不报错。
- 模型应是 **Y 轴向上、只含花头**（不要含长茎——茎由引擎按真实茎长/弯曲生成）。
- 复杂模型建议 ≤ 5 万面；同一模型多支花共用缓存。

## 推荐来源（CC0 / 免费商用）

- **Meshy**（meshy.com）：14,800+ 免费 CC0 花卉模型，直接提供 GLB，可商用无需署名
- **Pixabay 3D**（pixabay.com/3d）：免费 GLB 花卉
- Sketchfab / CGTrader / TurboSquid：注意逐个确认商业授权条款

## 花瓣贴图（可选，用于材质增强）

Pixnio / GAHAG / Photock 提供 CC0 高清花卉照片，可作花瓣颜色/法线贴图来源。
放到 `public/textures/petals/`（规则见该目录 README），或用
`node scripts/fetch-textures.mjs` 批量拉取。
