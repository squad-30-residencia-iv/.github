# 📋 Requisitos da Solução

> Documento mantido pelo **Squad 1 (Negócios & Produto)**. Consolida conceitos, requisitos funcionais, regras de negócio e escopo macro do Portal de Vouchers.

---

## 1. Conceitos

| Termo | Definição |
| :---- | :-------- |
| **Campanha** | Entidade principal do sistema. Todo voucher é necessariamente derivado de uma campanha. |
| **Alvo** | Escopo de aplicação de um benefício ou de uma quantidade, em uma de três formas: `TODOS`, `CATEGORIA(id)` ou `PRODUTO(id)`. Substitui o uso de "produto" como eixo único de configuração. |
| **Item de Campanha** | Tupla (alvo, benefício, quantidade de vouchers). Uma campanha possui um ou mais itens. |
| **Vigência da Campanha** | Janela em que a campanha pode gerar vouchers (data/hora de início e fim). |
| **Validade do Voucher** | Janela em que um voucher já emitido pode ser resgatado. É independente da vigência da campanha. |
| **Hierarquia Organizacional** | Rede → Região → Estabelecimento → Canal (físico ou virtual). |

---

## 2. Módulo de Campanhas

### 2.1 Requisitos funcionais

| ID | Descrição |
| :-- | :-------- |
| **RF01** | O sistema deve permitir o cadastro de uma nova campanha promocional baseada em cupons ou vouchers. |
| **RF02** | O sistema deve permitir associar um ou mais alvos (produtos ou categorias) a uma campanha. |
| **RF02a** | O sistema deve permitir definir o benefício da campanha por alvo, em percentual (%) ou valor fixo (R$), quando necessário. |
| **RF02b** | O sistema deve permitir aplicar um único benefício para toda a campanha, quando não houver necessidade de diferenciação equivalente a um único alvo do tipo TODOS. |
| **RF03** | O sistema deve permitir configurar as condições para geração dos vouchers, possibilitando combinar diferentes regras da campanha. |
| **RF04** | O sistema deve permitir definir a categoria de cada produto vinculado à campanha. |
| **RF05** | O sistema deve permitir definir o período de vigência da campanha (data/hora de início e fim), válido para todos os alvos nela contidos. |
| **RF06** | O sistema deve permitir definir a quantidade total de vouchers disponíveis para a campanha como um todo. |
| **RF06a** | O sistema deve permitir definir a quantidade total de vouchers disponíveis para a campanha como um todo. |
| **RF06b** | O sistema deve permitir cadastrar produtos e categorias básicos (nome, categoria à qual pertence, identificador) diretamente no portal, já que a integração com o catálogo real da empresa está fora de escopo nesta fase. |
| **RF07** | O sistema deve permitir vincular a campanha a estabelecimento(s), rede ou região específicas. |
| **RF08** | O sistema deve permitir definir o público ou tipo de cliente elegível para a campanha. |
| **RF09** | O sistema deve permitir configurar as regras de elegibilidade do cliente para participar da campanha, conforme o módulo de Elegibilidade do Cliente. |
| **RF10** | O sistema deve permitir editar uma campanha, respeitando as regras e restrições aplicáveis aos vouchers já emitidos. |
| **RF11** | O sistema deve permitir pausar, encerrar ou cancelar uma campanha antes do fim da vigência. |
| **RF12** | O sistema deve permitir consultar o status da campanha, incluindo: ativa, agendada, pausada, encerrada e esgotada. |
| **RF13** | O sistema deve permitir duplicar uma campanha existente como base para uma nova. |

### 2.2 Regras de negócio

| ID | Descrição |
| :-- | :-------- |
| **RN01** | Uma campanha não poderá ser ativada sem as informações obrigatórias definidas, incluindo período, benefício, quantidade de vouchers, público elegível e regras necessárias para a campanha. |
| **RN02** | A data de início não pode ser posterior à data de fim. |
| **RN03** | A quantidade de vouchers emitidos (somada entre todos os alvos) não pode ultrapassar a quantidade total definida na campanha. |
| **RN03a** | Se a quantidade de vouchers for definida por produto (RF06a), a soma das quantidades por produto não pode ultrapassar a quantidade total da campanha (RF06). |
| **RN03b** | A soma das quantidades de vouchers definidas por alvo não pode ultrapassar a quantidade total da campanha. |
| **RN04** | Campanhas encerradas, canceladas ou esgotadas não poderão gerar novos vouchers. |
| **RN05** | O valor do desconto deve ser maior que zero e, se percentual, não pode ultrapassar 100%. |
| **RN06** | Uma campanha só poderá ser vinculada a estabelecimentos, redes ou regiões previamente cadastrados e ativos no sistema. |
| **RN06a** | Ao atingir a quantidade máxima de vouchers de um produto específico, novas emissões para aquele produto devem ser bloqueadas, mesmo que a campanha ainda tenha saldo de vouchers para outros produtos. |
| **RN06b** | Ao atingir a quantidade máxima de vouchers de um alvo, novas emissões para aquele alvo devem ser bloqueadas, mesmo que a campanha ainda tenha saldo em outros alvos. |

---

## 3. Módulo de Plataforma (Motor de Voucher)

### 3.1 Requisitos funcionais

| ID | Descrição |
| :-- | :-------- |
| **RF14** | O sistema deve gerar um voucher único (código) para cada emissão dentro de uma campanha ativa. |
| **RF14a** | O sistema deve suportar diferentes condições configuráveis para geração dos vouchers, incluindo valor total da compra, quantidade de compras, volume de itens, produtos ou categorias específicas, combinação de produtos e período da compra. |
| **RF15** | O sistema deve disponibilizar o voucher ao cliente elegível, por meio do canal definido para a solução (canal ainda a definir). |
| **RF16** | O sistema deve validar se o cliente é elegível antes de emitir/disponibilizar o voucher. |
| **RF17** | O sistema deve permitir a validação e o resgate do voucher no momento da compra, por meio do mecanismo definido para a solução (ex.: código ou QR Code). |
| **RF17a** | O sistema deve validar as restrições de uso configuradas na campanha, incluindo valor mínimo ou máximo da compra, produtos ou categorias aplicáveis, limites de utilização, validade e lojas ou canais permitidos. |
| **RF18** | O sistema deve impedir o resgate de um voucher fora do seu período de validade próprio, calculado no momento da emissão. |
| **RF18a** | O sistema deve permitir configurar a validade do voucher como prazo relativo (N dias/horas a partir da emissão) ou data fixa, com opção de teto máximo. |
| **RF19** | O sistema deve controlar a quantidade de utilizações permitida para cada voucher, de acordo com as regras definidas na campanha. |
| **RF20** | O sistema deve atualizar o status do voucher (disponível, utilizado, expirado, cancelado) em tempo real. |
| **RF21** | O sistema deve registrar histórico de todas as movimentações do voucher (emissão, uso, expiração, cancelamento). |

### 3.2 Regras de negócio

| ID | Descrição |
| :-- | :-------- |
| **RN07** | Um voucher expirado não pode ser resgatado, mesmo que ainda não utilizado. |
| **RN07a** | O encerramento (natural ou antecipado), a pausa ou o esgotamento da campanha não afetam a validade dos vouchers já emitidos, que permanecem resgatáveis até sua própria expiração. |
| **RN08** | Um voucher só poderá ser resgatado nos estabelecimentos, redes ou regiões vinculados à campanha de origem e nos canais permitidos. |
| **RN09** | Ao atingir a quantidade máxima de vouchers da campanha, novas emissões devem ser bloqueadas automaticamente. |
| **RN10** | O cancelamento de uma campanha deverá invalidar automaticamente os vouchers ainda não utilizados vinculados a ela. |
| **RN10a** | Quando mais de um alvo se aplicar ao mesmo item da compra, prevalece o mais específico (PRODUTO > CATEGORIA > TODOS). |

---

## 4. Módulo de Dashboard e Relatórios

### 4.1 Requisitos funcionais

| ID | Descrição |
| :-- | :-------- |
| **RF22** | O sistema deve exibir a quantidade de vouchers emitidos por campanha. |
| **RF23** | O sistema deve exibir a quantidade de vouchers utilizados (resgatados) por campanha. |
| **RF24** | O sistema deve exibir a quantidade de vouchers expirados e não utilizados por campanha. |
| **RF25** | O sistema deve exibir indicadores de uso das campanhas, como a taxa de utilização dos vouchers. |
| **RF26** | O sistema deve permitir filtrar os indicadores por período, categoria, estabelecimento, rede, região e tipo de cliente. |
| **RF27** | O sistema deve permitir exportar os dados dos relatórios ou dashboard, em formato a ser definido. |
| **RF27a** | O sistema deve disponibilizar informações de auditoria e histórico das operações realizadas nas campanhas e vouchers. |

---

## 5. Elegibilidade do Cliente (Segmentação)

### 5.1 Requisitos funcionais

| ID | Descrição |
| :-- | :-------- |
| **RF28** | O sistema deve permitir configurar critérios de elegibilidade por perfil do cliente, como dados cadastrais, faixa etária ou localização. |
| **RF28a** | O sistema deve permitir direcionar a campanha a clientes específicos ou a grupos de clientes definidos pelos critérios configurados. |
| **RF29** | O sistema deve permitir configurar critérios de elegibilidade por histórico de compras, como valor gasto, frequência de compra ou categoria adquirida em determinado período. |
| **RF30** | O sistema deve permitir combinar múltiplos critérios de elegibilidade em uma mesma campanha. |
| **RF31** | O sistema deve calcular ou validar a elegibilidade do cliente no momento da emissão do voucher. |
| **RF32** | O sistema deve permitir simular a avaliação dos critérios de elegibilidade para um cliente informado, antes da ativação da campanha, de modo que o analista possa validar a configuração das regras. A consulta em massa da base de clientes depende de serviço externo de segmentação e está fora do escopo desta fase. |

### 5.2 Regras de negócio

| ID | Descrição |
| :-- | :-------- |
| **RN11** | Um cliente que não atenda aos critérios de elegibilidade não poderá receber voucher da campanha. |
| **RN12** | Critérios de elegibilidade baseados em histórico de compra devem considerar uma janela de tempo configurável (ex.: últimos 90 dias). |
| **RN13** | *(Pendência)* Definir se a elegibilidade será reavaliada somente na emissão do voucher ou também no momento do resgate. |

---

## 6. Módulo de APIs e Integrações

### 6.1 Requisitos funcionais

| ID | Descrição |
| :-- | :-------- |
| **RF33** | O sistema deve disponibilizar uma API para consulta das campanhas vigentes. |
| **RF34** | O sistema deve disponibilizar APIs para geração, validação e resgate de vouchers. |
| **RF35** | O sistema deve disponibilizar uma API para consulta dos vouchers associados a um cliente. |
| **RF36** | As APIs devem permitir a integração das campanhas e vouchers com aplicações satélites e outros sistemas. |

---

## 7. Escopo e pendências registrados no levantamento

- **Fora de escopo nesta fase:** integração com o catálogo real da empresa (produtos e categorias são cadastrados de forma básica no portal — RF06b).
- **Fora de escopo nesta fase:** consulta em massa da base de clientes; depende de serviço externo de segmentação (RF32).
- **A definir:** canal de disponibilização do voucher ao cliente (RF15).
- **A definir:** formato de exportação dos relatórios/dashboard (RF27).
- **Pendência de regra:** reavaliação da elegibilidade só na emissão ou também no resgate (RN13).
