# 🌐 Administração dos Recursos do Azure – Resumo AZ-104

## 🔷 Portal do Azure
Interface visual e intuitiva baseada na web.

- Permite ver, criar e gerenciar recursos de forma centralizada.
- Funciona como um hub unificado com acesso a:
  - Treinamentos, documentação e suporte.
  - Customização da experiência.
- Disponível também via aplicativo móvel.
- Permite o uso do **Cloud Shell** diretamente no navegador.

---

## 💻 Azure Cloud Shell

- Localizado no topo do portal com o ícone `>_`.
- Shell interativo baseado em navegador.

### Ambientes disponíveis:
- **Bash** (Linux)
- **PowerShell** (Windows)

### Características

| Item                     | Detalhes                                |
|--------------------------|------------------------------------------|
| Tempo de inatividade     | Expira após 20 minutos                   |
| Ferramentas pré-instaladas | Sim                                   |
| Editor de texto incluído | Sim                                     |
| Requisitos iniciais      | Storage Account, Resource Group, Share  |


---

## ⚙️ PowerShell e Cmdlets

### 📌 Cmdlets e Módulos
- Cmdlets seguem o padrão: `verbo-substantivo` (ex: `Get-Process`).
- Agrupados em **módulos** (DLLs).
- Use `Get-Module` para listar módulos carregados.

### 💠 Azure PowerShell
- Extensão do PowerShell com cmdlets para o Azure.
- Disponível via:
  - Cloud Shell
  - Instalação local (Windows, Linux, macOS)

### Modos de uso:
- Interativo (linha a linha)
- Script (automatizado)

### Requisitos:
- Instalar PowerShell base
- Instalar módulo Az:
  ```powershell
  Install-Module -Name Az
  ```
- Primeiro comando: `Connect-AzAccount`
  
## 💻 Azure CLI
- Interface de linha de comando multiplataforma:
- Compatível com Windows, macOS e Linux
- Funciona no Cloud Shell ou localmente
- Padrão de comandos:
```powershell
az <grupo> <subgrupo> <ação>
#Exemplo:
az vm restart -g MyResourceGroup -n MyVm
```
- Modos:
  - Interativo
  - Script
- Comandos úteis:
   - `az find` – procura comandos
   - `--help` – detalha opções e sintaxe

## 🛠️ Azure Resource Manager (ARM) – Modelos
- Arquivos JSON que definem infraestrutura e configurações.
- Vantagens:
   - Consistência, reutilização, validação e automação.
- Estrutura em pares chave-valor:
  - `parameters, variables, resources, outputs`
- Idempotente: Pode ser executado várias vezes sem duplicar recursos.

## 💡 Bicep – IaC Simplificado
- Linguagem declarativa da Microsoft (compila para ARM).
- Mais legível, curta e simples que JSON ARM.
-Recursos:
  - Módulos reutilizáveis
  - Validação automática
- Ideal para: Iniciantes ou Ambientes Microsoft
- ⚠️ Funciona apenas no Azure.
- 🔁 Para multi-cloud, use Terraform.

## 🧪 Implantação na Prática – Passo a Passo
### 📤 Exportar template de um recurso:
1. Acesse o recurso no Resource Group
2. Clique em Automation > Export template
3. Baixe template.json e parameters.json

### 🔁 Reimplantar via Portal:
1. Acesse Deploy a custom template
2. Clique em Build your own template in the editor
3. Carregue `template.json`
4. Edite e selecione parameters.json
5. Salve e clique em Deploy

### 🖥️ Reimplantar via PowerShell (Cloud Shell):
1. Vá em Manage files > Upload os arquivos `.json`
2. Use nano para editar os valores desejados
```powershell
# Execute:
New-AzResourceGroupDeployment -ResourceGroupName az104-rg2 
  -TemplateFile template.json 
  -TemplateParameterFile parameters.json
 ```
📊 Implantação via PowerShell foi cerca de 4 segundos mais rápida do que pelo portal.

## ✅ Revisão de Conceitos – Q&A

### ☁️ Cloud Shell

| Pergunta                                      | Resposta                                     |
|-----------------------------------------------|----------------------------------------------|
| Recebe várias máquinas por usuário?           | ❌ Errado – apenas uma VM por sessão         |
| Localização do Cloud Shell?                   | Topo do portal, ícone `>_`                  |
| Ambientes disponíveis?                        | Bash (Linux) e PowerShell (Windows)         |
| Requisitos iniciais?                          | Storage Account                             |
| Vantagem principal?                           | Rapidez e automação via linha de comando    |

### ⚙️ PowerShell e CLI

| Pergunta                                      | Resposta                                     |
|-----------------------------------------------|----------------------------------------------|
| Requisitos PowerShell local?                  | PowerShell base + módulo Az                 |
| Primeiro comando para autenticação?           | `Connect-AzAccount`                         |
| Ferramenta visual mais usada?                 | Portal do Azure                             |
| Quando usar CLI ou PowerShell?                | Tarefas repetitivas, automação e scripts    |

### 📦 Grupos de Recursos

| Pergunta                      | Resposta             |
|-------------------------------|----------------------|
| Parâmetros obrigatórios?      | Nome e Localização   |

### 🛠️ ARM & Bicep

| Pergunta                                      | Resposta                                     |
|-----------------------------------------------|----------------------------------------------|
| O que é um modelo ARM?                        | JSON que define infraestrutura do Azure     |
| Elemento inválido em template ARM?            | `Inputs`                                    |
| O que é idempotência?                         | Execução sem alterações adicionais          |
| Objetivo dos templates ARM?                   | Automatizar e padronizar implantações       |
| Export Template gera?                         | Template JSON + Parameters JSON             |

### 📘 Bicep

| Pergunta                                      | Resposta                                     |
|-----------------------------------------------|----------------------------------------------|
| Diferença entre Bicep e ARM?                  | Bicep é mais simples e legível              |
| Limitação do Bicep?                           | Só funciona no Azure                         |
| Ferramenta recomendada para edição?           | Visual Studio Code                           |
| Pode ser usado em multi-cloud?                | 🛑 Não – use Terraform                        |
| Ferramenta multi-cloud recomendada?           | Terraform                                    |
