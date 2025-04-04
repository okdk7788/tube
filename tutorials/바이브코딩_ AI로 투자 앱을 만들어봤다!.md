## AI를 활용한 투자 앱 개발 시도: 현실적인 튜토리얼 가이드

**서론**

이 튜토리얼은 프로그래밍 초보자라는 가정 하에, 오직 AI 도구만을 사용하여 투자 관리 애플리케이션을 구축하는 과정을 안내합니다. 강의 영상의 내용을 바탕으로, 실제 AI 도구(Repl.it Agent, Vercel v0, Vault.new, Lovable)를 사용했을 때 어떤 결과가 나오는지, 그리고 그 과정에서 겪게 되는 현실적인 문제점들을 살펴봅니다.

**강의 목표:**

*   AI 코딩 도구를 사용하여 웹 애플리케이션(투자 앱) 개발을 시도합니다.
*   사용자 인증, 주식 검색, 관심 목록 추가, 상세 정보 및 차트 보기 기능을 구현하는 것을 목표로 합니다.
*   각 AI 도구의 사용 과정과 그 결과를 통해 현재 AI 기반 개발의 가능성과 한계를 이해합니다.

**사전 준비:**

*   각 AI 도구(Repl.it Agent, Vercel v0, Vault.new, Lovable) 웹사이트 접근 및 계정 생성 (유료 플랜 필요 가능성 있음)
*   웹 브라우저

---

**본론: AI 도구를 이용한 투자 앱 개발 시도**

**1단계: 목표 애플리케이션 정의**

우리가 만들고자 하는 앱은 사용자가 다음 기능을 사용할 수 있는 투자 앱입니다.

*   이메일과 비밀번호를 사용한 계정 생성 및 로그인
*   주식 검색 (종목명 또는 심볼 사용)
*   검색한 주식을 관심 목록(Watchlist)에 추가
*   관심 목록 페이지에서 등록된 주식들의 상세 정보 (가격, 차트, 회사 정보) 확인

**2단계: Repl.it Agent 사용 시도 ($25/월 또는 $180/연)**

1.  **Repl.it Agent 접속 및 프롬프트 입력:**
    *   Repl.it Agent 웹사이트에 접속합니다.
    *   다음과 같은 요구사항을 명확히 작성하여 프롬프트를 입력합니다: "주식 추적 앱을 만들고 싶습니다. 사용자는 이메일과 비밀번호로 계정을 생성할 수 있어야 합니다. 주식을 검색하고 관심 목록에 추가할 수 있어야 하며, 관심 목록 페이지에서는 주식의 차트, 가격, 회사 정보를 볼 수 있어야 합니다."
    *   (선택 사항) "Improve prompt" 기능을 사용하여 프롬프트를 더 구체화합니다.
    *   AI가 코드를 생성할 때까지 기다립니다.

2.  **초기 결과 확인 및 테스트 (회원가입 및 로그인):**
    *   AI가 기본적인 앱 구조와 회원가입/로그인 폼을 생성합니다.
    *   **테스트:** 이메일, 비밀번호, 비밀번호 확인을 입력하여 회원가입을 시도합니다. (성공)
    *   **테스트:** 생성된 계정으로 로그인을 시도합니다. (초기 에러 발생 후, AI가 수정하여 로그인 성공)

3.  **주식 검색 기능 테스트 및 문제 발생:**
    *   로그인 후 주식 검색 기능을 테스트합니다. (예: "net" 또는 "Cloudflare" 검색)
    *   **문제:** 검색 시 에러가 발생하거나 결과가 나오지 않습니다.
    *   **AI에게 문제 보고:** "회원가입과 로그인은 되지만, 주식을 검색할 수 없습니다."라고 피드백을 제공합니다.

4.  **주식 검색 문제 해결 시도 (API 문제 식별 및 수정 요청):**
    *   AI가 코드를 수정한 후 다시 로그인을 시도합니다.
    *   **테스트:** 다시 주식 검색을 시도합니다. (예: "net")
    *   **문제 식별:** 검색 결과가 나오지만, 실제 API를 사용하는 것이 아니라 미리 정의된(하드코딩된) 몇 개의 주식 정보만 반환하는 것을 발견합니다. (자막에서는 "stock API" 코드를 확인하여 이를 발견)
    *   **API:** Application Programming Interface의 약자로, 프로그램들이 서로 상호작용하는 것을 도와주는 매개체입니다. 여기서는 주식 데이터를 가져오기 위한 인터페이스를 의미합니다.
    *   **AI에게 구체적인 API 사용 요청:** "모든 주식을 검색할 수 있도록 Yahoo Finance 같은 API를 사용해주세요." (`yfinance`는 Python 라이브러리 이름)
    *   AI가 코드를 수정할 때까지 기다립니다. (하드코딩된 주식 목록이 삭제되는 것을 확인)

5.  **`yfinance` 적용 후 재테스트 및 추가 문제 발생:**
    *   **테스트:** 다시 주식 검색을 시도합니다. (예: "net" 또는 "coinbase")
    *   **문제:** 여전히 주식 검색이 제대로 작동하지 않습니다. (자막에서는 결국 개발자가 수동으로 코드를 수정했다고 언급)
    *   **수동 개입:** (실제 강의에서는 여기서 개발자가 직접 코드를 수정했지만, 튜토리얼에서는 AI의 한계를 인지하는 단계로 넘어갑니다.)
    *   **가정:** 만약 `yfinance`를 사용하도록 코드가 (수동 또는 AI에 의해) 수정되었다면, 다음과 유사한 Python 코드가 포함될 수 있습니다.
        ```python
        # 이 코드는 AI가 생성했거나, 수동으로 추가해야 할 수 있는 예시입니다.
        import yfinance as yf

        def search_stock(ticker):
            try:
                stock = yf.Ticker(ticker)
                # stock.info 또는 다른 필요한 정보를 반환
                return stock.info 
            except Exception as e:
                print(f"Error searching for {ticker}: {e}")
                return None
        ```

6.  **관심 목록 기능 테스트 및 에러 발생:**
    *   주식 검색이 (부분적으로) 작동한다고 가정하고, 검색된 주식(예: "net", "nflx")을 관심 목록에 추가합니다.
    *   **문제:** 관심 목록 페이지로 이동하거나 목록을 보려고 할 때 또 다른 에러가 발생합니다.
    *   **AI에게 에러 보고:** 발생한 에러 메시지를 복사하여 AI에게 붙여넣고 수정을 요청합니다.
    *   AI가 데이터베이스 저장 로직 및 차트 표시 (Matplotlib 사용 언급) 관련 코드를 수정합니다.

7.  **Repl.it Agent 결과 요약:**
    *   회원가입, 로그인은 가능했으나 주식 검색 및 관심 목록 기능에서 심각한 버그 발생.
    *   실제 데이터 연동(API 사용)에 어려움을 겪음.
    *   AI의 자동 수정 기능이 느리고 완벽하지 않아, 결국 사용자가 직접 코드를 수정해야 하는 상황 발생. 부분적으로 작동하지만 사용자가 실제 사용하기에는 부족한 수준.

**3단계: Vercel v0 사용 시도 ($20/월)**

1.  **v0 접속 및 프롬프트 입력:**
    *   Vercel v0 웹사이트에 접속합니다.
    *   Repl.it Agent와 유사한 프롬프트를 입력하되, 기술 스택을 명시합니다: "Next.js, Tailwind CSS, Yahoo Finance API를 사용하여 투자 앱을 만들어주세요."
    *   **Next.js:** React 기반의 웹 프레임워크로, 서버 사이드 렌더링 및 정적 사이트 생성 등 기능을 제공합니다.
    *   **Tailwind CSS:** 유틸리티 클래스 기반의 CSS 프레임워크로, HTML 내에서 직접 스타일을 빠르게 적용할 수 있게 합니다.
    *   AI가 코드를 생성할 때까지 기다립니다.

2.  **초기 결과 확인 (UI 및 기능 부재):**
    *   로그인 및 회원가입 폼 UI가 생성됩니다.
    *   **문제:** v0는 자체 데이터베이스 기능을 제공하지 않으므로, 회원가입/로그인 버튼을 클릭해도 아무런 동작도 하지 않습니다.
    *   **데이터베이스(DB):** 체계화된 데이터의 모음으로, 정보를 저장, 검색, 관리하는 시스템입니다. 사용자 계정 정보 등을 저장하는 데 필요합니다.

3.  **대시보드 접근 시도 및 에러 발생:**
    *   주소창에 `/dashboard`를 입력하여 대시보드 페이지로 직접 접근을 시도합니다.
    *   **문제:** 대시보드 페이지에서 에러가 발생합니다.
    *   **AI에게 문제 보고:** "Fix with v0" 버튼을 클릭하여 AI에게 에러 수정을 요청합니다.
    *   AI가 코드를 수정하지만, 다시 대시보드에 접근해도 여전히 에러가 발생합니다. ("Retry" 시도도 실패)

4.  **새 프로젝트 생성 및 재시도:**
    *   기존 프로젝트의 문제일 수 있다고 판단하여, 동일한 프롬프트로 완전히 새로운 프로젝트를 생성합니다.
    *   **결과:** 거의 동일한 코드가 생성됩니다.

5.  **새 프로젝트 테스트 (가짜 데이터 확인):**
    *   새 프로젝트의 `/dashboard`에 접근합니다. 몇 가지 주식 항목이 보입니다.
    *   **테스트:** "Cloudflare"를 검색해봅니다. (결과 없음)
    *   **테스트:** 목록에 있는 "Apple"을 클릭합니다. 차트가 표시되지만, 실제 데이터가 아닌 가짜 데이터(placeholder)로 보입니다.
    *   **AI에게 기능 개선 요청:** "주식 심볼을 사용해서 검색할 수 있도록 해주세요. Yahoo Finance npm 패키지를 사용해야 합니다."

6.  **기능 개선 시도 실패:**
    *   AI가 `yahoo-finance` 패키지를 인지하고 코드를 재작성하는 것처럼 보이지만, 실제로는 관련 기능이 제대로 구현되지 않습니다.
    *   **테스트:** 다시 `/dashboard`에 접근하면 이전과 동일한 에러가 다시 발생합니다.

7.  **Vercel v0 결과 요약:**
    *   프론트엔드 UI 생성은 가능했으나, 백엔드(데이터베이스 연동, 실제 API 호출) 기능 구현에 실패.
    *   에러 수정 능력이 부족하고, 가짜 데이터를 실제 데이터로 대체하지 못함. 최종적으로 사용 불가능한 결과물 생성.

**4단계: Vault.new 사용 시도 (무료 플랜 및 유료 토큰 플랜 시작 $20/월)**

1.  **Vault.new 접속 및 프롬프트 입력:**
    *   Vault.new 웹사이트에 접속합니다. (Supabase 통합 기능 언급됨)
    *   **Supabase:** 오픈 소스 Firebase 대안으로, 데이터베이스, 인증, 스토리지 등 백엔드 기능을 제공합니다.
    *   이전과 동일한 프롬프트를 입력합니다.
    *   AI가 Next.js 프로젝트 설정, 관련 라이브러리(Radix UI - Shadcn UI의 기반) 설치, 페이지(auth, dashboard, symbol) 생성을 진행합니다.

2.  **초기 결과 확인 및 테스트:**
    *   홈페이지(`/`)는 기본 프롬프트 입력 화면만 표시됩니다. (인덱스 페이지 미생성)
    *   `/dashboard` 페이지로 이동하여 주식 검색 기능을 테스트합니다.
    *   **테스트:** "net"을 검색합니다.
    *   **문제:** 주식 검색 시 즉시 에러가 발생합니다.

3.  **에러 수정 시도 실패:**
    *   AI에게 에러 수정을 요청합니다.
    *   AI가 전체 페이지 코드를 다시 작성하는 등 여러 번 시도하지만, 결국 에러를 해결하지 못합니다.

4.  **Vault.new 결과 요약:**
    *   Supabase 통합 등 잠재력은 보였으나, 핵심 기능인 주식 검색에서 발생한 초기 에러를 해결하지 못하고 실패.

**5단계: Lovable 사용 시도 (무료 평가판 및 유료 플랜 시작 $20/월)**

1.  **Lovable 접속 및 프롬프트 입력:**
    *   Lovable 웹사이트에 접속합니다. (Supabase 통합 기능 언급됨)
    *   동일한 프롬프트를 입력합니다.
    *   AI가 `yahoo-finance` 패키지 설치 필요성을 인지하고 진행합니다.
    *   Next.js가 아닌 다른 방식(아마도 기본적인 React 또는 다른 프레임워크)으로 앱 구조를 생성합니다. (`App.tsx` 파일 생성 언급)

2.  **빌드 에러 발생 및 수정:**
    *   AI가 페이지들(dashboard 등)을 생성하는 과정에서 빌드 에러 발생 ("Build unsuccessful").
    *   **AI에게 문제 보고:** 에러 수정을 요청합니다.
    *   AI가 에러를 수정하고 빌드에 성공합니다. 로그인 페이지 등이 나타납니다.

3.  **UI 문제 발생:**
    *   **문제:** 잠시 보였던 인덱스 페이지(초기 화면)가 갑자기 사라지는 등 비정상적인 UI 동작이 발생합니다.
    *   사용자는 무엇을 해야 할지 모르는 상황에 처합니다. ("I can't see anything"이라고 피드백)

4.  **Lovable 결과 요약:**
    *   `yahoo-finance` 필요성을 인지하고 Supabase 통합을 시도하는 등 긍정적인 면도 있었으나, 빌드 에러와 예측 불가능한 UI 문제로 인해 결국 사용 가능한 결과물을 만들지 못함.

---

**결론: AI 기반 개발의 현주소**

강의 영상의 시도 결과, 현재의 주요 AI 코딩 도구들은 **단독으로 복잡한 애플리케이션(간단한 To-Do 리스트 이상)을 처음부터 끝까지 완벽하게 구축하는 데는 한계**가 있었습니다.

*   **최종 결과물:** 어떤 도구도 사용자가 실제 사용할 만한 수준의 버그 없는 투자 앱을 완성하지 못했습니다. Repl.it Agent가 가장 근접했지만, 여전히 많은 문제와 수동 개입이 필요했습니다.
*   **과정의 어려움:** AI가 코드를 생성하고 수정하는 동안 사용자는 계속 기다려야 했으며, AI가 에러를 제대로 해결하지 못하거나 루프에 빠지는 경우 좌절감을 느꼈습니다. 이는 코드를 직접 작성하는 것보다 비효율적일 수 있습니다.
*   **AI의 역할:** 현재 AI는 개발자를 완전히 대체하기보다는, **개발자의 생산성을 높이는 보조 도구**로서의 역할이 더 적합해 보입니다. 특정 기능 구현(예: CSS 스타일링, 간단한 함수 작성)이나 프로토타입(MVP - Minimum Viable Product) 제작에는 도움을 줄 수 있지만, 전체 애플리케이션 아키텍처 설계, 복잡한 버그 디버깅, 실제 데이터 연동 등에는 여전히 숙련된 개발자의 개입이 필수적입니다.
*   **긍정적인 측면:** AI 덕분에 아이디어를 빠르게 프로토타입으로 만들 가능성이 열렸고, 이렇게 생성된 코드나 프로토타입을 기반으로 실제 개발자들이 개선하고 확장하는 새로운 기회가 생길 수 있습니다. 또한, 코드 생성 속도가 빨라짐에 따라 더 많은 코드가 생산되고, 이는 유지보수 및 버그 수정 수요 증가로 이어져 개발자에게 또 다른 기회가 될 수 있습니다.

결론적으로, AI 코딩 도구는 강력하지만 만능은 아닙니다. 개발자는 AI를 효과적으로 활용하여 생산성을 높일 수 있지만, 여전히 핵심적인 문제 해결 능력과 깊이 있는 프로그래밍 지식은 중요합니다.