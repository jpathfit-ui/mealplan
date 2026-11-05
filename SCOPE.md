# Meal Cart: One-Page Scope

**Purpose:** Turn calorie and macro targets plus the foods you actually eat into meal specs, an exact quantified grocery list, and a cost estimate. It is a planning tool, not a recipe app. It plans before you shop.

## Core flow (target: under 2 minutes)
1. Tick the foods you will use this shopping trip (Foods tab).
2. Set calories, number of days, and how many different days to rotate (Plan tab). Rotate = 1 means the same meals every day (meal prep).
3. Generate. Get meals as ingredient specs (e.g. "Chicken 180 g, pasta 90 g, broccoli 150 g, oil 8 g, ~650 kcal, 48 g protein").
4. Open the List tab: total quantity per ingredient across all days, cost, share of spend, savings.

## Settings (set once)
- Daily calories, macro split (P/C/F %), meal slots (e.g. Breakfast = big, Lunch = light, Snack), variance at day level and meal level, optional "never exceed target" ceiling.
- Preferences: hot / cold, low prep, slow cooker.
- Stores, primary store, extra-trip cost, weekly budget.
- Google Sheet link (optional; the app works fully without it).

## Solver (no AI, runs instantly)
- Meals are built from templates (protein + carb + veg + fat) filled from your ticked foods.
- Per-100 g nutrition for each food; portions adjusted until the meal lands inside the variance window and close to the macro split.
- Whatever you tick is the rule. If you tick only ground beef, every meal uses ground beef.
- Warns when your foods cannot hit your targets instead of quietly giving bad meals.
- Swap form per meal: different protein/carb/veg, hot or cold, "use more of" an ingredient, or just surprise me.

## Money
- Typical price per food (learned as a running average from prices you log after shopping), plus optional per-store "this week" prices.
- Shows: estimated cost vs budget, savings vs typical prices, biggest spend lines (share of total).
- Store comparison only on the biggest-spend items, with a break-even check against the extra trip cost.

## Outputs
- "Find a recipe" buttons per meal (Google, Claude, ChatGPT) with a pre-built prompt containing the ingredients, amounts, macros and prep style.
- Optional Google Sheet logging (Apps Script web link): every generation logged as a row; actual prices logged after shopping in a separate tab (estimated vs actual kept apart). CSV export always available.

## Out of scope for v1
Fast-food items, recipe library, receipt photo scanning, accounts, pantry tracking, automatic flyer or store price pulls.

## Known walls and the plan
| Wall | Plan |
|---|---|
| No free official price data | v1: manual and learned prices. Phase 2: test a Loblaw/Sobeys store-site scraper or a Flipp scraper (Apify) writing to a Sheet tab the app reads. Unofficial, may break. |
| Nutrition accuracy | Starter foods use approximate values. Verify against Canadian Nutrient File / USDA and edit in the Foods tab. |
| Sales are unpredictable | Do not forecast. Track typical price, flag when below it, optional stock-up when cheap. |

## Phases
1. **v1 (this build):** planner, list, cost, savings, top spend, store compare from entered prices, Sheet logging.
2. Price layer: scraper tab in the Sheet feeds store prices automatically.
3. Receipt photo logging, pantry/leftover tracking, stock-up planning.
