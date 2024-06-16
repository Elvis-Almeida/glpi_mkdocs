# Como usar o GLPI

![Banner GLPI](/glpi/images/glpi.png)

## Introdução

GLPI (Gestionnaire Libre de Parc Informatique) é uma ferramenta de código aberto para gerenciamento de ativos de TI e helpdesk, serve para rastrear e gerenciar seus recursos de TI.

Suas principais funcionalidades são:

- **Gestão de Ativos de TI**
- **Gestão de Mudanças**
- **Gestão de Problemas**
- **Gestão de Projetos**
- **Gestão de Contratos**
- **Relatórios e Análise**

## Visão geral

### Dashboard

![dashboard](/glpi/images/dashboad1.png)

Aqui você tem uma visão geral e abrangente de todo o sistema que vão desde a quantidade de computadores, softwares, racks, licenças, monitores, dispositivos de rede, telefone e impressoras, dados sobre os chamados e tickets abertos.

### Ativos

![Ativos](/glpi/images/Ativos.png)

Na seção de ativos permite você gerenciar diversos tipos de ativos de TI, algumas das principais funcionalidades que podem ser realizadas nas opções de ativos do GLPI como:

**Inventário de Equipamentos**.

você pode manter um inventário detalhado de todos os seus equipamentos de TI, como:

> Computadores: Desktops, laptops, servidores, etc.<br>
> Impressoras: Impressoras de rede, multifuncionais, etc.
> Monitores <br>
> Dispositivos de Rede: Roteadores, switches, pontos de acesso, etc.<br>
> Periféricos: Teclados, mouses, etc.

**Gerenciamento de Software**

Você pode rastrear e gerenciar todos os softwares instalados em sua infraestrutura, incluindo:

> Licenças de Software: Monitorar a quantidade de licenças e suas validades.<br>
> Versionamento: Manter registro das versões dos softwares instalados.<br>
> Conformidade: Garantir que todos os softwares estejam em conformidade com as políticas da empresa.

**Gerenciamento de Componentes**

Você pode registrar componentes de hardware e seus detalhes, como:

> Memória RAM<br>
> Discos Rígidos/SSD<br>
> Placas de Vídeo<br>
> Processadores<br>

**Gerenciamento de Periféricos e Consumíveis**

Você pode rastrear e gerenciar periféricos e consumíveis, incluindo:

> Periféricos: Teclados, mouses, webcams, etc.<br>
> Consumíveis: Tinta de impressora, papel, etc.

**Gerenciamento de Redes**

Você pode documentar e gerenciar ativos de rede:

> Endereços IP: Gerenciamento de endereços IP e sub-redes.<br>
> Mapeamento de Rede: Visualização da topologia da rede.

**Gerenciamento de Documentação**

Armazenar e gerenciar documentação relacionada aos ativos:

> Contratos de Suporte<br>
> Manuais de Usuário<br>
> Notas Fiscais<br>
> Garantias

**Rastreio de Histórico e Manutenção**

Manter um registro do histórico e das atividades de manutenção:

> Histórico de Movimentações: Registrar movimentações de ativos entre diferentes locais ou usuários.<br>
> Histórico de Manutenção: Registrar reparos e manutenções realizadas em equipamentos.<br>
> Agendamento de Manutenções Preventivas: Planejar manutenções preventivas para evitar falhas.

**Relatórios e Análises**

Gerar relatórios detalhados sobre os ativos, incluindo:

> Inventário de Ativos<br>
> Relatórios de Utilização<br>
> Relatórios de Manutenção<br>
> Relatórios de Conformidade de Software<br>
> Automatização e Scripts

### Assistência

![Dashboard chamados](/glpi/images/dashboadchamados.png)

Na seção de assistência tem muitas funcionalidades para gerenciar o suporte técnico e assistência aos usuários, algumas das principais ações que podem ser realizadas nas opções de assistência do GLPI são:

**Criação e Gerenciamento de Tickets**

Criação de Tickets: Os tickets podem ser criados manualmente por técnicos ou usuários, ou automaticamente via email ou integração com outros sistemas.

Classificação e Categorização: Os tickets podem ser organizados em categorias e atribuídos diferentes níveis de prioridade.

**Atribuição e Gestão de Responsáveis**

Atribuição de Tickets: Tickets podem ser atribuídos automaticamente com base em regras predefinidas ou manualmente a técnicos ou grupos.

Gestão de Equipes: Criação de grupos de técnicos para facilitar a distribuição e gestão de tickets.

**Monitoramento e Resolução de Tickets**

Rastreamento de Status: Monitorar o status dos tickets e acompanhar o cumprimento dos SLAs.

Resolução de Problemas: Manter um histórico de atividades e documentar soluções para resolver os problemas reportados.

**Comunicação e Colaboração**

Comunicação Interna: Adicionar notas internas e transferir tickets entre técnicos ou grupos.

Comunicação com o Usuário: Enviar notificações automáticas por email e permitir que usuários acompanhem o status dos tickets via portal.

**Relatórios e Estatísticas**

Relatórios Personalizados: Gerar relatórios sobre o desempenho da equipe e detalhes dos tickets.

Dashboards: Criar dashboards personalizáveis para uma visão geral do help desk.

Existem muito mais funcionalidades que o GLPI pode oferecer porém nessa documentação ficará registrado apenas essas duas grandes áreas de atuação do GLPI que é a de **Ativos** e de **Assistência**

## Adicionando Ativos

Para iniciarmos vamos começar adicionando o ativo de computadores, para chegar nessa tela é só ir em `Ativos > Computadores`

![alt text](/glpi/images/AdicionandoAtivos.png)

Para adicionar um novo computador basta clicar em **Adicionar** botão que fica na parte superior do site.

![alt text](/glpi/images/ativoAddComputador.png)

Aqui nessa tela você pode adicionar informações como:

**Informações Gerais**

- Nome: O nome do computador para identificação.
  Status: O status atual do computador (em uso, em manutenção, etc.).

**Localização**

- Localização: O local físico onde o computador está situado.

**Detalhes do Computador**

- Tipo de computador: A classificação do tipo de computador (desktop, laptop, servidor, etc.).

- Técnico encarregado: O técnico responsável pela manutenção e suporte do computador.

- Fabricante: A empresa que fabricou o computador.

- Grupo encarregado: O grupo responsável pela gestão do computador.

- Modelo: O modelo específico do computador.

**Informações Adicionais do Usuário**

- Número alternativo do usuário: Um número alternativo para identificar o usuário.

- Número de série: O número de série único do computador.

- Nome alternativo do usuário: Um nome alternativo para o usuário do computador.

- Número de inventário: Um número de inventário único para rastreamento.

- Usuário: O nome do usuário atual do computador.

**Detalhes de Rede**

- Rede: Informações relacionadas à rede à qual o computador está conectado.

**Informações de Grupo e Identificação**

- Grupo: O grupo ao qual o computador pertence.

- UUID: O identificador único universal do computador.

- Comentários: Qualquer comentário adicional relevante para o computador.

- Fonte de Atualização: A origem das informações de atualização do computador.

Para cada item de ativos no GLPI seque a mesma lógica de cadastro, porém cada item terá suas respectivas informações de cadastro. Após preencher tudo você pode clicar em adicionar que seu item será adicionado ao inventário.

## Criando Chamado

Para criar um chamado você pode ir em `Assistência > Criar achamado`:

![Criando Chamado](/glpi/images/CriandoChamado.png)

Nessa tela você pode definir diversos parâmetros ao criar seus tickets como:

**Título do Chamado**<br>
**Descrição do Chamado**<br>
**Solicitante**<br>
**Localização**<br>
**Categoria**<br>
**Urgência**<br>
**Impacto**<br>
**Prioridade**<br>
**Atribuição**<br>
**Ativo Relacionado**<br>
**Data de Abertura**<br>
**Anexos**<br>
**SLA (Acordo de Nível de Serviço)**

E após preencher todos os campos você clicar em adicionar que seu ticket será adicionado.
