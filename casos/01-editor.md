# O editor: a equipe muda, o paciente vê

## O problema
As mensagens de boas-vindas, os menus por especialidade e os agradecimentos moravam dentro de cenários do Make com dezenas de módulos. Para trocar um texto, alguém precisava achar o módulo certo num cenário enorme. Um erro ali podia desligar o atendimento.

## O que fiz
Um programa para Windows, de um arquivo só, que abre em janela própria:

- **Conversa:** desenha o mapa da conversa (mensagem, botões e para onde cada botão leva) e mostra, num celular de mentira, como o paciente recebe. A equipe troca texto, imagem e botões ali.
- **Modelos:** cria e duplica modelos de mensagem na Meta. Ao substituir um modelo, mantém os códigos dos botões para não quebrar as rotas do cenário.
- **Disparar:** envia para um contato ou para listas em PDF, XLS, XLSX ou CSV, com intervalo entre envios, limite por lote, botão de parar e registro em CSV.
- **Fluxos:** monta uma conversa nova do zero, com prévia navegável.
- **Custos:** mostra o gasto com a Meta por mês, pela API de preços da própria Meta.
- **Avisar atendente:** liga um botão da conversa a um aviso para a pessoa do atendimento.

## Decisões técnicas
- **Publicar com segurança.** Antes de gravar, o programa faz backup do cenário. Depois, compara o que foi gravado com o esperado; na primeira publicação real a diferença foi zero.
- **O mapa só mostra ligações reais.** Uma seta só aparece quando o botão de fato encaminha para aquela mensagem. Ligações deduzidas confundiam a equipe e foram retiradas.
- **Código nativo.** O programa é compilado com Nuitka, o que dificulta a engenharia reversa.
- **Credencial fora do repositório.** O acesso ao Make é embutido e embaralhado só na hora de gerar o executável; nunca fica no código-fonte. O executável é tratado como uma senha.
- **Funciona no computador da equipe.** Se faltar o componente de navegador do Windows (WebView2), o programa oferece instalar; se não der, abre no Edge em modo app.
- **Cobrança sem tocar no cartão.** A Meta não permite cadastrar cartão por API; a aba Pagamento só abre a página oficial de cobrança, num perfil de navegador separado.

## Ritmo
Seis versões entre 11 e 13/11/2026, ajustadas a cada uso da equipe.

## O que eu levo
Para quem não é técnico, a melhor ferramenta é a que mostra o resultado (a conversa como o paciente vê), não a configuração.
