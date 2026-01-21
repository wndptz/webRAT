Sistema de RAT - Relatório de Atendimento Técnico

https://img.shields.io/badge/Status-Produção-success
https://img.shields.io/badge/Tecnologia-HTML%2FCSS%2FJavaScript-blue
https://img.shields.io/badge/Armazenamento-LocalStorage-lightgrey
https://img.shields.io/badge/Licença-MIT-green

Um sistema web completo para gerenciamento de Relatórios de Atendimento Técnico (RAT) que funciona totalmente no navegador, sem necessidade de servidor ou banco de dados externo.

✨ Funcionalidades

📋 Gestão de RATs

· CRUD completo: Criar, ler, editar e excluir relatórios
· Formulário intuitivo: Todos os campos necessários para atendimentos técnicos
· Cálculos automáticos: Horas trabalhadas, combustível (KM × 1.6), despesas
· Cópias inteligentes: Criar cópias de RATs existentes com um clique
· Persistência local: Dados salvos automaticamente no localStorage

📊 Faturamento Avançado

· Valor por hora configurável: Defina seu valor hora uma vez, use sempre
· Seleção múltipla: Escolha quais RATs incluir no faturamento
· Cálculos automáticos: Total de horas, valor horas, despesas e total geral
· Relatório consolidado: Gere faturamento completo em Markdown
· Validação inteligente: Detecta e ajuda a corrigir horas não calculadas

📁 Exportação Flexível

· Exportação individual: Cada RAT como arquivo Markdown separado
· Exportação em massa: Baixe todos os RATs de uma vez
· Backup JSON: Exporte/importe todos os dados em formato JSON
· Nomenclatura automática: Arquivos nomeados por consultor + data + ID

🎨 Interface Moderna

· Design responsivo: Funciona em desktop e mobile
· Indicadores visuais: Badges coloridos para tipos de atendimento
· Modo edição/criação: Interface clara para cada contexto
· Notificações: Feedback imediato das ações realizadas

🚀 Como Usar

1. Primeiro Acesso

1. Abra o arquivo index.html em qualquer navegador moderno
2. Digite seu nome no campo "Consultor" (será lembrado automaticamente)
3. Defina o valor da sua hora no campo "Valor da Hora"

2. Criando um RAT

1. Preencha os campos obrigatórios (*):
   · Projeto/Sistema
   · Empresa
   · Data/Hora Início
   · Descrição do Serviço
2. Selecione o tipo de atendimento (Presencial/Remoto)
3. Para atendimentos presenciais:
   · Informe a distância em KM (combustível calculado automaticamente)
   · Adicione valores de pedágio se aplicável
4. Use "Calcular Horas" se tiver Data/Hora Fim
5. Clique em "Salvar RAT"

3. Editando e Gerenciando

· Editar: Clique no ícone ✏️ na tabela
· Criar cópia: Clique no ícone 📋
· Gerar Markdown: Clique no ícone 📄
· Excluir: Clique no ícone 🗑️

4. Faturando RATs

1. Defina o valor da hora (se ainda não definiu)
2. Selecione os RATs a faturar (todos selecionados por padrão)
3. Clique em "Gerar Faturamento"
4. Revise o relatório consolidado no modal
5. Copie ou baixe o faturamento completo

5. Exportando Dados

· Backup completo: Use "Exportar JSON" para backup
· Restaurar backup: Use "Importar JSON" para restaurar
· Arquivos individuais: "Baixar Todos os RATs" para Markdowns separados

📋 Campos do Formulário

Informações Básicas

· Projeto (Sistema) * - Nome do projeto/sistema atendido
· Empresa * - Cliente atendido
· CNPJ - CNPJ do cliente
· Contato - Nome e telefone do contato
· Consultor * - Seu nome (persistente)

Detalhes do Atendimento

· Tipo de Atendimento * - Presencial ou Remoto
· Distância (KM) - Apenas para presencial (desabilita automaticamente para remoto)
· Data Início * - Data do atendimento
· Hora Início * - Hora de início
· Intervalo - Intervalo para descanso/almoço (padrão: 01:00)
· Data Fim - Data de término
· Hora Fim - Hora de término
· Horas Trabalhadas - Calculado automaticamente (HH:MM)

Descrição e Despesas

· Descrição do Serviço * - Detalhamento do serviço realizado
· Valor Alimentação - Despesas com alimentação
· Valor Pedágio - Despesas com pedágio
· Valor Outros - Outras despesas
· Observação - Observações adicionais

🔧 Regras de Negócio

Cálculo de Combustível

· Valor fixo por KM: R$ 1,60
· Cálculo automático: distância × 1.6 = valor combustível
· Apenas presencial: Desabilitado para atendimentos remotos

Cálculo de Horas

1. Preencha Data/Hora Início e Fim
2. Clique em "Calcular Horas" ou deixe o sistema calcular ao salvar
3. Intervalo é automaticamente subtraído
4. Horas negativas são ajustadas para "00:00"

Faturamento

· Valor horas: horas × valor hora
· Despesas: Soma de alimentação + combustível + pedágio + outros
· Total geral: valor horas + despesas

📁 Estrutura de Dados

Armazenamento Local

· RATs: localStorage.getItem('rats') - Array de objetos JSON
· Consultor: localStorage.getItem('consultor') - Nome do consultor
· Valor Hora: localStorage.getItem('valorHora') - Valor da hora em R$

Formato JSON dos RATs

```json
{
  "id": 1,
  "projeto": "ERP/CUSTOMIZAÇÕES",
  "empresa": "EMPRESA CLIENTE LTDA",
  "cnpj": "99.999.999.0001-99",
  "contato": "ALEX NALLI",
  "tipoAtendimento": "Presencial",
  "distanciaKm": 90,
  "totalKm": 144,
  "valorKm": 1.6,
  "dataInicio": "2026-01-08",
  "horaInicio": "08:30",
  "intervalo": "00:30",
  "dataFim": "2026-01-08",
  "horaFim": "17:30",
  "horasTrabalhadas": "08:30",
  "descricao": "Alinhamento das correções...",
  "valorAlimentacao": 50,
  "valorPedagio": 0,
  "valorOutros": 0,
  "observacao": "Nenhuma observação adicional.",
  "consultor": "Seu Nome",
  "dataCriacao": "2026-01-16T17:45:18.000Z"
}
```

💡 Dicas e Melhores Práticas

Para Consultores

1. Preencha sempre o consultor - Facilita a identificação dos relatórios
2. Use cópias inteligentes - Para atendimentos similares, crie cópias
3. Calcule horas sempre - Evite problemas no faturamento
4. Faça backup regular - Exporte JSON periodicamente

Para Gestores

1. Padronize nomes de projetos - Facilita busca e organização
2. Revise horas antes de faturar - Use a validação automática
3. Use a exportação em massa - Para arquivamento ou compartilhamento
4. Monitore despesas - Analise padrões nos relatórios

🔄 Compatibilidade e Portabilidade

Navegadores Suportados

· ✅ Chrome 60+
· ✅ Firefox 55+
· ✅ Safari 11+
· ✅ Edge 79+
· ✅ Opera 50+

Funcionamento Offline

· ⚡ Totalmente offline após carregado
· 💾 Persistência local sem necessidade de internet
· 📁 Exportação/importação para backup físico

Portabilidade

· 🚀 Arquivo único - Apenas um HTML contém todo o sistema
· 📦 Sem instalação - Basta abrir no navegador
· 🔄 Multiplataforma - Windows, macOS, Linux, Android, iOS

🛠️ Tecnologias Utilizadas

· HTML5 - Estrutura semântica
· CSS3 - Estilização moderna com variáveis CSS
· JavaScript (ES6) - Lógica e interatividade
· Font Awesome - Ícones
· LocalStorage API - Persistência de dados
· File API - Exportação/importação de arquivos

📄 Licença

Este projeto está licenciado sob a licença MIT - veja o arquivo LICENSE para detalhes.

🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (git checkout -b feature/AmazingFeature)
3. Commit suas mudanças (git commit -m 'Add some AmazingFeature')
4. Push para a branch (git push origin feature/AmazingFeature)
5. Abra um Pull Request

⚠️ Limitações Conhecidas

· Armazenamento limitado: localStorage tem limite de ~5-10MB
· Sem multiusuário: Sistema projetado para uso individual
· Sem histórico: Não mantém histórico de alterações
· Sem sincronização: Dados apenas no navegador local

🆘 Suporte e Problemas

Problemas Comuns

1. Dados perdidos - Use backups JSON regularmente
2. Horas não calculadas - Preencha Data/Hora Fim ou use cálculo manual
3. Arquivos não baixam - Verifique bloqueador de popups do navegador

Solução de Problemas

· Limpar dados: Use "Limpar Todos os Dados" com cautela
· Importar backup: Restaure de um backup JSON anterior
· Trocar navegador: Se persistirem problemas, tente outro navegador

---

Nota: Este sistema é uma ferramenta de produtividade para consultores técnicos. Não substitui sistemas de gestão empresarial completos, mas é uma solução eficaz para registro e faturamento de atendimentos técnicos.

Versão: 1.0.0
Última atualização: Janeiro 2026
Sistema RAT - Desenvolvido para consultores técnicos