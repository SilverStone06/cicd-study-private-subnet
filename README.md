# git-cicd-study-ssm-2

Private EC2(사설 서브넷)에 SSH 대신 AWS SSM으로 배포하는 GitHub Actions 파이프라인 리포지토리입니다. Docker Hub 이미지를 사용합니다.

## 워크플로우
- `fastapi-private.yml`: Docker Hub 로그인 → 이미지 빌드/푸시 → SSM으로 배포
- `nginx-private.yml`: Docker Hub 로그인 → 이미지 빌드/푸시 → SSM으로 배포

## 필요 시크릿
- `DOCKER_USERNAME`: Docker Hub 로그인에 사용하는 계정 아이디
- `DOCKER_PASSWORD`: Docker Hub 로그인용 액세스 토큰(또는 비밀번호)
- `AWS_ACCESS_KEY_ID`: 배포용 IAM 사용자의 액세스 키 ID
- `AWS_SECRET_ACCESS_KEY`: 배포용 IAM 사용자의 시크릿 액세스 키
- `AWS_REGION`: 리소스가 있는 AWS 리전(예: `ap-northeast-2`)
- `EC2_INSTANCE_ID`: 배포 대상 EC2 인스턴스 ID

## 주의
- 워크플로우는 `fastapi-private`, `nginx-private` 디렉터리가 있다고 가정합니다.
- 현재 리포에는 해당 디렉터리가 없어 빌드 단계가 실패할 수 있습니다.\n
