# React-TypeScript-Settings
1. React-TypeScript
2. ESLint-Prettier

VSCode 에디터 기반으로 리액트 프로젝트 환경설정에 대한 내용입니다.

변경사항은 계속 업데이트 예정입니다.

React 설치

TypeScript 설치

ESLint-Prettier 설치 및 설정

레퍼런스

레포 주소

**이 글은 기본적인 프로그램이 설치된 상태를 가정합니다(node, npx, vscode)**

## React & TypeScript 설치

타입스크립트 템플릿 CRA로 손쉽게 설치할 수 있다

```jsx
npx create-react-app [project name] --template typescript
```

- `--template` 를 빼먹을 경우 타입스크립트를 제외한 React 환경만 설치된다.
- 프로젝트 파일들을 살펴보자 예 )`.tsx` 로 이루어져있는지

## ESLint 설정하기

- ESLint? 
- ESLint는 ECMAScript 코드에서 문제점을 검사하고 일부는 더 나은 코드로 정정하는 린트 도구 중의 하나

### 필요한 모듈 설치하기

```jsx
npm i --save-dev typescript eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

`.eslintrc.json` 파일 수정

```jsx
{
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "project": "./tsconfig.json"
  },
  "env": {
    "node": true
  },
  "extends": ["plugin:@typescript-eslint/recommended"]
}
```

### typescript-eslint 실행

```jsx
# 기본적으로 js 확장자만 검사하므로
npx eslint --ext .js,.ts src
# 또는
npx eslint src/**/*
```

### vscode 에서 ESLint Extenstion 을 설치한 후 `settings.json` 파일에 다음의 항목을 추가한다.

```jsx
{
  "eslint.validate": [
    { "language": "typescript", "autoFix": true },
    { "language": "typescriptreact", "autoFix": true }
  ]
}
```

## Prettier 적용하기

- Prettier?
- An opinionated code formatter
- 이 단계는 ESLint를 적용한 이후에 진행한다

### 필요한 모듈 설치

```jsx
npm i --save-dev prettier eslint-plugin-prettier eslint-config-prettier
```

`.eslintrc.json` 설정에 추가

```jsx
{
  "extends": ["plugin:prettier/recommended", "prettier/@typescript-eslint"]
}
```

최종

```jsx
{
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "project": "./tsconfig.json"
  },
  "env": {
    "node": true
  },
  "extends": ["plugin:@typescript-eslint/recommended", "plugin:prettier/recommended", "prettier/@typescript-eslint"]
}
```

### vscode 에서 Prettier Extenstion 을 설치한 후 `settings.json` 파일에 다음의 항목을 추가한다.

```jsx
{
  "javascript.format.enable": false,
  "typescript.format.enable": false
}
```

## 관련 에러 핸들링

`Could not find a declaration file for module 'react'. '/Users/sungtaekpark/personal/eslint-setting/node_modules/react/index.js' implicitly has an 'any' type.`

 위와 같은 에러가 발생하는 경우

```jsx
// 타입스크립트를 적용했기 때문에 타입스크립트 관련 모듈을 다시 설치해줬다
$ npm install --save @types/react
```

- React 를 타입스크립트 버전으로 수정해주는 과정

## Reference

[[React] TypeScript와 ESLint, Prettier 설정하기](https://gingerkang.tistory.com/98)