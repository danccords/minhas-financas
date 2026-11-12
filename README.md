# Minhas Finanças

Controle financeiro pessoal para o celular, no formato da minha planilha mensal.

- **Mês a mês:** entradas, gastos, saldo e investido, com os blocos *Gastos do mês*, *Fixos* (com "pago"), *Cartão de crédito parcelado*, *Entradas* e *Investimentos*
- **Compras parceladas:** informe o valor total ou o valor de cada parcela (com juros) e o número de vezes; o app cria todas as parcelas nos meses seguintes
- **Fechamento do cartão:** com o dia de fechamento de cada cartão, a 1ª parcela já cai no mês da fatura certa
- **Virada de mês:** copiar fixos e trazer parcelas do mês anterior (avança 5/10 → 6/10)
- **Por categoria** (com valor esperado) e **por tipo de pagamento** (com "fatura paga?")
- **Visão anual** com gráfico de entradas × gastos

## Onde ficam os dados

Os lançamentos ficam no **Firebase (Cloud Firestore)**, na conta de quem fez login (Google ou e-mail e senha), e sincronizam entre celular e computador. As regras do banco só deixam cada usuário ler e gravar os próprios dados (`users/{uid}/...`), e só para contas liberadas: o dono e os e-mails que ele adicionar em **Ano → Quem pode usar o app**. Contas com e-mail e senha precisam confirmar o e-mail. A configuração do Firebase que aparece no código é pública por natureza; a proteção vem do login e das regras.

O app também guarda uma cópia local para funcionar sem internet; as mudanças sobem quando a conexão volta. Em **Ano → Conta e backup** dá para baixar e restaurar um backup.

No iPhone, abra no Safari e use **Compartilhar → Adicionar à Tela de Início**. Assim ele abre como app e o iOS não apaga os dados por falta de uso.

## Dados iniciais

`dados-iniciais.json` guarda os lançamentos iniciais **criptografados** (AES-256-GCM, chave derivada da senha com PBKDF2-SHA256, 600 mil iterações). Sem a senha o arquivo é ilegível. Quando o app abre vazio, ele pede a senha e carrega esses dados no aparelho; "Começar vazio" ignora.
