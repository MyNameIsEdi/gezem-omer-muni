
# Omer Sanitation Schedule Widget 🚛

A custom, lightweight web widget designed for the Local Council of Omer (מועצה מקומית עומר). It allows residents to easily search for their address to get accurate garbage and yard waste collection schedules.

Designed specifically to be drop-in ready for **WordPress / Elementor** via the Custom HTML Widget, requiring absolutely zero external dependencies.

## ✨ Features

* **Smart Autocomplete:** A custom-built, fast autocomplete dropdown that highlights matched letters as the user types and filters results in real-time.
* **Complex Routing Logic:** Intelligently handles split streets (e.g., streets where houses 1-37 are in District C, and 38+ are in District D).
* **Smart Parsing:** Automatically ignores the word "רחוב" (Street) if typed by the user and seamlessly separates the text (street name) from the numbers (house number) within a single input field.
* **Keyboard Navigation:** Fully supports keyboard arrows (Up/Down) and `Enter` for accessibility and speed.
* **Zero Dependencies:** Pure Vanilla JavaScript, HTML, and CSS. No jQuery or heavy libraries needed.
* **Responsive UI:** Mobile-friendly design with clear error handling, color-coded feedback, and visual cues.

## 🚀 Installation (Elementor / WordPress)

1. Open your page in the Elementor Editor.
2. Search for the **HTML** widget and drag it into your desired section.
3. Copy the entire code block (HTML + CSS + JS) from `index.html`.
4. Paste it into the HTML Code box in Elementor.
5. Click **Update/Publish**.
*(Note: Be sure to clear your WordPress cache to see the live changes).*

## 🧠 How it Works

The logic relies on two main data objects in the JavaScript:

### 1. `districtDays`

Defines the collection schedule for each district (רובע).

```javascript
const districtDays = {
  "א'": { garbage: "שני, רביעי ושישי", yardOut: "ראשון", yardCollect: "שני" },
  // ...
};

```

### 2. `streets`

Acts as the database mapping streets to their respective districts.

* **Standard Streets:** Mapped directly to a string (e.g., `"תפוז": "א'"`).
* **Split Streets:** Mapped to an array of objects defining the `min` and `max` house numbers for each district.

```javascript
const streets = {
  "תפוז": "א'", // Regular street
  "אורן": [     // Split street
    { min: 1, max: 37, district: "ג'" },
    { min: 38, max: 999, district: "ד'" }
  ]
};

```

## 🛠️ Customization

* **Styling:** All CSS is scoped under the `.omer-sanitation-app` class to prevent conflicts with your website's global styles. You can easily tweak the primary colors (`#085c34` for green, `#f5e1a9` for the result card) in the `<style>` block.
* **Rules & Guidelines:** The bottom of the success card contains a `.rules-box` div. You can edit the `<ul>` list in the `showSuccess()` function to update the municipal guidelines for waste disposal.

## 📄 License

This project is open-source and available under the [MIT License](https://www.google.com/search?q=LICENSE).
