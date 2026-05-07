<p align="center">
<a href="README.md"><img src="https://img.shields.io/badge/Lang-English-blue?style=for-the-badge" alt="English"></a>
</p>

<h1 align="center">厨神.skill</h1>

<p align="center">
Agent真能用得上的家常菜谱，内涵2988种美食（95%以上为中餐）<br>
2988个真实菜谱，非AI生成
</p>

<p align="center">
<img src="assets/chef-animation_cn.gif" alt="演示动画" width="960">
</p>

---

## 安装

### 方式 1：通过 npx（推荐）

```bash
npx skills add yummy-chat/masterchef-skill
```

### 方式 2：通过 SkillHub（供 Agent 使用）

```bash
# 检查是否已安装 SkillHub
skillhub --version

# 若未安装，请先安装 SkillHub CLI（仅 CLI，无 GUI）
curl -fsSL https://skillhub.cn/install/skillhub.md | bash

# 然后安装 masterchef 技能
skillhub install masterchef
```

---

## API 接口

本 skill 提供两个原子 API 能力，Agent 可直接调用进行编排和集成。

### 1. 食材搜索

**POST** `https://api.yummy.chat/ingredients`

传入 1-3 个食材，返回可制作的菜品列表。

```bash
curl -s -X POST https://api.yummy.chat/ingredients \
  -H "Content-Type: application/json" \
  -d '{"ingredients": ["茄子", "土豆"]}'
```

**返回：**
```json
{
  "results": [
    { "ingredient": "茄子", "dishes": ["地三鲜", "油焖茄子", "凉拌茄子"] },
    { "ingredient": "土豆", "dishes": ["地三鲜", "土豆炖牛肉", "酸辣土豆丝"] }
  ]
}
```

### 2. 菜谱查询

**POST** `https://api.yummy.chat/howtocook`

传入菜名，返回完整菜谱（食材、步骤、小贴士）。

```bash
curl -s -X POST https://api.yummy.chat/howtocook \
  -H "Content-Type: application/json" \
  -d '{"dish_name": "地三鲜"}'
```

**返回：**
```json
{
  "dish_name": "地三鲜",
  "recipes": ["地三鲜\n所属菜系：东北菜\n烹饪难度：⭐⭐⭐\n\n食材与调味品\n..."]
}
```

---

## 使用示例

### 示例 1：菜谱查询

**你：** 地三鲜怎么做？

**厨神：**
```
# 地三鲜
所属菜系：东北菜
烹饪难度：⭐⭐⭐

## 食材与调味品
🍆 茄子 2根（约400g，切滚刀块）
🥔 土豆 2个（约300g，切滚刀块）
🫑 青椒 2个（约150g，切块）
🧄 大蒜 4瓣（切末）
🧅 葱 1根（切段）
🫗 食用油 适量
💧 生抽 2勺
🍶 老抽 1勺
🦪 蚝油 1勺
🍬 白糖 1茶勺
🧂 盐 适量
💧 水淀粉 适量

## 制作步骤
1. 茄子、土豆切滚刀块，青椒切块，大蒜切末，葱切段备用
2. 锅中倒油烧至七成热，下土豆块炸至金黄捞出
3. 下茄子块炸至软烂捞出沥油
4. 锅留底油，爆香蒜末和葱段
5. 倒入炸好的土豆和茄子，加生抽、老抽、蚝油、白糖翻炒
6. 加入青椒块，淋入水淀粉勾芡，翻炒均匀即可出锅

## 健康建议
油炸食材热量较高，减脂期可改用少油煎或蒸的方式。
```

---

### 示例 2：食材搜索

**你：** 我有茄子和土豆，能做什么？

**厨神：**
```
根据你的食材，可以做这些菜：

🍆 茄子相关：
  • 地三鲜 ⭐ 推荐（同时用到茄子和土豆）
  • 油焖茄子
  • 凉拌茄子
  • 茄子煎饼

🥔 土豆相关：
  • 地三鲜 ⭐ 推荐（同时用到茄子和土豆）
  • 土豆炖牛肉
  • 酸辣土豆丝
  • 土豆泥

💡 特别推荐「地三鲜」，正好用上你的两种食材！
```

---

## 晒出你的作品 📸

跟着菜谱做了一道好菜？欢迎上传你的美食照片！

将照片以 `{菜谱ID}_{美式拼写名称}.png` 命名，放入 `recipe_photo/` 目录，然后提交 Pull Request 即可。

**命名示例：**
```
recipe_photo/
├── 2367_liangban-qiezi.png       # 凉拌茄子
├── 973_dan-chao-fan.png          # 蛋炒饭
└── 1203_italian-lemon-chicken.png # 意式柠檬鸡排
```

菜谱 ID 对应 `recipe/` 目录中的文件名前缀。

---

<p align="center">
Made with ❤️ by recipe@yummy.chat
</p>
