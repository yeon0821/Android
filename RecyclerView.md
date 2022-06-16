> ## RecyclerView란?

사용자가 관리하는 많은 수의 **데이터 집합(Data Set)**을 개별 **아이템** 단위로 구성하여
화면에 출력하는 **뷰그룹(ViewGroup)**이며, 한 화면에 표시되기 힘든 많은 수의 데이터를
**스크롤 가능한 리스트**로 표시해주는 위젯 (v7 지원 라이브러리(v7 Support Library)에서 제공됨)

→ 즉, ***리스트뷰(ListView)에서 유연함(Flexibility) & 성능(Performance)*** 더한 것!

### → ListView의 단점을 보완하기 위해 나옴

ListView는 리스트 항목이 갱신될 때마다, 매번 아이템 뷰를 새로 구성해야 함 → 성능 低



> ### How is it Flexible?

- RecyclerView는 기본적으로 **뷰홀더(ViewHolder) 패턴** 사용
- 수직(Vertical) 뿐만 아니라 **수평(Horizontal) 방향, Grid(격자)로 아이템들이 나열**되게 만들 수 있음
- 아이템 뷰의 **동적(Dynamic)구성을 용이**하게 만들어줌
- 또한, 이를 런타임(run-time)에 바꾸게 만들 수 있음



> ### RecyclerView 구성 요소

- **Adapter** 사용 : 아이템 뷰를 생성하는 역할

- **Layout Manager** 제공 : 아이템 뷰가 나열되는 형태를 관리하기 위한 요소
  → 레이아웃매니저(LayoutManager)가 제공하는 레이아웃 형태로, 어댑터를 통해 만들어진 각 아이템 뷰는 "뷰홀더(ViewHolder)"객체에 저장되어 화면에 표시되고, 필요에 따라 생성 또는 재활용(Recycle)

- **ViewHolder** : 화면에 표시될 아이템 뷰를 저장하는 객체. 어댑터에 의해 관리되며, 미리 생성된 뷰홀더 객체가 있는 경우, 새로 생성하지 않고 이미 만들어져 있는 뷰홀더를 재활용하는데, 이 때는 단순히 데이터가 뷰홀더의 아이템 뷰에 바인딩(Binding)됨.

  

> ### RecyclerView 사용법

![img](https://velog.velcdn.com/images%2Fryalya%2Fpost%2Fecc92863-f914-4356-b4f3-722a9d7ca11c%2Fimage.png)

- step1. 사용할 Activity XML에 RecyclerView 추가
- step2. RecyclerView 아이템에 표시될 View 레이아웃 추가
  ( → 아이템 View를 위한 레이아웃 XML 작성 )
- step3. Adapter 구현
  ( → RecyclerView.Adapter상속하여 구현 )

```null
- onCreateViewHolder(ViewGroup parent, int viewType) : viewType 형태의 아이템 뷰를 위한 뷰홀더 객체 생성. 
- onBindViewHolder(ViewHolder holder, int position) : position에 해당하는 데이터를 뷰홀더의 아이템뷰에 표시.
- getItemCount() : 전체 아이템 갯수 리턴.
```

- step4. RecyclerView에 Adapter와 Layout Manager 지정
  ( → setAdapter(), setLayoutManager() 메서드 사용하여 지정 )



> ### RecycklerView 생명주기(패턴)

- ### onAttachedToRecyclerView

- ### onCreateViewHolder

- ### onBindViewHolder

  → ViewHolder Binding

- ### onViewAttachedToWindow

  → Holder가 화면에 완전히 보여짐

- ### onViewDetachedFromWindow

  → Holder가 화면에서 완전히 보여지지 않음

- ### onViewRecycled

  → 재활용 할 Holder 가져오기
  (log ex. → 0번째 홀더가 재사용 되겠음을 알리는 onViewRecycled: 0)

- ### onDetachedFromRecyclerView