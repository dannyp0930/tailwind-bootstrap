# Tailwind CSS: Utility-First

## 목차

- [Tailwind CSS Core Concept](#Tailwind-CSS-Core-Concept)
- [Tailwind CSS VS Bootstrap](#Tailwind-CSS-VS-Bootstrap)
- [결론](#결론)
- [참조](#참조)

## Tailwind CSS Core Concept

### Utility-First Fundamentals

- 미리 정의된 유틸리티 클래스를 사용하여 스타일을 적용
- 구체적이고 단일한 목적을 가져 높은 재사용성
- 클래스 이름이 스타일의 기능을 나타내 코드를 읽고 이해하기 용이

```html
<button class="bg-[#0d6efd] border border-[#0d6efd] text-white py-[0.375rem] px-3 leading-normal rounded-md">Tailwind</button>
```

### Hover, Focus, and Other States
:hover, :foucs와 같은 Pseudo class, ::before, ::after와 같은 Pseudo element를 간단히 스타일링 가능

```html
<button class="... hover:bg-[#0b5ed7]">Tailwind</button>
```

### Responsive Design

반응형 클래스:Mobile First(sm:, md:, lg:, xl:, 2xl:)릍 통한 반응형 디자인 구현
- sm: 640px
- md: 768px
- lg: 1024px
- xl: 1280px
- 2xl: 1536px

```html
<p class="text-3xl sm:text-2xl md:text-xl lg:text-base">
  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
  Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
  Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
  Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</p>
```

### Reusing Styles

```css
/* index.css */

@tailwind base;
@tailwind components;
@tailwind utilities;

@layer components {
  .btn {
      @apply border py-[0.375rem] px-3 leading-normal rounded-md ;
  }
  .btn-primary {
    @apply bg-[#0d6efd] border border-[#0d6efd] text-white py-[0.375rem] px-3 leading-normal rounded-md hover:bg-[#0b5ed7];
  }
}
```

```html
<button class="btn btn-primary">Tailwind</button>
```

- base: reset이나 default 스타일과 같이 전체 HTML에 적용할 경우
- components: 유틸리티로 재정의 하는 클래스 기반의 스타일
- utilities: 단일한 목적으로 사용하는 클래스, 다른 스타일보다 우선

###  Custom Styles

`tailwind.config.js` 설정을 통한 커스터마이징이 가능하다.
기존 tailwind css 설정을 사용하면서 추가하기 위해 `extend`설정 활용

```js
// tailwind.config.js

/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./src/**/*.{html,js}'],
  theme: {
    colors: {
      'blue': '#1fb6ff',
      'purple': '#7e5bef',
      'pink': '#ff49db',
      'orange': '#ff7849',
      'green': '#13ce66',
      'yellow': '#ffc82c',
      'gray-dark': '#273444',
      'gray': '#8492a6',
      'gray-light': '#d3dce6',
    },
    fontFamily: {
      sans: ['Graphik', 'sans-serif'],
      serif: ['Merriweather', 'serif'],
    },
    extend: {
      spacing: {
        '8xl': '96rem',
        '9xl': '128rem',
      },
      borderRadius: {
        '4xl': '2rem',
      }
    }
  },
}
```

## Tailwind CSS VS Bootstrap

### Tailwind CSS

- 유틸리티 클래스 기반으로 세밀한 스타일 조정 가능
- `tailwind.config.js` 파일을 통해 자유롭게 커스터마이즈
- JIT(Just-In-Time)엔진으로 코드에서 사용되는 CSS만 생성한 최적화
- 높은 러닝 커브

### Bootstrap

- 미리 정의된 컴포넌트와 디자인 시스템 제공
- SASS 변수 등 으로 커스터마이징 가능하지만 기본 스타일에 제한적
- 기본 CSS와 JS 파일이 함께 제공되며, 사용하지 않는 컴포넌트 포함될 가능성 존재
- 낮은 러닝커브

## 결론

- Tailwind CSS
  - 다양한 커스터마이징 필요할 때
  - 최적화를 우선시 할 때

- Bootstrap
  - 간단한 컴포넌트들로 빠른 개발이 필요 할 때
  - 특별한 디자인이 필요 없는 경우


## 참조

- https://tailwindcss.com/
- https://getbootstrap.com/