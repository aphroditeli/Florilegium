# 花瓣照片贴图（CC0）

把图库照片放进本目录，**同名即生效**，无需改代码：

## 命名规则

| 文件名 | 作用 |
| --- | --- |
| `<物种id>.jpg` | 物种级花瓣照片（所有花色共用，材质保留品种色轻着色） |
| `<物种id>_<花色id>.jpg` | 品种级照片，优先级更高（如 `rosa_hybrida_red.jpg`） |

## 行为

- 贴图存在：花瓣材质自动改用照片作为 albedo 贴图（真实纹理层次 + 品种色轻着色）。
- 贴图缺失：保持程序化纯色材质，应用不报错。
- 建议：花瓣占比大、顺光、纹理清晰的照片；1024px 左右即可，≤ 500KB。

## 推荐来源（CC0 / 免费商用，无需署名）

- **Pixnio**（pixnio.com）：国际 CC0 图库，花卉高清照片量大
- **GAHAG**（gahag.net）：日本 CC0 素材库
- **Photock**（photock.jp）：日本免费商用高清图库

批量下载：把照片直链填进 `scripts/texture-sources.json`，运行 `node scripts/fetch-textures.mjs`。
