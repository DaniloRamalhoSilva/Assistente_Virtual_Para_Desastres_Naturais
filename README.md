# 🌪️ Assistente Virtual para Desastres Naturais – Arquitetura RAG

Um sistema inteligente de suporte a vítimas, moradores e familiares em situações de desastres naturais, com respostas claras, empáticas e contextualizadas, utilizando modelos de linguagem (LLMs) e recuperação de informação semântica.

---

## 📌 Sobre o Projeto

Este projeto foi desenvolvido como parte da disciplina de IA Generativa e Redes Avançadas, com o objetivo de aplicar a arquitetura **RAG (Retrieval-Augmented Generation)** na construção de um **assistente virtual inteligente** para situações críticas como enchentes, incêndios, deslizamentos e outros desastres naturais.

---

## 🎯 Objetivos

- Aplicar a arquitetura RAG para enriquecer as respostas de um chatbot com **informações externas atualizadas**.
- Utilizar **modelos de linguagem da OpenAI** via API para gerar respostas empáticas e personalizadas.
- Simular situações reais com diferentes **perfis de usuários** (vítima, morador, familiar).
- Refletir sobre os **impactos éticos e sociais** do uso de assistentes virtuais em contextos de risco.

---

## 🧠 Arquitetura Implementada

### 🔹 Retrieval
- **Fontes locais**: documentos `.docx` com manuais, orientações da Defesa Civil e protocolos de segurança.
- **Vector Store**: estrutura semântica com embeddings gerados por `OpenAIEmbeddings`, armazenados em `InMemoryVectorStore`.
- **Pré-processamento**: divisão de textos em `chunks` com sobreposição, usando `RecursiveCharacterTextSplitter`.

### 🔹 Augmented Generation
- **Modelo**: `gpt-4o-mini`, acessado via `LangChain`.
- **Prompting personalizado**: inclui o perfil do usuário, previsão do tempo e contexto da situação.
- **Memória de conversa**: histórico de interações mantido por `ConversationBufferMemory`.

### 🔹 Contexto Dinâmico
- **API externa**: `wttr.in` para previsão do tempo atualizada e injeção no prompt como variável contextual.

---

## 👥 Perfis de Usuário

| Perfil     | Descrição                                                                 |
|------------|---------------------------------------------------------------------------|
| 🆘 Vítima   | Usuário em situação de perigo imediato. Recebe instruções de resgate e sobrevivência. |
| 🌧️ Morador | Mora em área afetada ou sob risco. Recebe alertas e instruções preventivas.   |
| 📞 Familiar | Busca por notícias de entes queridos. Recebe orientações para localizar e informar autoridades. |

---

## 💬 Exemplos de Interação

### 🎙️ Entrada (Vítima):
> **"Está tudo alagado e estou no telhado, o que devo fazer?"**

### 🤖 Resposta:
> Mantenha a calma. Acione os Bombeiros (193) ou Defesa Civil (199). Não tente nadar. Sinalize com objetos visíveis. Se possível, desligue a energia. Aguarde resgate em local seguro.

---

### 🎙️ Entrada (Morador):
> **"Está chovendo forte, moro em área de risco. O que faço?"**

### 🤖 Resposta:
> Fique alerta. Suba para um local seguro. Leve alimentos e documentos. Desligue a energia e evite áreas alagadas. Siga um plano de evacuação, se disponível.

---

### 🎙️ Entrada (Familiar):
> **"Minha mãe está em área alagada e não consigo contato. O que fazer?"**

### 🤖 Resposta:
> Tente contato via redes sociais ou 171 (mensagem gravada). Fale com vizinhos e autoridades locais. Não entre na área alagada. Sua segurança também é prioridade.

---

## 📚 Fontes de Informação

- 📄 Documentos locais (.docx) com protocolos de segurança civil.
- 🌐 API pública de previsão do tempo: [wttr.in](https://wttr.in).
- 🤖 Conhecimento pré-embutido do modelo LLM da OpenAI.

---

## 🧪 Testes Realizados

- Simulações com os três perfis principais em cenários como:
  - Enchente
  - Incêndio residencial
  - Comunicação interrompida com familiares
- As respostas foram avaliadas quanto a:
  - ✅ **Aderência** à informação recuperada
  - ✅ **Clareza emocional** e orientação prática
  - ✅ **Corretude** e segurança das instruções

---

## 🧩 Pontos de Melhoria

- 🔄 **Integração com APIs oficiais** (MapBiomas, Defesa Civil, Inmet) para alertas em tempo real.
- 📎 **Referência explícita às fontes** dos documentos usados em cada resposta.
- 🗺️ **Respostas multimodais** com mapas de risco e imagens de abrigos.
- 🖥️ **Interface acessível em Streamlit ou Gradio** para uso em dispositivos móveis.

---

## ⚖️ Considerações Éticas

> O assistente **não substitui os serviços de emergência oficiais**. Todas as respostas incluem disclaimers reforçando que, em situações críticas, a prioridade deve ser entrar em contato com bombeiros, Defesa Civil ou serviços médicos especializados.

---

## 📁 Estrutura do Projeto
```bash
📦 Assistente_Virtual_Para_Desastres_Naturais
├── README.md
├── Assistente_Virtual_Para_Desastres_Naturais.ipynb (colab)
├── GS_2025.01_2TIA_GENAI.docx (documento original do projeto)
├── Relatório Técnico.docx (Entregavel)
├── Relatório de Avaliação do Assistente Virtual RAG.docx 
└── docsw/
    ├── PortugalP1-4.docx
    ├── manualdeprimeirossocorros.docx
    ├── Manual-de-Gerenciamento-de-Desastres.docx
    ├── icrc_007_0870.docx
    ├── guia_preparacao_respostas_emergencia_saude_publica_inundacao.docx
    ├── cartilha-primeiros-socorros.docx
    ├── Cartilha_prevencao_de_desastres.docx
    └── cartilha_emergencias_desastres_compressed.txt

```
## 🚀 Execução
Suba o notebook no Google Colab. [(Assistente_Virtual_Para_Desastres_Naturais)](https://colab.research.google.com/drive/1p_5ZCDpaA8EDqkkxtN_ON4Ui_5yhqnbD?usp=sharing).  
Insira sua OpenAI API Key.  
Carregue os arquivos de documentos em /content/docsw.  
Execute as células sequencialmente.  
Interaja com o assistente diretamente via input().

## 👨‍🏫 Créditos
Desenvolvido como parte da disciplina GENAI – Geração de Soluções com IA, turma 2TIA – 2025.1.

Coordenado por: Prof. José Maia
- Autores: 
    - Danilo Ramalho Silva RM: 555183
    - João Vitor Pires da Silva RM: 556213
    - Israel Dalcin Alves Diniz RM: 554668
