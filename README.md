## 1. Setup

## 2. The Hero Editor

`{{ something }}` : interpolation binding syntax

- 컴퍼넌트의 프로퍼티 값을 html에 string으로 넣는다.

`[(ngModel)]` : 2-way binding

- `<input [(ngModel)]="hero.name">`

- AngularJS와 다르게 기본으로 이용할 수 없음.`FormsModule` 필요.

## 3. Master/Detail

`*ngFor="let hero of heroes"`

- AngularJS의 `ng-repeat="hero in heroes"`와 동일.

`@component({styles: []})`

- 컴퍼넌트에만 적용되는 css 지정 가능.

`(event)` : 이벤트 바인딩

```html
<li *ngFor="let hero of heroes" (click)="onSelect(hero)">
```

`*ngIf="selectedHero"`

- AngularJS의 `ng-if="selectedHero"`와 동일.

`[class.selected]="hero === selectedHero"`

- AngularJS의 `ng-class="{selected : hero === selectedHero}"`와 동일.

## 4. Multiple Components

```js
import { Component } from '@angular/core';

@Component({
  selector: 'hero-detail',
})
export class HeroDetailComponent {
}
```

- component를 정의하려면 `Component` 심볼을 항상 `import`해야한다.

- component 클래스는 항상 다른곳에서 `import`하기에 `export`한다.

`binding expression`

```html
<hero-detail [hero]="selectedHero"></hero-detail>
```

```js
export class HeroDetailComponent {
  @Input() hero: Hero;
}
```

- `[hero]="selectedHero"`에서 hero는 binding expression의 타겟이 된다.

- *target* 바인딩 프로퍼티를 `@Input()`을 통해 *input* 프로퍼티로 선언해야한다.

- 부모 component의 `selectedHero` 프로퍼티를 자식 component의 `hero` 프로퍼티로 바인드함.

`Module`

- 모든 component는 `Angular module`안에 선언되어야 한다.

```js
declarations: [
  AppComponent,
  HeroDetailComponent
],
```

- module의 `declarations` 배열에는 module에 속할 component, pipe, directive가 포함된다.
