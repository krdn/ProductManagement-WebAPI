# 제품 관리 API

ASP.NET Core 8.0과 Entity Framework Core를 사용하여 개발된 제품 관리 RESTful API입니다.

## 프로젝트 개요

이 프로젝트는 제품 정보를 관리하기 위한 API를 제공합니다. CRUD(Create, Read, Update, Delete) 작업을 지원하며, MS SQL Server를 데이터 저장소로 사용합니다.

## 기술 스택

- **백엔드**:
  - ASP.NET Core 8.0
  - Entity Framework Core 8.0
  - C# 12
- **데이터베이스**:
  - MS SQL Server
- **API 문서화**:
  - Swagger/OpenAPI
- **아키텍처**:
  - 레이어드 아키텍처(Layered Architecture)
  - 의존성 주입(Dependency Injection)
  - 리포지토리 패턴(Repository Pattern)

## 프로젝트 구조

```
ProductManagement-WebAPI/
├── Controllers/          # API 컨트롤러
├── Models/               # 도메인 모델 클래스
├── Data/                 # 데이터 액세스 레이어
├── Services/             # 비즈니스 로직 서비스
├── appsettings.json      # 애플리케이션 설정
├── Program.cs            # 애플리케이션 진입점
└── ProductApi.csproj     # 프로젝트 파일
```

## API 엔드포인트

| 엔드포인트 | 메서드 | 설명 |
|------------|--------|------|
| `/api/products` | GET | 모든 제품 목록 조회 |
| `/api/products/{id}` | GET | 특정 ID의 제품 조회 |
| `/api/products` | POST | 새 제품 추가 |
| `/api/products/{id}` | PUT | 특정 ID의 제품 업데이트 |
| `/api/products/{id}` | DELETE | 특정 ID의 제품 삭제 |

## 설치 및 실행 방법

### 필수 조건

- [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [MS SQL Server](https://www.microsoft.com/ko-kr/sql-server/sql-server-downloads)

### 설치 단계

1. 저장소를 클론합니다:
   ```bash
   git clone https://github.com/krdn/ProductManagement-WebAPI.git
   cd ProductManagement-WebAPI
   ```

2. 데이터베이스 연결 문자열을 설정합니다:
   `appsettings.json` 파일에서 `ConnectionStrings` 섹션의 `DefaultConnection`을 사용자의 MS SQL Server 환경에 맞게 수정합니다.

3. 데이터베이스 마이그레이션을 실행합니다:
   ```bash
   dotnet ef migrations add InitialCreate
   dotnet ef database update
   ```

4. 애플리케이션을 실행합니다:
   ```bash
   dotnet run
   ```

5. 브라우저에서 Swagger UI를 통해 API를 테스트합니다:
   ```
   https://localhost:5001/swagger
   ```

## 주요 기능

1. **제품 목록 조회**: 모든 제품 목록을 JSON 형식으로 반환합니다.
2. **제품 상세 조회**: 특정 ID의 제품 정보를 반환합니다.
3. **제품 추가**: 새로운 제품을 데이터베이스에 추가합니다.
4. **제품 업데이트**: 기존 제품 정보를 업데이트합니다.
5. **제품 삭제**: 특정 제품을 데이터베이스에서 삭제합니다.

## 에러 처리

API는 적절한 HTTP 상태 코드와 오류 메시지를 반환하여 클라이언트에게 유용한 피드백을 제공합니다:

- `400 Bad Request`: 요청 본문이 유효하지 않은 경우
- `404 Not Found`: 요청한 리소스를 찾을 수 없는 경우
- `500 Internal Server Error`: 서버 내부 오류가 발생한 경우

## 보안 고려사항

이 프로젝트는 데모용이므로 프로덕션 환경에서 사용하기 전에 다음 보안 기능을 추가해야 합니다:

- JWT 인증 및 권한 부여
- HTTPS 적용
- 입력 유효성 검사 강화
- 민감한 데이터 암호화
- 요청 제한(Rate Limiting)

## 확장 가능성

이 프로젝트는 다음과 같은 방향으로 확장할 수 있습니다:

- 사용자 인증 및 권한 부여 추가
- 다국어 지원
- 캐싱 계층 추가
- 제품 카테고리 및 태그 관리
- 파일 업로드 기능(제품 이미지 등)
- 로깅 및 모니터링 강화
- 단위 테스트 및 통합 테스트 추가

## 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하세요.

## 문의 및 기여

질문이나 기여하고 싶은 사항이 있다면 이슈를 생성하거나 풀 리퀘스트를 보내주세요.