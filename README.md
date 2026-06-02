<a href="https://ject.kr/project/10" align="middle">
<img alt="StudyTrip" src="https://github.com/user-attachments/assets/d0616b4b-924b-4c3d-87fa-a0359e68706f">
</a>

# 프로젝트 소개
<div align="justify">
많은 학습자가 중장기 목표를 세우고도 작심삼일로 끝나는 경험을 반복합니다. 할 일 앱에 목표를 적고, 타이머 앱으로 시간을 재고, 노트 앱에 기록을 남기는 파편화된 루틴 속에서 정작 <b>내가 얼마나 왔는지</b>는 확인하기 어렵습니다. 문제는 의지가 아닙니다. <b>목표와 오늘 할 일 사이의 연결이 끊겨 있기 때문입니다.</b> 큰 목표를 세워도 오늘 무엇을 해야 할지 막막하고, 하루를 열심히 보내도 전체 목표에서 내가 어디쯤 있는지 보이지 않습니다. 그 간극이 동기를 소진시키고, 결국 포기로 이어집니다.
<br></br>

<b>스터디트립(StudyTrip)</b>은 학습의 여정을 하나의 **여행**으로 재설계합니다. 큰 목표는 **여행**으로, 중간 목표는 **스탬프**로, 일일 할 일은 **미션**으로 나누어 추상적인 목표를 오늘 실행 가능한 단위로 구체화합니다. 학습 성향에 따라 코스형과 탐험형 중 하나를 선택할 수 있고, 여행을 완료하면 총 학습 시간, 세션 수, 연속 학습일이 담긴 리포트를 통해 과정의 흔적을 눈에 보이는 성과로 남길 수 있습니다. 스터디트립은 단순한 학습 관리 도구가 아니라,
**완주의 경험이 쌓이는 공간**입니다.
</div>

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Animals/T-Rex.png" alt="T-Rex" width="30" height="30" />&nbsp;기술 스택

### 백엔드
![image](https://github.com/user-attachments/assets/bae79e83-17b6-4ee7-a08f-7f8d1b758d1c)

### 인프라
![image](https://github.com/user-attachments/assets/ef524156-d51f-432c-936f-664ac880986a)

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/Fire.png" alt="Fire" width="30" height="30" />&nbsp;아키텍처
![image](https://github.com/user-attachments/assets/c2df546f-ae4d-4eb8-a90b-a2ee62f16fca)

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Microsoft-Teams-Animated-Emojis/master/Emojis/Smilies/Yellow%20Heart.png" alt="Yellow Heart" width="30" height="30" />&nbsp;핵심 기여
<details>
<summary><b>Java → Kotlin 점진적 마이그레이션 적용해 서비스 안정성 및 가독성 향상</b></summary>
<div markdown="1">

- 테스트 코드를 Kotlin으로 재작성 후, `Presentation → Application → Infrastructure → Domain` 계층 순으로 전환
- Kotlin의 null-safety, `val` 기반 불변성, `data class`, `object`를 적용해 도메인 모델의 안정성과 가독성 개선
- 기존 비즈니스 로직과 API 동작을 유지하면서, 중복 로직 및 미사용 레거시 코드 제거
- Java–Kotlin 혼용 환경의 정적 호출, `object` 패턴 상호운용 이슈를 고려한 마이그레이션 전략 수립
- 비즈니스 로직과 API 동작은 변경하지 않으면서, 코드베이스 `10%` 단축 (30,621 → 27,410 라인)

</div>
</details>

<details>
<summary><b>CQRS 패턴을 도입해 트랜잭션 처리 개선 및 Dirty Checking 문제 해결</b></summary>
<div markdown="1">

- 서비스가 점점 비대해지면서 조회와 변경 로직이 혼재되고, **트랜잭션이 분산 적용되어 경계가 불명확해지는 문제 발생**
- `@Transactional(readOnly = true)`가 적용된 메서드에서 조회한 엔티티가 **준영속** 상태로 전환
- 준영속 상태가 된 엔티티를 수정하거나 삭제할 때, `변경 감지(Dirty Checking)`가 작동하지 않는 문제 발생
- CQRS 패턴을 적용해 `Query Service(조회)`와 `Command Service(등록, 수정, 삭제)`로 책임을 명확히 분리
- 모든 서비스 계층에서 `@Transactional`을 제거하고, Facade 계층에서만 트랜잭션을 처리하도록 개선
- 트랜잭션 경계가 명확해지고, 준영속 상태로 인한 **Dirty Checking 문제 해결**

</div>
</details>

<details>
<summary><b>DDD 기반 백엔드 아키텍처 설계</b></summary>
<div markdown="1">

- `Application / Domain / Infrastructure / Presentation` 계층 분리로 구조적 책임 구분
- **Factory 패턴**: 도메인 객체 생성을 캡슐화해 도메인의 순수성과 일관성 유지
- **Facade 패턴**: 여러 도메인 서비스 호출을 하나의 진입점으로 통합하고 컨트롤러 역할 단순화
- **Adapter 패턴**: 외부 기술(JPA, OpenAPI)을 도메인 인터페이스에 연결해 도메인과 기술 구현 분리

</div>
</details>

<details>
<summary><b>테스트 전략 수립 및 설계 품질 개선</b></summary>
<div markdown="1">

- `JUnit5`, `Mockito` 기반 Service 단위 테스트로 비즈니스 로직 및 예외 흐름 검증
- `SpringBootTest`, `MockMvc` 기반 Controller 통합 테스트로 인증 → 실패 → 성공 시나리오 검증
- **Fixture / Helper** 도입으로 테스트 데이터 생성을 표준화하고 중복 제거
- 코드 리뷰에서 테스트 범위와 책임 분리를 점검하고, 테스트 코드 기반으로 설계 품질을 지속적으로 개선

</div>
</details>
