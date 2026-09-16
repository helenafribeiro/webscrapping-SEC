# webscrapping-SEC
Coleta automatizada da seção de demonstrações contábeis dos relatórios anuais protocolados na Securities and Exchange Commission (SEC), nos formulários 10-K, 20-F e 40-F, a partir de um painel de empresa-ano definido previamente.

O que o código faz
Consulta a interface de submissões da SEC (data.sec.gov/submissions) para cada CIK do painel e monta a tabela de protocolos.
Pareia cada observação de empresa-ano ao protocolo correspondente, primeiro pela data de encerramento do período informada pela SEC (tolerância de 15 dias) e, subsidiariamente, por janela de 15 a 400 dias sobre a data de arquivamento.
Localiza no documento a seção de demonstrações contábeis (Item 8 no 10-K, Item 18 ou 17 no 20-F, anexo EX-99 no 40-F) por âncoras textuais e por pontuação de sinais contábeis, com balanço patrimonial e notas explicativas obrigatórios, mínimo de quatro sinais e de 150 valores numéricos.
Converte o trecho selecionado em PDF com cabeçalho de identificação e registra logs de extração e de falhas, permitindo retomada da execução.
Estrutura
notebooks/ — cadernos Google Colab na ordem de execução
scripts/ — geradores dos cadernos e utilitários
docs/ — metodologia e figuras usadas no relato técnico
Execução

Os cadernos foram escritos para o Google Colab com Google Drive montado. Antes de executar, informe nome e endereço eletrônico na variável de identificação, conforme exigido pela política de acesso automatizado da SEC, que também limita a taxa de requisições (o código adota 8 por segundo, ante o teto de 10).

Dependências principais: pandas, requests, wkhtmltopdf, poppler-utils.

Dados

Os arquivos PDF gerados e as bases Compustat não são versionados neste repositório, por volume e por restrição de licença. O repositório contém o código, a documentação do método e os arquivos de índice de pequeno porte.
