# MageHx_MageTemplateUtils

A Magento 2 module that introduces convenient global utilities for use in `.phtml` templates, helping you write cleaner, more expressive code.

---

## ✨ Features

### 🔒 Escaper Shortcuts

Use simple closure aliases instead of long `$escaper` method calls:

| Alias          | Equivalent                     |
|----------------|--------------------------------|
| `$eHtml()`     | `$escaper->escapeHtml()`       |
| `$eJs()`       | `$escaper->escapeJs()`         |
| `$eUrl()`      | `$escaper->escapeUrl()`        |
| `$eHtmlAttr()` | `$escaper->escapeHtmlAttr()`   |

**Example:**

```php
<?= $eHtml(__('Hello world!')) ?>
````

Instead of:

```php
<?= $escaper->escapeHtml(__('Hello world!')) ?>
```
---

### 📦 ViewModel Provider – `$viewModelProvider`

Fetch a ViewModel instance directly inside a `.phtml` file without having to declare it in layout XML:

```php
<?php
use Namespace\Module\ViewModel\YourViewModel;

/** @var Closure $viewModelProvider */

$viewModel = $viewModelProvider(YourViewModel::class);
?>
```
---

### 🧾 Form Key Helper – `$formKey`

Insert a hidden form key input in one line:

```php
<form>
    <?= $formKey ?>
    ...
</form>
```

Simple, secure, and saves time.

---

### 🔐 CSP Nonce Provider – `$nonce`

Generate a valid CSP nonce for inline scripts:

```php
<script nonce="<?= $eHtmlAttr($nonce) ?>">
    // safe inline script
</script>
```

Essential for security-conscious development.

---

### 🎨 Conditional Class Names – `$classNames`

Apply dynamic class names with ease and clarity:

**Before:**

```php
<div class="flex items-center <?= $escaper->escapeHtmlAttr($condition1 ? 'justify-between' : 'justify-center') ?> <?= $escaper->escapeHtmlAttr($i > 10 ? 'bg-orange' : '') ?>">
    ...
</div>
```

**After:**

```php
<div class="<?= $classNames([
    'flex items-center',
    $condition1 ? 'justify-between' : 'justify-center',
    'bg-orange' => $i > 10
]) ?>">
    ...
</div>
```

Improves readability and maintainability of conditional UI.

---

## 📦 Installation

```cmd
composer require magehx/mage-template-utils
```

---

## 🔗 Requirements

* PHP **8.1+**

---

## 🛠️ License

[MIT](LICENSE) – free to use and modify.

---

## 💬 Feedback / Contributions

PRs and issues are welcome. Let’s make Magento templating less painful!

