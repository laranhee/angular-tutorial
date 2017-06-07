## 1. Setup

## 2. The Hero Editor

- `{{ something }}` : interpolation binding syntax

컴퍼넌트의 프로퍼티 값을 html에 string으로 넣는다.

- `[(ngModel)]` : 2-way binding

`<input [(ngModel)]="hero.name">`

AngularJS와 다르게 기본으로 이용할 수 없음.`FormsModule` 필요.
