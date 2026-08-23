# Projeto Final — Análise Exploratória de Consultas Médicas (No-Show)
### Disciplina: DS-PY-004 — Técnicas de Programação I (Python)

Este repositório contém o projeto final de análise exploratória de dados desenvolvido em grupo. O objetivo principal é investigar os fatores operacionais, clínicos e socioeconômicos que influenciam o absenteísmo em consultas médicas.

---

## 📊 A Base de Dados
A base escolhida foi o dataset público **"Medical Appointment No Shows"** (originalmente hospedado no Kaggle), que reúne informações de mais de **110.000 consultas médicas reais** realizadas no estado do Espírito Santo, Brasil.

### Recorte Temporal e Escopo
Os dados compreendem agendamentos e consultas ocorridos no ano de 2016. Cada linha representa uma consulta marcada e indica se o paciente compareceu ou faltou.

### Dicionário de Dados Inicial
*   **PatientId:** Identificação única do paciente.
*   **AppointmentID:** Identificação única da consulta.
*   **Gender:** Gênero do paciente (F ou M).
*   **ScheduledDay:** O dia em que a consulta foi marcada no sistema.
*   **AppointmentDay:** O dia real em que a consulta deveria acontecer.
*   **Age:** Idade do paciente.
*   **Neighbourhood:** O bairro onde a clínica ou hospital está localizado.
*   **Scholarship:** Indica se o paciente é beneficiário do programa social Bolsa Família (0 para Não, 1 para Sim).
*   **Hipertension / Diabetes / Alcoholism:** Colunas binárias indicando a presença dessas condições clínicas.
*   **Handcap:** Indicador de acessibilidade do paciente.
*   **SMS_received:** Indica se o paciente recebeu mensagens de texto de lembrete (0 para Não, 1 para Sim).
*   **No-show:** Coluna alvo. Indica se o paciente faltou (**"Yes"**) ou compareceu (**"No"**).

---

## 🎯 Perguntas de Negócio (Definidas Antes da Análise)
Para direcionar a investigação com foco em tomadas de decisão para a gestão da saúde pública, dividimos o projeto em 3 grandes frentes, mapeadas individualmente para cada integrante do grupo:

1.  **[Integrante 1 - Nome Aqui]: O tempo de espera entre o agendamento e o dia da consulta é um fator determinante para o absenteísmo?**
    *   *Foco técnico:* Criação da coluna derivada `WaitTime` e análise de correlação estatística e temporal com o status de falta.
2.  **[Integrante 2 - Nome Aqui]: O envio de lembretes via SMS é eficaz para engajar o paciente, e essa eficácia varia de acordo com faixas etárias?**
    *   *Foco técnico:* Agrupamento de idades com `pd.cut` em blocos geracionais e cruzamento de matrizes usando `pivot_table`.
3.  **[Integrante 3 - Nome Aqui]: Pacientes em vulnerabilidade socioeconômica ou portadores de doenças crônicas possuem taxas de falta mais severas?**
    *   *Foco técnico:* Agregações estatísticas complexas com `groupby` unindo dados clínicos (`Diabetes`, `Hypertension`) e sociais (`Scholarship`).

---

## 🛠️ Como Reproduzir Este Projeto

### Pré-requisitos
Certifique-se de ter o Python 3.11 instalado na máquina. O projeto faz o uso do gerenciador de pacotes rápido `uv`.

### Passo a Passo
1. Clone o repositório público:
   ```bash
   git clone https://github.com
   ```
2. Acesse a pasta do projeto:
   ```bash
   cd Repositorio_Projeto_Caixaverso
   ```
3. Crie e ative o ambiente virtual com as dependências instaladas:
   ```bash
   uv venv
   # No Windows (PowerShell):
   .venv\Scripts\Activate.ps1
   # Instale os pacotes:
   uv pip install pandas numpy matplotlib seaborn openpyxl ipykernel
   ```
4. O conjunto de dados bruto deve estar localizado na pasta `dados/KaggleV2-May-2016.csv`.
5. Abra o VS Code e execute o arquivo `notebooks/analise.ipynb` utilizando o kernel `.venv`.
