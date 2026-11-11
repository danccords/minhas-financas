# Minhas Finanças

Controle financeiro pessoal para o celular, no formato da minha planilha mensal.

- **Mês a mês:** entradas, gastos, saldo e investido, com os blocos *Gastos do mês*, *Fixos* (com "pago"), *Cartão de crédito parcelado*, *Entradas* e *Investimentos*
- **Compras parceladas:** informe o valor total ou o valor de cada parcela (com juros) e o número de vezes; o app cria todas as parcelas nos meses seguintes
- **Fechamento do cartão:** com o dia de fechamento de cada cartão, a 1ª parcela já cai no mês da fatura certa
- **Virada de mês:** copiar fixos e trazer parcelas do mês anterior (avança 5/10 → 6/10)
- **Por categoria** (com valor esperado) e **por tipo de pagamento** (com "fatura paga?")
- **Visão anual** com gráfico de entradas × gastos

## Onde ficam os dados

Os lançamentos ficam salvos **só no navegador do aparelho** (localStorage). Nada é enviado para o GitHub nem para nenhum servidor.
Use **Ano → Backup → Baixar backup** de vez em quando, e **Restaurar backup** para levar os dados para outro aparelho.

No iPhone, abra no Safari e use **Compartilhar → Adicionar à Tela de Início**. Assim ele abre como app e o iOS não apaga os dados por falta de uso.

## Dados iniciais

`dados-iniciais.json` guarda os lançamentos iniciais **criptografados** (AES-256-GCM, chave derivada da senha com PBKDF2-SHA256, 600 mil iterações). Sem a senha o arquivo é ilegível. Quando o app abre vazio, ele pede a senha e carrega esses dados no aparelho; "Começar vazio" ignora.
