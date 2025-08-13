text
# Desafio DIO - Máquinas Virtuais no Azure via Python (Google Colab)

## 📃 Descrição
Projeto que demonstra a criação e configuração de uma **Máquina Virtual Windows no Microsoft Azure** utilizando **Python** no **Google Colab**, com automação via **SDK oficial do Azure**.  
Objetivo: consolidar conhecimentos sobre **máquinas virtuais na nuvem** e **documentação técnica no GitHub**, unindo teoria e prática.

***

## 🎯 Objetivos
- Criar uma VM Windows Server no Azure de forma totalmente automatizada.
- Utilizar Python e Google Colab para gerenciar recursos.
- Documentar passo a passo, com imagens e boas práticas, e publicar no GitHub.

***

## 📦 Tecnologias e Ferramentas
- **Microsoft Azure**
- **Python 3** (Google Colab)
- Bibliotecas:
  - `azure-identity`
  - `azure-mgmt-resource`
  - `azure-mgmt-network`
  - `azure-mgmt-compute`
- **Git & GitHub**
- **Markdown** para documentação.

***

## 🛠️ Pré-requisitos
- Conta ativa no Microsoft Azure.
- Criar **Service Principal** com permissões de **Contributor**:
az ad sp create-for-rbac --name "sp-colab" --role Contributor --scopes /subscriptions/<SEU_SUBSCRIPTION_ID>

text
- Guardar:
  - `SUBSCRIPTION_ID`
  - `TENANT_ID`
  - `CLIENT_ID`
  - `CLIENT_SECRET`
- Conta no GitHub.
- Nunca publique credenciais no GitHub (use variáveis de ambiente).
- Em produção, evite expor a porta 3389 na internet (prefira Azure Bastion ou VPN).

***

## 🚀 Passos para execução
1. Acesse o Google Colab: https://colab.research.google.com/
2. Crie um novo notebook e cole o script de criação da VM (com geração de imagens).
3. No início do script, preencha:
SUBSCRIPTION_ID = "xxxx"
TENANT_ID = "xxxx"
CLIENT_ID = "xxxx"
CLIENT_SECRET = "xxxx"

text
4. Execute todas as células.
5. Aguarde 2–5 minutos para criar a VM.
6. Anote o IP público exibido no final.
7. Conecte-se via RDP:
   - Endereço: `<IP_PUBLICO>:3389`
   - Usuário: o definido no script (ex.: azureuser)
   - Senha: a definida no script

***

## 📁 Estrutura de Pastas
📂 projeto-vm-azure
├── README.md
├── vm_azure_colab.ipynb (ou vm_azure_colab.py)
└── /images
├── 01-resumo-implantacao.png
├── 02-rede.png
├── 03-parametros-vm.png
└── 04-conexao-rdp.png

text

***

## 📸 Resultados
As imagens abaixo são geradas automaticamente pelo notebook:

**Resumo da implantação**  
![Resumo](images/01-resumo-implantacao.png)

**Recursos de rede**  
![Rede](images/02-rede.png)

**Parâmetros da VM**  
![Parâmetros](images/03-parametros-vm.png)

**Conexão RDP**  
![RDP](images/04-conexao-rdp.png)

***

## ⚠️ Cuidados
- Exclua os recursos após os testes para evitar custos:
resource_client.resource_groups.begin_delete("rg-lab-vm")

text
- Não exponha credenciais no repositório.
- Em produção, prefira Azure Bastion/VPN em vez de RDP aberto.

***

## 🧯 Troubleshooting
- Autenticação falhou: valide `CLIENT_ID`, `CLIENT_SECRET`, `TENANT_ID` e a permissão Contributor.
- Quota/capacidade: use `Standard_B1s` ou mude de região/solicite aumento de cota.
- IP público vazio: aguarde 1–3 min e reexecute a célula que consulta o IP.
- RDP sem conexão: confirme VM em “Running”, regra 3389 e firewall do SO.

***

## 🧭 Próximos Passos
- Repetir com VM Linux (SSH com chave).
- Adicionar scripts de pós-implantação (IIS/Apache).
- Refazer com Azure CLI ou Terraform para comparar IaC.

***

## 📚 Referências
- SDK Python do Azure
- Guia: Criar VM Windows no Azure (Portal)
- Markdown no GitHub

---

✍ Autor: Rone Bragaglia  
📍 Santo André - SP  
📅 Agosto/2025

