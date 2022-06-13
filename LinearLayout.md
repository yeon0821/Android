# LinearLayout

## 1. LinearLayout이란 무엇이고 어떻게 사용할까

LinearLayout이란 가장 간단하면서 유용하게 쓰이는 레이아웃.

대표적인 기능은 텍스트, 버튼같은 뷰를 단순히 가로나 세로 순서대로 배치할 떄 자주 사용.

처음 사용할 때 리니어 레이아웃에는 반드시 최소 3가지 조건을 명시해야한다.

1. 높이
2. 너비
3. 배치의 방향(가로, 세로)

**android:orientation** 에서 vertical로 설정해서 추가된 3개의 버튼이 수직으로 하나씩 배치가 된것을 볼수 있다. 가로로 설정하고 싶다면 vertical 대신 horizontal을 설정.

**android:layout_width, android:layout_height** 를 통해서 레이아웃의 크기를 설정할 수 있다.

**match_parent**는 자신보단 상위의 레이아웃에 맞게 크기를 조절한다는 뜻. 여기서 더 상위 레이아웃은 없으니 자동으로 기기의 화면에 맞게 조절

------

## 2. Layout gravity

layout gravity 사용 이유

: 뷰의 위치 정렬 기준을 정하기 위해서 사용.(왼쪽, 가운데, 오른쪽 등)

------

## 3. gravity

layout gravity와 gravity는 엄연한 차이가 있으니 주의.

gravity 사용이유

: 뷰 내부의 요소들의 정렬기준을 정할 때 사용.