# GitHub Actions

GitHub Actions es una plataforma de integración y despliegue continuo (CI/CD) que permite automatizar procesos como compilación, pruebas y despliegue directamente en GitHub.

## Conceptos clave

### **¿Qué es GitHub Actions?**
Es una plataforma que facilita la creación de flujos de trabajo automatizados para manejar eventos en tu repositorio, como commits, solicitudes de extracción, y más.

### **¿Qué es un Workflow?**
Un workflow es un proceso automatizado configurable que ejecuta uno o más *jobs*. Se define en un archivo YAML dentro del directorio `.github/workflows` de tu repositorio y se activa mediante un evento específico.

### **¿Qué es un Event?**
Un evento es una actividad específica en un repositorio, como un push o la apertura de un pull request, que activa la ejecución de un workflow.

### **¿Qué es un Job?**
Un job es un conjunto de tareas (*steps*) dentro de un workflow que se ejecutan en el mismo *runner*.

### **¿Qué es un Runner?**
Un *runner* es un servidor que ejecuta los workflows. GitHub proporciona runners con entornos preconfigurados en Ubuntu, Windows y macOS. También puedes usar runners auto-hospedados.

### **¿Qué es un Step?**
Un *step* es una unidad de ejecución dentro de un job. Puede ser:
- Un script o comando de shell.
- Una acción (*action*) predefinida o personalizada.

### **¿Qué es un Action?**
Una *action* es una aplicación personalizada que realiza tareas complejas o repetitivas dentro de un workflow.

---

## Principales Triggers

Los triggers son eventos que activan la ejecución de un workflow. Algunos de los más comunes son:

- **`push`**: Cuando se realiza un commit en el repositorio.
- **`pull_request`**: Cuando se abre, actualiza o cierra una solicitud de extracción (*pull request*).
- **`issues`**: Cuando se abre, cierra o actualiza un issue.
- **`issue_comment`**: Cuando se comenta en un issue.
- **`workflow_dispatch`**: Permite ejecutar workflows manualmente desde la interfaz de GitHub.
- **`schedule`**: Ejecuta workflows en un horario predefinido (cron jobs).

---

## Ejemplo básico de un Workflow

```yaml
name: CI/CD Pipeline

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3
      
      - name: Run tests
        run: echo "Running tests..."
      
      - name: Deploy
        run: echo "Deploying application..."