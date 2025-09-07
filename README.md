---

# 💡 IntelliCode Crew – AI-Driven Development

Welcome to **IntelliCode Crew** — a cutting-edge multi-agent AI system designed to **automate coding, debugging, and development tasks** efficiently. This project leverages the power of [crewAI](https://crewai.com) to orchestrate multiple intelligent agents that collaborate on programming projects, helping developers and teams achieve more in less time.

---

## 🛠️ Installation

### Requirements

* **Python**: `>=3.10` and `<3.14`
* **Dependency Manager**: [UV](https://docs.astral.sh/uv/)
* **Optional**: [Docker Desktop](https://docs.docker.com/desktop/) for safe code execution

### Step 1: Install UV

If not already installed, run:

```bash
pip install uv
```

### Step 2: Install Dependencies

Navigate to your project folder and install requirements:

```bash
uv pip install -r requirements.txt
```

Or, lock dependencies and install via the CLI:

```bash
crewai install
```

---

## ⚙️ Customization

Before running the crew, configure it to match your needs:

1. **Define agents**

   * `config/agents.yaml` → Define coder agents and capabilities

2. **Define tasks**

   * `config/tasks.yaml` → Define coding tasks your crew will execute

3. **Customize crew logic**

   * `crew.py` → Adjust agent behavior, execution limits, and tools

---

## 🐳 Docker Installation & Safe Code Execution

IntelliCode Crew supports **safe code execution** using Docker. This ensures your agents’ code runs securely without affecting your system.

### Step 1: Install Docker Desktop

* **Windows / Mac**:
  Download and install from [Docker Desktop](https://docs.docker.com/desktop/).

* **Linux**:
  Follow the official guide for your distro: [Install Docker Engine](https://docs.docker.com/engine/install/)

### Step 2: Verify Docker Installation

Run the following command to ensure Docker is installed correctly:

```bash
docker --version
```

You should see a version output, e.g.:

```
Docker version 24.0.2, build abc123
```

### Step 3: Enable Safe Code Execution in IntelliCode Crew

In `crew.py`, configure your agent with safe execution:

```python
@agent
def coder(self) -> Agent:
    return Agent(
        config=self.agents_config['coder'],
        verbose=True,
        allow_code_execution=True,
        code_execution_mode="safe",  # Uses Docker sandbox
        max_execution_time=120,
        max_retry_limit=5
    )
```

> **Notes:**
>
> * `code_execution_mode="safe"` runs all code in a Docker container
> * Adjust `max_execution_time` and `max_retry_limit` to control task execution limits

### Step 4: Run IntelliCode Crew

From the project root:

```bash
crewai run
```

Your coder agents will now execute code **safely inside Docker**, generating outputs without impacting your local environment.

---

## 🤝 Understanding Your Crew

The **IntelliCode Crew** is composed of specialized AI agents:

* Each agent has **roles, goals, and capabilities**
* Tasks are orchestrated through `config/tasks.yaml`
* Agents can **execute code**, retry failed tasks, and log outputs

This setup allows teams to **automate repetitive coding tasks** and speed up development cycles.

---

## 🚀 Key Features

* Multi-agent collaboration on coding tasks
* Safe code execution with Docker
* Configurable retry limits and execution time
* Seamless task orchestration (sequential or parallel)
* Verbose logging for transparency

---

✨ **Boost your productivity and coding efficiency with the collective intelligence of IntelliCode Crew – AI-Driven Development.**

---
