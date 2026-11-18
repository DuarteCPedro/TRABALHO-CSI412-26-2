* **Problema que o software resolve:**
  O InvenTree resolve dificuldades operacionais de controlar estoques físicos, cadeias de suprimentos e processos de produção sem depender de planilhas manuais ou de sistemas ERPs de alto custo e baixa adaptabilidade. Como um software livre de gerenciamento de estoque e ciclo de vida de produtos (IMS/PLM), ele tem diversas funcionalidades, sendo altamente extensível por meio de um sistema de plugins. O projeto demonstra duas intenções principais:
  * **Democratizar o acesso à tecnologia:** Oferecer uma ferramenta industrial leve, gratuita e de fácil implementação para pequenas e médias empresas, startups de hardware, laboratórios e entusiastas.
  * **Permitir a personalização pelo contexto do usuário:** Adaptar fluxos de trabalho, interface e metadados às regras de negócio de cada operação sem exigir modificações no código-fonte original.
  * **Evidências:** [Documentação oficial](https://docs.inventree.org/en/latest/); arquivo `README.md` (commit: `7a137c8`); [Arquitetura de plugins](https://docs.inventree.org/en/latest/plugins/).

* **Público-alvo:**
  O InvenTree atende usuários que operam com engenharia de hardware, manufatura e distribuição logística, desde:
  * **Startups de hardware e indústrias eletrônicas:** Empresas que desenvolvem placas e equipamentos embarcados, exigindo integração com ferramentas CAD e regulamentações.
  * **Pequenas/médias empresas e distribuidoras:** Operações comerciais com SKUs que precisam controlar estoques via código de barras e integrar com ERPs corporativos.
  * **Laboratórios de pesquisas e equipes acadêmicas:** Grupos de prototipagem e competições tecnológicas (como equipes da Formula SAE) que gerenciam listas de materiais e custos de fabricação.
  * **Evidências:** [Definição oficial na documentação](https://docs.inventree.org/en/latest/); [Relatos no GitHub](https://github.com/inventree/InvenTree/discussions) — algumas discussões: “How do you handle RoHS information / compliance?”, “racking manufacturing operations / labor costs in BOM pricing”, “For website: Organizations that use InvenTree”, “[PAID PROJECT] Looking for an expert InvenTree/Python developer for SAP ERP Integration”.

* **Principais usuários:**
  O InvenTree organiza o acesso dos usuários através do **RBAC (Controle de acesso baseado em papéis)**, agrupando contas (`user`) em grupos (`group`) com diferentes permissões (`view`, `change`, `add`, `delete`) sobre 12 papéis distintos, além de funções com privilégios para administradores (`staff` e `superuser`). Na prática, os principais perfis de usuários são:
  * **Projetistas/Desenvolvedores:** Atuam nos papéis `part categories`, `parts` e `bills of material`, cadastrando componentes, revisões técnicas e listas de materiais integradas a ferramentas de desenho de placas (CADs).
  * **Equipe de produção:** Atuam nos papéis `build orders`, `bills of material` e `stock items`, executando ordens de fabricação, separando matéria-prima e registrando peças montadas.
  * **Estoquistas:** Atuam nos papéis `stock locations`, `stock items` e `transfer orders`, organizando prateleiras, realizando contagens de estoque e bipando códigos de barras pelo aplicativo móvel (*InvenTree mobile app*).
  * **Comercial:** Atuam nos papéis `purchase orders`, `sales orders`, `return orders` e `pricing`, gerenciando pedidos e o cadastro de empresas parceiras (`company`).
  * **Colaboradores de TI:** Atuam sob o papel `admin` e as tags `staff` e `superuser`, configurando permissões, auditoria, templates, plugins e integrações.
  * **Evidências:** [User permissions na documentação](https://docs.inventree.org/en/latest/settings/permissions/); [Fluxos de chão de fábrica em mobile app](https://docs.inventree.org/en/latest/app/); [Distinção entre usuários internos e empresas externas em companies](https://docs.inventree.org/en/latest/concepts/company/).

* **Principais funcionalidades:**
  * **Peças e listas de materias:** Cadastro por hierarquia e categorias, revisões, conversão de unidades físicas e listas de materiais com importação/exportação em lote.
  * **Estoque e rastreabilidade:** Mapeamento por localizações em cascata, alertas de estoque vazio ou cheio, rastreamento por lote ou número de série e histórico de movimentações.
  * **Produção (*build orders*):** Execução de ordens de construções com cálculo de insumos, alocação de estoque e suporte a produções terceiras.
  * **Compras e vendas:** Cadastro de fornecedores, fabricantes e clientes (`company`), gestão de compra, venda e devolução, e valores em várias moedas.
  * **Códigos de Barras e aplicativo:** Leitura e geração de etiquetas, suporte para distribuidores e aplicativo Android/iOS para operação no estoque.
  * **Relatórios em PDF:** Geração de etiquetas, certificados de pedidos a partir de templates HTML/CSS com pré visualização.
  * **API REST, plugins e auditoria:** API documentada com autenticações, biblioteca Python, suporte a extensões plugins e trilha de auditoria.
  * **Evidências:** Documentação oficial em [Parts](https://docs.inventree.org/en/latest/part/), [Stock](https://docs.inventree.org/en/latest/stock/), [Manufacturing](https://docs.inventree.org/en/latest/manufacturing/), [Purchasing](https://docs.inventree.org/en/latest/purchasing/), [Sales](https://docs.inventree.org/en/latest/sales/), [Barcodes](https://docs.inventree.org/en/latest/barcodes/), [App](https://docs.inventree.org/en/latest/app/), [Reports](https://docs.inventree.org/en/latest/report/), [API](https://docs.inventree.org/en/latest/api/) e [Plugins](https://docs.inventree.org/en/latest/plugins/).

* **Tecnologias utilizadas:**
  * **Principais:** **Python** e **Django** (como framework) no backend; **React** e **TypeScript** no frontend; **PostgreSQL** como banco de dados principal (com suporte a MySQL/MariaDB e SQLite); e **Docker / Docker Compose** para implantação.
  * **Secundárias (apoio):** **Redis** (cache e filas assíncronas), **Caddy** ou **Nginx** (proxy reverso) e **WeasyPrint** (geração de PDFs).
  * **Evidências:** Documentação oficial ([Architecture](https://docs.inventree.org/en/latest/develop/architecture/), [Processes](https://docs.inventree.org/en/latest/start/processes/) e [React Frontend](https://docs.inventree.org/en/latest/develop/react-frontend/)); 
* **Licença:**
  * **MIT License:** Licença de código aberto que permite usar, modificar e distribuir o software gratuitamente, exigindo apenas os créditos originais e isenção dos autores.
  * **Evidência:** [LICENSE](https://github.com/inventree/InvenTree/blob/7a137c8/LICENSE) na raiz do repositório (commit `7a137c8`).

* **Versão/release analisada:**
  * **Release `1.7.2` (Commit has: `7a137c8`):** Versão congelada como base para o trabalho, seguindo o versionamento do projeto para garantir que futuras atualizações no repositório não invalidem os diagramas e as evidências levantadas.
