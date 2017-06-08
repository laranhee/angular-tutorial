## 1. Setup

## 2. The Hero Editor

- `{{ something }}` : interpolation binding syntax

컴퍼넌트의 프로퍼티 값을 html에 string으로 넣는다.

- `[(ngModel)]` : 2-way binding

`<input [(ngModel)]="hero.name">`

AngularJS와 다르게 기본으로 이용할 수 없음.`FormsModule` 필요.

## 3. Master/Detail

- `*ngFor="let hero of heroes"`

AngularJS의 `ng-repeat="hero in heroes"`와 동일.

- `@component({styles: []})`

컴퍼넌트에만 적용되는 css 지정 가능.

- `(event)` : 이벤트 바인딩

```html
<li *ngFor="let hero of heroes" (click)="onSelect(hero)">
```

- `*ngIf="selectedHero"`

AngularJS의 `ng-if="selectedHero"`와 동일.

- `[class.selected]="hero === selectedHero"`

AngularJS의 `ng-class="{selected : hero === selectedHero}"`와 동일.
