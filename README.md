# CLA Weather Skill

使用高德地图天气 API 查询指定地区的实况天气和天气预报的 Claude Code 技能。

## 功能

- 查询指定城市的实况天气（温度、湿度、风向、风力等）
- 查询未来 4 天的天气预报
- 支持中文城市名或县区名称查询
- 自动 API Key 管理

## 安装

### 方式一：克隆仓库

```bash
cd ~/.claude/skills
git clone https://github.com/opscolin/skill-weather.git
mv skill-weather/weather .
rm -rf skill-weather
```

### 方式二：下载 .skill 文件

1. 下载 `weather.skill` 文件
2. 解压到 `~/.claude/skills/` 目录：

```bash
unzip weather.skill -d ~/.claude/skills/
```

## 使用

首次使用需要配置高德地图 API Key。

### 获取 API Key

1. 访问 [高德开放平台](https://console.amap.com/)
2. 登录/注册账号
3. 创建应用并获取 Web 服务 API Key

### 配置 API Key

有以下三种方式配置 API Key（优先级从高到低）：

1. **命令行参数**（推荐测试使用）
```bash
python ~/.claude/skills/weather/scripts/weather_query.py "北京" --api-key YOUR_API_KEY
```

2. **环境变量**
```bash
export AMAP_API_KEY=YOUR_API_KEY
```

3. **自动保存到文件**
首次运行时，脚本会提示输入 API Key 并自动保存到 `~/.claude/skills/weather/api_key.txt`

### 查询天气

```bash
# 查询实况天气
python ~/.claude/skills/weather/scripts/weather_query.py "北京"

# 查询天气预报（未来4天）
python ~/.claude/skills/weather/scripts/weather_query.py "北京" all

# 查询区县天气
python ~/.claude/skills/weather/scripts/weather_query.py "朝阳区"
```

## 输出示例

```
📍 北京市
🌡️  温度: 19℃
💧 湿度: 23%
🌬️  风向: 南
💨 风力: ≤3
☁️  天气: 阴
⏰ 更新时间: 2026-03-27 17:38:13
```

## API 说明

该技能使用高德地图开放平台的以下 API：

- **地区查询 API**: `https://restapi.amap.com/v3/config/district`
- **天气查询 API**: `https://restapi.amap.com/v3/weather/weatherInfo`

详细文档请参考 [高德开放平台](https://lbs.amap.com/api/webservice/summary)

## 许可证

MIT License
