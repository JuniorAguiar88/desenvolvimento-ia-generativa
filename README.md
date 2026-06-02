# 🤖 Desenvolvendo Software com IA Generativa

> Repositório de estudos e projetos práticos da disciplina **Desenvolvendo Software com IA Generativa** — Módulo 4 (18h)

## 📋 Sobre

Este repositório contém os notebooks e projetos desenvolvidos durante o curso, cobrindo desde fundamentos de LLMs até deploy em produção. Cada dia (Day-1, Day-2, Day-3) possui seus próprios materiais e laboratórios práticos.

## 🚀 Projetos

### 📘 Day-1: Fundamentos de LLM + Tool-use

**Notebook:** [`01_agent_cli_tool_use_jose_wilson_aguiar_junior.ipynb`](./01_agent_cli_tool_use_jose_wilson_aguiar_junior.ipynb)

Um **agente CLI inteligente** que decide automaticamente quando:
- Responder diretamente (pure-prompt)
- Chamar ferramentas externas (tool-use)

#### 🎯 Funcionalidades

| Tool | Descrição | Quando é usada |
|------|-----------|----------------|
| `get_weather` | Consulta clima de uma cidade | Perguntas sobre temperatura/previsão |
| `calculator` | Calculadora exata | Operações aritméticas > 2 dígitos |
| `get_current_time` | Data/hora com fuso horário | Perguntas sobre hora atual |

#### 🧪 Exemplos de uso

```
👤 Você: que horas são em Manaus?
🔧 Tool call: get_current_time
   📥 Args: {"timezone": "America/Manaus"}
   📤 Result: {'horario': '15:58:21', 'offset': '-0400', ...}
🤖 Assistente: São 15:58:21 no horário de Manaus (UTC-4).

👤 Você: Quanto é 12345 * 67890?
🔧 Tool call: calculator
   📤 Result: 838102050
🤖 Assistente: O resultado é 838.102.050.

👤 Você: O que é um LLM?
💬 Pure-prompt (sem tool)
🤖 Assistente: LLM significa Large Language Model...
```

## 🛠️ Tecnologias

- **Python 3.12**
- **Groq API** (gratuita) — modelo `llama-3.3-70b-versatile`
- **OpenAI SDK** (compatibilidade)
- **Pydantic** — validação de schemas
- **Rich** — interface CLI colorida
- **pytz** — suporte a fusos horários

## ⚙️ Como executar

### 1. Clone o repositório

```bash
git clone https://github.com/JuniorAguiar88/desenvolvimento-ia-generativa.git
cd desenvolvimento-ia-generativa
```

### 2. Instale as dependências

```bash
pip install openai pydantic rich pytz python-dotenv
```

### 3. Configure sua API Key

Crie uma conta gratuita no [Groq](https://console.groq.com/keys) e obtenha sua API Key.

No notebook, substitua na Célula 2:

```python
GROQ_API_KEY = "gsk_SUA_CHAVE_AQUI"
```

### 4. Execute o notebook

Abra no Jupyter, VS Code ou Google Colab e execute as células em ordem.

## 📊 Resultados do LAB-001

### Tabela Comparativa: Pure-prompt vs Tool-use

| Query | Pure-prompt | Tool-use | Vencedor |
|-------|-------------|----------|----------|
| Que horas são? | Alucina ou diz que não sabe | ✅ Retorna horário exato | **Tool-use** |
| Clima em SP? | Dado desatualizado (cutoff) | ✅ Dado atualizado | **Tool-use** |
| 12345 * 67890? | Erra ~10% em aritmética | ✅ Resultado exato | **Tool-use** |
| O que é um LLM? | ✅ Resposta natural | Overhead desnecessário | **Pure-prompt** |
| Explique tool-use | ✅ Explicação direta | Sem ganho | **Pure-prompt** |

### Lição principal

> **Tool-use não substitui o LLM — ele estende o LLM.**
> O modelo continua responsável por entender a intenção do usuário
> e decidir QUAL tool chamar (ou nenhuma).

## 🏗️ Estrutura do Repositório

```
.
├── README.md
├── 01_agent_cli_tool_use_jose_wilson_aguiar_junior.ipynb
└── (futuros notebooks dos Days 2 e 3)
```

## 🎓 Desafios Superados

- ✅ Integração com Groq API (alternativa gratuita à OpenAI)
- ✅ Tratamento de argumentos `None` em tool calls
- ✅ Compatibilidade com campos não suportados (`annotations`)
- ✅ Conversão correta de fusos horários com `pytz`

## 📅 Próximos Passos

- [ ] **Day-2**: RAG End-to-End + Evaluation
- [ ] **Day-3**: Deploy em produção com custo controlado

## 👤 Autor

**José Wilson Aguiar Junior**  
Estudante de Desenvolvimento de Software com IA Generativa

- GitHub: [@JuniorAguiar88](https://github.com/JuniorAguiar88)

## 📄 Licença

Este projeto é destinado exclusivamente para fins educacionais.

---

<div align="center">
  <sub>Feito com 💙 durante a Residência em Inteligência Artificial - Instituto SiDi 2026</sub>
</div>
