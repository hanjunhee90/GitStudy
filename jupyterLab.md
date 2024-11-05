## Conda 가상 환경 설정 및 Jupyter 연동

### 1. Conda 가상 환경 생성

Conda를 사용하여 특정 이름과 Python 버전으로 가상 환경을 생성할 수 있습니다.

```bash
conda create -n <가상환경_이름> python=<파이썬_버전>
```

- **예시:**

```bash
conda create -n tech7 python=3.9.0
```

이 명령어는 `tech7`이라는 이름의 가상 환경을 Python 3.8.0 버전으로 생성합니다.

---

### 2. 가상 환경 활성화

가상 환경을 생성한 후, 아래 명령어로 가상 환경을 활성화할 수 있습니다.

```bash
conda activate <가상환경_이름>
```

- **예시:**

```bash
conda activate tech7
```

---

### 3. `ipykernel` 설치

가상 환경이 활성화된 상태에서, Jupyter에서 사용하기 위해 `ipykernel`을 설치합니다.

```bash
conda install ipykernel
```

---

### 4. Jupyter에 가상 환경 추가

Jupyter 노트북에서 가상 환경을 사용하려면 아래 명령어를 사용해 해당 환경을 Jupyter에 등록합니다.

```bash
python -m ipykernel install --user --name <가상환경_이름> --display-name "<표시_이름>"
```

- **예시:**

```bash
python -m ipykernel install --user --name tech7 --display-name "tech7"
```

- `--name <가상환경_이름>`: Conda에서 사용할 가상 환경의 이름을 지정합니다.
- `--display-name "<표시_이름>"`: Jupyter의 커널 목록에서 보일 이름을 지정합니다.

---

### 5. 가상 환경 비활성화

작업을 완료한 후에는 가상 환경을 비활성화할 수 있습니다.

```bash
conda deactivate
```

---

### 6. Jupyter Lab 실행

가상 환경을 Jupyter에서 사용하려면, Jupyter Lab을 실행합니다.

```bash
jupyter lab
```
