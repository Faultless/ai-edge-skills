## Gemma AI Skills

A collection of Gemma LLM skills for use with the [Google AI Edge Gallery](https://github.com/google-ai-edge/gallery) app on Android and iOS.

## Skills

### Food Macro Tracker

Analyze food from a photo or ingredient list to estimate calories, protein, fat, and carbs using the [Spoonacular API](https://spoonacular.com/food-api).

**Features:**
- Send a photo of your meal and Gemma identifies the ingredients
- Or type ingredients directly (e.g. "2 cups rice, 1 lb chicken breast")
- Returns per-ingredient and total macro breakdown
- Interactive webview with donut chart visualization

**Tags:** `JS` `API` `Webview` `Secret` `Camera`

## How to Add Skills to the AI Edge Gallery App

### Prerequisites

1. Install the **AI Edge Gallery** app on your device
   - Android: [Google Play Store](https://play.google.com/store/apps/details?id=com.google.ai.edge.gallery)
   - iOS: [App Store](https://apps.apple.com/app/google-ai-edge-gallery/id6740718624)
2. Get a free [Spoonacular API key](https://spoonacular.com/food-api) (for the Food Macro Tracker skill)

### Option 1: Load from URL (Recommended)

This method loads the skill directly from this GitHub Pages site.

1. Open the **AI Edge Gallery** app and select a model (e.g. Gemma) to enter the **Agent Skills** use case.
2. Tap the **Skills** chip at the top of the chat screen.
3. Tap the **(+)** button and select **Load skill from URL**.
4. Enter the skill URL:
   ```
   https://<username>.github.io/ai-edge-skills/food-macro-tracker
   ```
5. The skill will be downloaded and added to your skill list.
6. When you first use the skill, the app will prompt you to enter your **Spoonacular API key**. This is stored locally on your device and never sent through the LLM.

### Option 2: Import from Local File (Android only)

Use this if you want to test locally or don't have the GitHub Pages site deployed.

1. Clone this repo and connect your Android device via USB.
2. Push the skill folder to your device:
   ```bash
   adb push food-macro-tracker/ /sdcard/Download/
   ```
3. Open the **AI Edge Gallery** app and enter the **Agent Skills** use case.
4. Tap the **Skills** chip, then the **(+)** button, and select **Import local skill**.
5. Use the file picker to navigate to the `food-macro-tracker` folder in your Downloads directory.

### Option 3: Add from Community-Featured Skills

If this skill is listed in the [community skills gallery](https://github.com/google-ai-edge/gallery/discussions/categories/skills):

1. Open the **AI Edge Gallery** app and enter the **Agent Skills** use case.
2. Tap the **Skills** chip, then the **(+)** button, and select **Add skill from featured list**.
3. Find **Food Macro Tracker** in the list and tap to add it.

## Using the Skill

Once the skill is installed:

1. Start a conversation with your model in the Agent Skills use case.
2. **From a photo:** Take or attach a photo of food. The model will identify the ingredients and estimate portion sizes, then call the skill to get nutrition data.
3. **From text:** Type your ingredients, e.g.:
   ```
   What are the macros for 2 eggs, 2 slices of bacon, and 1 slice of toast with butter?
   ```
4. The skill returns:
   - A text summary of total calories, protein, fat, carbs, fiber, and sugar
   - An interactive card with a donut chart and per-ingredient breakdown

## Repo Structure

```
ai-edge-skills/
├── .nojekyll                          # Ensures GitHub Pages serves .md as raw files
├── index.html                         # Landing page for the GitHub Pages site
├── README.md
└── food-macro-tracker/
    ├── SKILL.md                       # Skill metadata + LLM instructions
    ├── scripts/
    │   └── index.html                 # JS logic (Spoonacular API integration)
    └── assets/
        └── webview.html               # Interactive nutrition display
```

## Deploying Your Own Copy

1. Fork or clone this repo.
2. Push to your GitHub account.
3. Go to **Settings > Pages** and set the source to the `main` branch.
4. Your skills will be available at `https://<username>.github.io/ai-edge-skills/`.

The `.nojekyll` file in the repo root is critical -- it prevents GitHub Pages from processing `SKILL.md` files through Jekyll, which would break the AI Edge Gallery app's ability to parse them.
