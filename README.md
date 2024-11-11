# Secrets-detection

## Secrets-detection:

The “Secret Detection” tool was developed with the aim of checking secret leaks during the pipeline. Created to simplify this process, the tool stands out for its efficiency in analyzing the repository and with its regex, representing the result intuitively through a JSON report.

## How to run:

### GitLab

```bash
stages:
  - secret-detection

secrets_scan:
  stage: secret-detection
  image: python:3.13.0
  script:
    - python3 -m venv venv  # Cria um ambiente virtual
    - source venv/bin/activate  # Ativa o ambiente virtual
    - pip install --upgrade pip  # Atualiza o pip no ambiente virtual
    - pip uninstall -y secrets-detection  # Desinstala a versão anterior
    - pip install --upgrade --no-cache-dir secrets-detection==0.1.3  # Instala a versão desejada do pacote
    - scan-secrets  # Executa o script de análise de segredos
  artifacts:
    paths:
      - secrets_report.json  # Salva o relatório gerado
```

