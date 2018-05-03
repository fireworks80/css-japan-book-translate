# CSS 설계 교과서

## 1-1

## CSS 설계의 중요성
운용기간이 길고, 규모가 커저서Web사이트 어플리케이션 코드를 관리하는 것은 매우 어렵습니다. 정확하게 말하면 중장기에 걸쳐 운용해 나가는 중에 코드를 낭비하게 부풀어하지 않고 생각지도 못한 버그를 초래하지 않도록 코드를 작성한다는 것이 쉽지 않습니다. 그러기 위해서는, 완화의 자신만이 알고 있는 괴상한 코드를 작성하는 것이 아니라 누구에게나 이해하기 쉬운 코드를 쓸 것이 중요합니다. 그것은 css도 예외는 아닙니다.
어떻게하면 이해하기 쉽고 안전한 css를 쓸 것인가 생각해 봅시다.

### 프론트엔드와 css일

우리들 프론트엔드의 직업은 디자인너가 photoshop으로 만들어난 디자인칸푸를 브라우저위에서 표현하는것만으로 완결하는것은 거의 없습니다.
엄밀히 말하면 일의 형태로 납품하면 끝, 이라는 것은 있을지 모르겠지만, 그 프로젝트는 납품후에도 중장기에 걸쳐 운영됩니다.
그 운용 단계에서 컨텐츠가 계속 증가 하고 때로는 캠페인이나 작은 리뉴얼을 거쳐 변화해 버립니다.
그 중에서 납품처 담당자나 자사 서비스에서의 운영을 담당하는 개발자는 코드를 유지보수하고 유지하지 않으면 안됩니다.
이책을 손에 들고 있는 독자여러분은 아마도 위의 어느 하나에 해당하는 것이 아닐까 생각합니다. 프로젝트의 시작때부터 관계 첫 번째 줄의 코드를 작성 하는 입장일 수도 있고 어느 누군가가 작성한 코드를 유지보수하는 입장일 수도 있습니다. 어쨌든 전자 이면 후임자가 곤란하지 않을 것 같은 코드를, 후자이면 유지 보수 할 수록
심해지지 않도록 할 수 있는 코드를 작성해야 합니다.
이해할 수 없는 코드를 쓰는 것은 다른 개발자 뿐만 아니라, 1개월 후, 1주일 후, 3일 후 자신도 곤란하게 될 수 있습니다. 불행히도, 이러한 문제에 직면하고 처음으로 제대로 코드를 작성 했어야 했다고 후회하게 됩니다.

운영중 컨텐츠가 늘어, 보다 많은 사람이 관여하도록 되어 있다......

하지만, HTML5등장과 간단한 web사이트로부터 복잡한 web어플리케이션의 발전에 의해 풍부한 web사이트를 취급하는것이 일반화 된 지금, 코드도 점점 복잡화 되고 있습니다.
이 책에 포커스되는 css도 예외는 아니고 css 그것이 에니메이션 같은 표현을 다루게 될 수도 있고, 다른 한편으로 보다 많은 레이아웃의 기능을 가지거나 고해상도 모바일 브라우저에 대응하거나 하기 위해 테크닉을 구사하지 않으면 안되는 것도 있습니다.
풍부한 표현으로는 javascript가 주목되기 쉬운 것이 작년의 web이었으나, 그 배경에서 css로서 아키텍쳐(설계사상)나, 개발효율성과 유지 보수 효율을 높이기 위한 방법을 도입함으로써 보다 높은 품질의 web사이트 응용프로그램을 구축 할 수 있습니다. 이를 위해 css의 설계(디자인)이라는 것을 지금 다시 생각하는 것이 중요해 지고 있는 것입니다. 

### 개발에서 없어서는 않될 설계

'설계'라는 말은 넓게 잡으면, 기획이나 디자인의 공정에서는 정보설정 이나 UI설계가 빠져서는 안되고, 개발과정에서는 백엔드로서의 서버나 데이터베이스의 설계등이 필요합니다. 프론트엔드에서는 특히 최근의 경항으로 MV*계의 아키텍쳐가 화재가 된 javascript설계도 매우 중요해지고 있습니다만, CSS도 예외는 아닙니다.
여기에서 설계가 왜 필요한지 포합에서 CSS설계의 필요성을 생각해 봅시다.

이러한 설계 아키텍쳐라는 말로써 자주 예가 되는 것은 건축이야기 입니다.(처음 아키텍쳐라는 언어가 건축용어에서 유래 되었기 때문에) 이상적인 완성 예상도만 보고, 그것이 어떻게 만들어지는지 파악하지 않고, 정말로 안전하고 미려한 것을 만들 수 있을까요?
우리들의 web의 개발 작업으로 말하면, 완성예상도는 photoshop에서 제작 주입된 설계 데이터로 대체 생각 할 수 있습니다. 단순히 그것을 재현하는 것 뿐만이라면 일부 브라우저의 버그에 대응하지 않으면 안되지만 그만큼 어렵다는 것은 아닙니다.
문제는 앞에서 언급한대로 그 프로젝트가 운영단계에 들어가, 많은 혁신이 필요하게 되었을때 입니다.
어제까지 단색 밝은 베이지의 배경이었던 곳이 오늘에는 청과흰 스트라이프로 변경되었다면 그것은 어렵지 않고, 건축물에도 갈아치우며 고쳐는 정도 입니다.

하지만, 건축물과 달리 Web에서는 구조 자체를 크게 변경하거나 의외의 요소를 삽입 또는 제거 하지 않으면 안될 수 있습니다. 하지만 아무리 이 같은 일이 일어 날 수 있다고 해도 아무도 그 미래를 예측 할 수 없습니다.
책 전체를 통해 전하고 싶은 메시지 하나는 어떤 변화에 대해서도 전혀 손을 넣을 필요가 없는 CSS를 작성하는 것은 불가능 합니다. 따라서 우리가 할 수 있는 것, 그리고 이 책에서 설명하는 것은 어떻게 하면 유지관리 휴울성을 떨어뜨리지 않고 또한 적은 노력으로 혁신할 수 있도록 디자인을 생각하는 것입니다.

## 보다 나은 CSS목표

보다나은 설계 목표로서 Google엔지니어로 있는 HTML/CSS 관련 도구 와 문서를 남기고 있는 philwalton씨의 블로그 기사에서 인용한 다음 4가지를 예를 들겠습니다.

ー 예측 가능한
- 재사용 가능한
- 유지 관리가 쉬운
- 확장 가능한

이 목표는 출신기사에도 있듯이 CSS뿐만 아니라 소프트웨어 개발 프로그래밍 언어 전반에 말할 수 있는 것이고, 반대로 말하면, 많은 프로그래밍 언어가 가지는 사례의 본질은 CSS에서도 살릴 수 있습니다.
CSS에서 이들이 구체적으로 어떤 의미를 가지는지를 설명 해야 합니다.

### 예측 가능한

예측 가능하다는 말하는 것은 예상대로 행동 여부 것입니다. 다른 규칙이 영향을 서술 한 규칙대로 행동이나 모양이되지 않거나 추가 한 규칙이 다른 규칙에 영향을 줄 수 없도록하는 것입니다.

### 재사용 가능한

스타일이 복사 & 붙여넣기 되면서 계속 커지는 CSS가되지 않기 위해서라도 재사용 가능한 규칙을 가지는 것이 중요합니다 재사용 가능한 규칙이라는 것은 추상적이고 기능별로 분리되어 있을 필요가 있습니다. 발생한 UI 디자인의 마크 업 CSS를 한 번 만들면, 다시 유사한 UI를 만나면 일부러 고쳐 쓸 필요가 없도록하는 것이 이상적입니다.

### 유지 관리가 쉬운

새로운 규칙을 추가하거나 업데이트 할 때 기존의 규칙 리팩토링 필요로 하지 않는 것이 중요합니다 추가 한 규칙에 따라 기존의 규칙을 깨고 버리는 것은 피한다.

###확장 가능한 

자신과 자신 이외의 프로젝트에 참여하는 개발자를위한 유지 보수 관리가 쉽기해야합니다. 여기에서의 확장 용이성이라는 것은 단순히 CSS 규칙으로 뿐 아니라 그 CSS 설계가 사이트의 규모가 크고 복잡해짐에 따라 확장하기 쉬운 것이 되느냐는 것입니다. 또한 다른 개발자가 관련 프로젝트에서 그 CSS 디자인의 학습 비용은 낮게 있어야 합니다. 이 4 가지 목표를 충족시킬 수있는 CSS라면 좋은 설계의 CSS이라고합니다. 그러나 CSS는 이들을 충족시키기 위해 무력으로 쉽게 코드가 무너져 버립니다. 다음 섹션에서는 어떻게 CSS가 무너질 것인가를 생각해 봅시다.