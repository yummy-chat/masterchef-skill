<p align="center">
<a href="README.zh.md"><img src="https://img.shields.io/badge/Lang-中文-red?style=for-the-badge" alt="中文"></a>
</p>

<h1 align="center">masterchef.skill</h1>

<p align="center">
Practical home cooking recipes for AI Agents, featuring 2,988 dishes (95%+ Chinese cuisine)<br>
2,988 real recipes — not AI-generated
</p>

<p align="center">
<img src="assets/chef-animation.gif" alt="Demo animation" width="960">
</p>

---

## Installation

### Method 1: via npx (Recommended)

```bash
npx skills add yummy-chat/masterchef-skill
```

### Method 2: via SkillHub (for Agents)

**Check if SkillHub is installed:**
```bash
skillhub --version
```

**If not installed**, install SkillHub CLI first (CLI only, no GUI):
```bash
curl -fsSL https://skillhub.cn/install/skillhub.md | bash
```

**Then install masterchef skill:**
```bash
skillhub install masterchef
```

---

## API Reference

This skill exposes two atomic API capabilities. Agents can call them directly for orchestration and integration.

### 1. Ingredient Search

**POST** `https://api.yummy.chat/ingredients`

Given 1-3 ingredients, returns a list of matching dishes.

```bash
curl -s -X POST https://api.yummy.chat/ingredients \
  -H "Content-Type: application/json" \
  -d '{"ingredients": ["茄子", "土豆"]}'
```

**Response:**
```json
{
  "results": [
    { "ingredient": "茄子", "dishes": ["地三鲜", "油焖茄子", "凉拌茄子"] },
    { "ingredient": "土豆", "dishes": ["地三鲜", "土豆炖牛肉", "酸辣土豆丝"] }
  ]
}
```

### 2. Recipe Lookup

**POST** `https://api.yummy.chat/howtocook`

Given a dish name, returns the full recipe with ingredients, steps, and tips.

```bash
curl -s -X POST https://api.yummy.chat/howtocook \
  -H "Content-Type: application/json" \
  -d '{"dish_name": "地三鲜"}'
```

**Response:**
```json
{
  "dish_name": "地三鲜",
  "recipes": ["地三鲜\n所属菜系：东北菜\n烹饪难度：⭐⭐⭐\n\n食材与调味品\n..."]
}
```

> **Note:** Both APIs accept and return Chinese only. The agent handles translation automatically.

---

## Usage Examples

### Example 1: Recipe Lookup

**You:** How to make cola chicken wings?

**MasterChef:**
```
# Cola Chicken Wings (可乐鸡翅)
Cuisine: Chinese Home Cooking
Difficulty: ⭐⭐

## Ingredients
🍗 Chicken wings 500g (about 10 pieces)
🥤 Cola 330ml (1 can)
🧄 Garlic 3 cloves (minced)
🧅 Ginger 3 slices
🧅 Scallion 1 stalk (cut into sections)
💧 Soy sauce 2 tbsp
🍶 Cooking wine 1 tbsp
🧂 Salt to taste
🫗 Cooking oil 2 tbsp

## Steps
1. Clean chicken wings, make 2-3 cuts on each side for better flavor
2. Blanch wings in boiling water for 2 minutes, remove and drain
3. Heat oil in pan, add garlic, ginger, and scallion until fragrant
4. Add chicken wings, fry until both sides are golden
5. Pour in cooking wine and soy sauce, stir well
6. Pour in cola until wings are just covered
7. Bring to boil, then simmer on medium-low heat for 20 minutes
8. Turn to high heat to reduce sauce until thick and glossy
9. Serve hot

## Health Tips
High in sugar due to cola. For a healthier version, use diet cola or reduce the amount.
```

---

### Example 2: Ingredient Search

**You:** I have eggplant and potato, what can I cook?

**MasterChef:**
```
Based on your ingredients, here are some dishes you can make:

🍆 Eggplant:
  • Di San Xian ⭐ Top Pick (uses both eggplant and potato)
  • Braised Eggplant
  • Cold Eggplant Salad
  • Eggplant Pancake

🥔 Potato:
  • Di San Xian ⭐ Top Pick (uses both eggplant and potato)
  • Potato Beef Stew
  • Hot & Sour Shredded Potato
  • Mashed Potato

💡 "Di San Xian" is highly recommended — it uses both of your ingredients!
```

---

## Share Your Cooking 📸

Made a dish from a recipe? Share your food photos with the community!

Name your photo `{recipe_id}_{american-name}.png`, place it in the `recipe_photo/` directory, and submit a Pull Request.

**Naming examples:**
```
recipe_photo/
├── 2367_liangban-qiezi.png       # Cold Eggplant Salad
├── 973_dan-chao-fan.png          # Egg Fried Rice
└── 1203_italian-lemon-chicken.png # Italian Lemon Chicken
```

The recipe ID matches the prefix of files in the `recipe/` directory.

---

<p align="center">
Made with ❤️ by recipe@yummy.chat
</p>
