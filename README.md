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
    - |
      if pip show secrets-detection > /dev/null 2>&1; then
        echo "Pacote 'secrets-detection' encontrado, desinstalando..."
        pip uninstall -y secrets-detection
      else
        echo "Pacote 'secrets-detection' não encontrado, prosseguindo com a instalação."
      fi
    - python3 -m venv venv  
    - source venv/bin/activate 
    - pip install --upgrade pip  
    - pip install --upgrade --no-cache-dir secrets-detection
    - scan-secrets  
    - deactivate  
  artifacts:
    paths:
      - secrets_report.json
```

