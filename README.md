# Gestão Facilitada

Sistema de gestão para pequenos negócios (comércio e serviços) com dois painéis:

- **Cliente**: vendas e caixa, produtos, fornecedores, loja online, calculadora de preço, clientes, quem me deve, agenda com calendário do Brasil, emissão de nota (pedido ao escritório), impostos, documentos e relatórios (DRE, balanço gerencial e fechamento).
- **ADM (escritório contábil)**: empresas, planos, convites, fechamento por empresa, classificação de lançamentos, solicitações, notas, impostos e documentos.

É um arquivo único (`index.html`), sem servidor.

## Publicar no GitHub Pages

1. Crie um repositório e envie `index.html`, `README.md` e `.nojekyll`.
2. Em **Settings → Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`.
3. Em alguns minutos o site fica em `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`.

## Primeiro acesso do ADM

1. Abra o site com `#admin` no final do endereço (ex.: `https://SEU-USUARIO.github.io/REPO/#admin`).
2. O e-mail do administrador vem travado em `ADM_EMAIL` (começo do script do `index.html`). Só ele consegue criar o acesso. Crie a sua senha pessoal; ela nunca é gravada no código.
3. Depois, entre normalmente pelo endereço sem `#admin`.

## Cadastro de clientes e equipe (senha provisória)

- **Cliente**: em *Empresas e valores → Cadastrar cliente*, preencha os dados e a **senha provisória** (ou deixe vazio para gerar uma). Clique em *Abrir e-mail pronto para enviar* para mandar o acesso pelo seu e-mail.
- **Equipe**: em *Equipe e acessos*, mesmo processo, com perfil Analista ou Atendimento.
- No primeiro login, o sistema **obriga a pessoa a criar a própria senha**; a provisória deixa de funcionar.
- E-mail automático: se quiser que o sistema envie sozinho, coloque em `MAIL_WEBHOOK` a URL de um webhook (Make, Zapier ou uma função com Resend) que receba `{to, subject, text}`. Vazio = usa o seu app de e-mail.

## Visuais por empresa

Cada empresa pode ter um visual (Padrão, Verão feminino, Oceano, Natureza, Doce, Noite elegante, Barbearia). O ADM escolhe ao gerar o convite ou em **Empresas → Gestão**. Para criar um visual novo, adicione uma entrada em `THEMES` e um bloco `body.t-NOME{...}` no CSS.

## Planos

- **Comércio**: sistema completo de loja.
- **Serviço**: em desenvolvimento (competências e obrigações).
- **Personalizado**: o ADM marca as abas liberadas de cada cliente.

## Calendário

Feriados nacionais, estaduais (por UF), datas comerciais, estações e o tema de cada mês, com Carnaval e Páscoa calculados por ano. Feriados municipais: só Salvador por enquanto. Confirme sempre no calendário oficial do seu município.

## Limites importantes

- **Os dados ficam no navegador de cada pessoa** (por isso o cliente só consegue entrar no aparelho em que o cadastro foi feito; para uso real com vários aparelhos e e-mail de redefinição automático é preciso um backend, por exemplo Supabase ou Firebase Auth) (localStorage). Não há servidor, então uma empresa cadastrada num aparelho não aparece em outro. Para uso real com vários usuários é preciso um backend com login seguro e banco de dados.
- O acesso do ADM e as senhas são guardados de forma simplificada, só para protótipo. Não use para dados sensíveis.
- A emissão de nota fiscal real exige CNPJ, inscrição estadual, certificado digital e um emissor com API (ver aba **Emitir nota** e **Gateway fiscal**). Hoje o sistema só registra o pedido.
- Os dados de demonstração (Padaria Sol, Studio Lia, Praia Bahia e Loja Modelo) são fictícios.
