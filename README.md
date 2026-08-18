# StardewValley-zijiCP

星露谷物语 **Content Patcher 自制模组**（`[CP] NewRecipes by CyberZ`，v1.0.3）。

一个综合型 CP 改造模组：新增料理与两类大型加工机器，并对商店、博物馆/怪物杀手奖励、书籍功效、各类机器、动物产物、垃圾桶、鱼塘与雕像 Buff 等做了大量平衡性调整。中文注释已随各 JSON 数据文件内置。

---

## 功能总览（标注）

### 1. 新增料理与物品（`Data/Objects.json`）
- 新增菜品 **魔法姜茶（Migic Ginger）**：饮用后获得 +5 攻击、+1 运气、+0.8 移速 Buff，售价 750g。
- 新增/修改大量物品价格与品质，例如调整工匠品、鱼获售价；为 `seedmaker` 禁用种子袋等。

### 2. 新增大型机器（`Data/keg.json`、`Data/jar.json`）
- **超级酒桶（Double Keg）**：大型小桶，可同时处理小麦/啤酒花/茶叶/咖啡豆/蜂蜜/米，成品按原物品品质 1.25x / 1.5x / 2x 增产。
- **长罐头瓶（Long Jar）**：大型罐头瓶，可同时腌制多份蔬菜/水果，鲟鱼鱼籽可批量产出，品质加成更高。

### 3. 机器改造（`Data/Machines.json`）
- **再生机**：可回收 3 种海藻 → 随机种子 / 腐烂植物；可回收腐烂植物 → 虫肉/纤维/苔藓；可回收自动抚摸机 → 兔子脚（随机品质）。
- **碎骨机**：只能加工骨头碎片，产量+时间调整（不可放古物）。
- **熔炉 / 重型熔炉**：产出固定数量、放射性矿熔炼变慢、不可用仙尘。
- **织布机 / 油压机 / 蛋黄酱机 / 脱水机 / 诱饵制作机**：品质相关产量加成，且受自定义书籍 `_Book_Milk` 触发双倍。

### 4. 商店改造（`Data/shops/`）
- `Shops.json`：火山商店/浣熊/冒险家/沙漠节/矮人/旅行商人/桑迪/岛屿交易/赌场新增或调整商品（骨架卷轴随机按天出售、自动抚摸机 7w、离子炉心 5w 等）。
- `Prices.json`：全商店统一价格修正——各店主好感度 1500/2250 后价格从 1.5x 降到 1.0x，Joja 会员价差。
- `PierreFixes.json`：杂货店（皮埃尔）取消价格加成并新增大量种子/配方商品。
- `Limited.json`：杂货店种子等限购库存调整。
- `CasinoMore.json`：赌场新增英雄奖杯、汽水机及若干家具/挂画。

### 5. 博物馆与怪物杀手奖励（`Data/MonsterSlayerQuests.json`）
- 调整怪物杀手任务计数（沙尘精灵 300、史莱姆 750 等）与瀑布式奖励（大奖券、精灵石、本模组书籍）。
- 重写博物馆各阶段奖励（15/35/45/…/85 及矿物 3 种），发放矿石熔炼所需书籍与设备。

### 6. 书籍与能力（`Data/book/`）
- `Books.json`：新增 8 本可阅读书籍（鱼王养殖、远古奥秘、现代采矿、齐先生的笔记本、金色椰子、平衡的运气、动物制品工艺学、豪华自助餐）。
- `Powers.json`：为上述书籍解锁对应被动能力（效果见 i18n 中文描述）。
- `BookEffects.json`：书籍效果落地——书籍商人交换、远古斑点掉宝、矿石熔炼 (IridiumOre)、鱼王抓捕邮件、鱼塘产卵强化、金色椰子、运气/速度/森林魔法/钓鱼 Buff、巨大作物解锁、雕像/祝福 Buff 持久化与垃圾桶好物等。

### 7. 动物与鱼塘（`Data/Objects.json` 内联）
- 鸭 1 天、兔/恐龍 2 天、鸵鸟 3 天即产一次；鱼塘建材改为石 200/海藻 50/铜矿 10。

### 8. 地图开门时间（`Data/Objects.json` 内联）
- 铁匠铺、Joja 超市、沙漠沙之家等 LockedDoorWarp 开放时段调整。

---

## 目录结构（注释）

```
zijiCP/
├── manifest.json            # SMAPI 识别文件（名称/作者/版本/UniqueID/Nexus）
├── content.json             # 主入口：Include 各数据文件 + 加载贴图 + 冬季雪地覆盖
├── 介绍.txt                 # 作者自述：配方、机器、垃圾桶改动说明
├── Data/
│   ├── Objects.json         # 新增料理/物品 + 商店开门时间 + 动物/鱼塘生产
│   ├── Machines.json        # 各类机器产出规则改造
│   ├── keg.json             # 超级酒桶（新大型机器）
│   ├── jar.json             # 长罐头瓶（新大型机器）
│   ├── MonsterSlayerQuests.json  # 怪物杀手 + 博物馆奖励
│   ├── book/                # 书籍对象、能力、效果
│   │   ├── Books.json
│   │   ├── Powers.json
│   │   └── BookEffects.json
│   └── shops/               # 各商店规则
│       ├── Shops.json       # 商店货品增改
│       ├── Prices.json      # 价格/好感度折扣
│       ├── PierreFixes.json # 杂货店修复
│       ├── Limited.json     # 限购库存
│       └── CasinoMore.json  # 赌场内容
├── assets/                  # 自定义贴图（饮品、大件、书、雪地版）
└── i18n/                    # 多语言文本（zh.json / default.json）
```

---

## 安装

1. 安装 [SMAPI](https://smapi.io/) 与 [Content Patcher](https://www.nexusmods.com/stardewvalley/mods/1915)。
2. 将整个 `zijiCP` 文件夹放入 `星露谷物语/Mods/`。
3. 启动游戏时在 SMAPI 控制台确认 `[CP] NewRecipes by CyberZ` 正常加载。

> 依赖依赖项：SMAPI ≥ 4.0.0，Content Patcher（Format 2.7.2）。