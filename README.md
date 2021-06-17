# SCSS

## インストール

- npm:
  > npm install -g sass
- yarn:
  > yarn add -g sass

## 起動方法

- 基本（HTML）
  > sass --watch input.scss output.css
- ReactJS,NextJS,VueJS... : プロジェクトによって設定方法があるので、プロジェクトレーダーに確認することになる。

## 変数

- SCSS

```css:
$font-stack: "Noto Serif JP", sans-serif;
$primary-color: #000;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

- CSS

```css:
body {
  font: 100% "Noto Serif JP", sans-serif;
  color: #000;
}
```

## Nesting

- SCSS

```css:
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

- CSS

```css:
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```

## Mixins

```scss:
$baseSize: 10px;
$mobile_width: 480px;
$tablet_width: 768px;

@mixin mobile {
  @media (max-width: $mobile_width) {
    @content;
  }
}

@mixin tablet {
  @media (max-width: $tablet_width) {
    @content;
  }
}

html {
  font-size: $baseSize;
  @include tablet {
    font-size: $baseSize * 0.9;
  }
  @include mobile {
    font-size: $baseSize * 0.8;
  }
}

body {
  margin: 0 auto;
  @include tablet {
    margin: 0 1rem;
  }
  @include mobile {
    margin: 0 0.4rem;
  }
}

```

- CSS

```css:
html {
  font-size: 10px;
}
@media (max-width: 768px) {
  html {
    font-size: 9px;
  }
}
@media (max-width: 480px) {
  html {
    font-size: 8px;
  }
}

body {
  margin: 0 auto;
}
@media (max-width: 768px) {
  body {
    margin: 0 1rem;
  }
}
@media (max-width: 480px) {
  body {
    margin: 0 0.4rem;
  }
}
```

## Extend/Inheritance(拡張・継承)

```scss:
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.message {
  @extend %message-shared;
}

.success {
  @extend %message-shared;
  border-color: green;
}

.error {
  @extend %message-shared;
  border-color: red;
}

.warning {
  @extend %message-shared;
  border-color: yellow;
}

```

- CSS

```css:
.warning, .error, .success, .message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}
```
