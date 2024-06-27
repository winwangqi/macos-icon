# Icon Processing Script

该脚本可以处理图片文件或应用程序的图标文件，支持以下功能：
1. 读取应用程序的 ICNS 文件并解压缩。
2. 从解压缩的图标文件中找到最佳质量的 PNG 图像。
3. 对 PNG 图像进行处理，包括调整尺寸、添加圆角、内边距和阴影。
4. 将处理后的 PNG 图像重新打包成 ICNS 文件。
5. 保存原始的解压缩图标文件。
6. 将处理后的 PNG 图像和新的 ICNS 文件输出到指定目录。

## 功能概述

- **处理图片文件**：直接对输入的 PNG 图片文件进行处理。
- **处理应用程序图标**：读取应用程序包中的 ICNS 文件，解压缩并找到最佳质量的图标进行处理。

## 使用方法

1. **确保系统中已安装 ImageMagick 和 sips 工具**

   你可以使用 Homebrew 安装 ImageMagick：
   ```bash
   brew install imagemagick
   ```

2. **保存脚本并赋予执行权限**

   将脚本保存为 `icon` 并赋予执行权限：
   ```bash
   chmod +x icon
   ```

3. **运行脚本**

   - **处理图片文件**：
     ```bash
     ./icon /path/to/your/image.png
     ```
     该命令会对提供的 PNG 图片文件进行处理，并生成新的 ICNS 文件和处理后的 PNG 文件。

   - **处理应用程序图标**：
     ```bash
     ./icon /path/to/your/app.app
     ```
     该命令会读取应用程序包中的 ICNS 文件，解压缩并找到最佳质量的图标进行处理，并生成新的 ICNS 文件和处理后的 PNG 文件，同时保留解压缩后的原始图标。

## 处理步骤

- **调整图像尺寸为 1024x1024**：
  使用 `magick` 命令调整图像尺寸。

- **添加圆角**：
  使用 `magick` 命令添加圆角，圆角大小为 180 像素。

- **添加内边距**：
  使用 `magick` 命令添加内边距，内边距大小为 84 像素。

- **添加阴影**：
  使用 `magick` 命令添加阴影。

- **创建 ICNS 文件**：
  使用 `sips` 和 `iconutil` 命令将处理后的 PNG 图像打包成 ICNS 文件。

## 输出

所有处理结果会输出到 `output` 目录中，包括：
- 处理后的 PNG 图像 (`processed_icon.png`)
- 新生成的 ICNS 文件 (`icon.icns`)
- 解压缩后的原始图标文件（保存在 `output/original_icons` 目录中）

## 例子

- **处理图片文件**：
  ```bash
  ./icon /path/to/your/image.png
  ```

- **处理应用程序图标**：
  ```bash
  ./icon /path/to/your/app.app
  ```

## 注意事项

- 确保系统中已安装 ImageMagick 和 sips 工具。
- 运行脚本时提供有效的图片文件或应用程序路径。