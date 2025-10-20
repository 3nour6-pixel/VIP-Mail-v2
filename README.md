# VIP Mail Website - Multi-Language Support

## Overview
VIP Mail is a premium email service website with full support for English and Arabic languages. The website automatically detects the user's browser language preference and displays content accordingly.

## Features Implemented

### 1. Default Language: English
- The website now loads in English by default (lang="en", dir="ltr")
- All HTML files have been updated with English content

### 2. Automatic Language Detection
- The website detects the browser's preferred language on first visit
- If the browser language is Arabic, content automatically switches to Arabic
- Otherwise, English content is displayed

### 3. Language Switcher Buttons
- Two elegant circular buttons (EN/AR) in the navigation bar
- Professional design with active state highlighting
- Available in both desktop and mobile views
- Language preference is saved in localStorage for future visits

### 4. RTL/LTR Support
- Arabic: Right-to-left (RTL) layout with appropriate text alignment
- English: Left-to-right (LTR) layout with appropriate text alignment
- Direction changes automatically when switching languages

## Files Modified

### Core Files:
- `index.html` - Main page (fully updated)
- `about.html` - About Us page (fully updated)
- `contact.html` - Contact page (fully updated)
- `translations.js` - New file containing all translations
- `script.js` - Added language detection and switching functionality
- `styles.css` - Added language switcher button styles

### Pending Updates:
The following files still need to be updated with the same pattern:
- `payment.html`
- `inbox.html`
- `privacy.html`
- `terms.html`
- `refund.html`

## How to Update Remaining Pages

To update any remaining page, follow this pattern:

1. Change the HTML tag:
```html
<!-- OLD -->
<html lang="ar" dir="rtl">

<!-- NEW -->
<html lang="en" dir="ltr">
```

2. Add translations script:
```html
<script src="translations.js"></script>
```

3. Add language switcher buttons in the navbar:
```html
<div class="lang-switcher">
    <button class="lang-btn" id="lang-en">EN</button>
    <button class="lang-btn" id="lang-ar">AR</button>
</div>
```

4. Add data-i18n attributes to translatable elements:
```html
<h1 data-i18n="page_title">Page Title</h1>
<p data-i18n="description">Description text</p>
```

5. Add corresponding translations in `translations.js`:
```javascript
en: {
    page_title: "Page Title",
    description: "Description text"
},
ar: {
    page_title: "عنوان الصفحة",
    description: "نص الوصف"
}
```

## Technical Implementation

### Language Detection
```javascript
function getBrowserLanguage() {
    const browserLang = navigator.language || navigator.userLanguage;
    return browserLang.startsWith('ar') ? 'ar' : 'en';
}
```

### Language Switching
```javascript
function setLanguage(lang) {
    currentLang = lang;
    localStorage.setItem('preferredLang', lang);

    const htmlElement = document.documentElement;
    htmlElement.setAttribute('lang', lang);
    htmlElement.setAttribute('dir', lang === 'ar' ? 'rtl' : 'ltr');

    // Update all translatable elements
    document.querySelectorAll('[data-i18n]').forEach(element => {
        const key = element.getAttribute('data-i18n');
        if (translations[lang] && translations[lang][key]) {
            element.textContent = translations[lang][key];
        }
    });
}
```

## Usage

1. Open any page - it will automatically load in English
2. If your browser is set to Arabic, content will switch to Arabic
3. Click EN/AR buttons to manually switch languages
4. Your language preference is remembered for future visits

## Browser Support

- All modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile responsive design
- Graceful fallback for older browsers

## Future Enhancements

- Complete translation for all remaining pages
- Add more languages (French, Spanish, etc.)
- Implement server-side language detection
- Add language-specific SEO metadata

---

**Note**: The website is fully functional with English as the default language and automatic Arabic switching when detected.
