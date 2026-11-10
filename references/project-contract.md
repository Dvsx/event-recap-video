# 项目数据约定

以下是字段约定，可用JSON、YAML或Markdown表达，不要求特定解析库。

## brief

- event: 名称、主题、日期、地点；缺失可为空。
- audience、purpose、key_messages、call_to_action。
- video: ratio、resolution、fps、target_duration、audio_mode。
- brand: palette、logo_asset、fonts、logo_by_scene、safe_margins。
- music: asset、source_in、source_out、playback_rate、selection_reason。
- cover_targets: 用途、ratio、pixel_size、crop_evidence、safe_margins。
- constraints、confirmed_preferences、assumptions。

## asset-manifest

每项含 id、相对路径、类型、来源、尺寸/时长、用途标签、公开使用状态及依据。公开使用状态取 approved / restricted / unknown；用户提供只代表当前任务可用，不自动代表可放开源仓库。

## timeline

每个镜头含 id、start、end、assets、copy、intent、crop_focus、motion、transition、music_anchor、brand_visibility。时间以秒保存，并记输出帧。相邻镜头无非预期空隙或重叠，尾部与总时长一致。

## review

记录技术检查、关键帧检查、正常速度观看、音频听审、封面实际裁剪预览及其状态：passed / failed / not_checked。自动分析与人的主观反馈分开记。

## 推荐项目结构

```text
project/
  brief.md
  asset-manifest.json
  timeline.json
  music-selection.json
  MUSIC-CREDITS.md
  music-map.json
  assets/
  source/
  exports/
  review.md
```

路径相对项目根目录；不把某台机器的绝对路径写进可公开配置。仅创建实际使用的文件。工程实现由渲染工具管理，不重复维护两个互相矛盾的时间线。

音乐来源、许可和公开范围字段见 [BGM搜索规范](music-sourcing.md)，与music-map中的节拍数据分开。私人下载凭证和账号信息不放在公开清单中。
