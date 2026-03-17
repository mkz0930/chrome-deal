# chrome-deal

通过 WebSocket Relay Server 控制 Windows Chrome 浏览器的 OpenClaw Skill。

## 架构

```
Agent (WSL/Linux) → Relay Server (:19000) → Chrome 插件 → Windows Chrome
```

## 功能

- 打开网页 / 新建标签页 / 切换标签页
- 点击（CSS选择器 / 文字 / 坐标）
- 输入文字
- 滚动页面
- 截图
- 执行 JavaScript
- Cookie 管理
- 文件下载
- 通用登录
- 反爬模拟（随机滚动、延迟）

## 快速使用

```python
from chrome_deal import ChromeDeal

async def main():
    c = ChromeDeal()
    
    # 打开网页
    r = await c.open("https://www.amazon.com/s?k=cup")
    
    # 截图
    r = await c.screenshot()
    
    # 点击
    await c.click_text("全选")
    
    # 输入
    await c.type_text("#search", "light")
    
    # 滚动
    await c.human_scroll(pages=3)
```

## CLI 测试

```bash
python3 chrome_deal.py https://www.amazon.com
```

## 前置条件

1. Relay Server 运行中（端口 19000）
2. Chrome 插件已加载并连接

详见 [SKILL.md](SKILL.md)

## License

MIT
