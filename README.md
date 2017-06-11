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

## 5. Services

`@Injectable()`

- TypeScript에게 Angular가 이 service에게 의존성을 주입해야할 수 있다는 메타데이터를 방출한다.

- 의존성이 없더라도 기본적으로 명시하는 것을 스타일가이드는 추천.

- `@Component`는 `@Injectable`의 서브타입으로 component는 따로 명시 안해줘도 됨.

`component에 service 주입`

1. component 클래스에 private 프로퍼티를 정의한 생성자를 추가.

2. @component에 providers 메타데이터를 추가.

`ngOnInit` : 라이프사이클 훅 : component의 생성시에 호출.

- Angular는 component, directive의 라이프사이클에 대한 interface를 제공.

- `OnInit` interface의 `ngOnInit(): void`.

## 6. Routing

`@NgModule({providers: []})`

- 여러 뷰에서 서비스가 필요하다면 @NgModule에 providers에 이용할 서비스를 넣는다. 싱글톤 인스턴스.

`RouterModule`

- 라우팅을 위한 모듈

1. `<base href="/">` 설정

```js
RouterModule.forRoot([
  {
    path: 'heroes',
    component: HeroesComponent
  }
])
```
2. route 설정

    - `RouterModule.forRoot()`을 통해 route 정의 설정.

    - `path` : router가 매칭할 경로

    - `component` : router가 만들어야 할 component

3. `<router-outlet>`

- router가 route에 맞는 component를 보여주는 곳.

4. `<a routerLink="/heroes">`

- 사용자가 링크를 클릭했을 때 router에게 어디로 navigate 해야하는지 알려준다.

*`router component`*

- router에 붙어지고, 라우팅 된 뷰를 보여주는 component를 *router component* 라 칭함.

`parameterized route`

- `path: 'detail/:id'` : `:`로 파라미터 표현.

- `ActivatedRoute.params`에 정보가 들어있다. (id : "13")

`pipe`

```html
{{selectedHero.name | uppercase}} is my hero
```

- 템플릿에 보여질 값을 변화함.
