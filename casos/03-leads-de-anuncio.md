# Leads de anúncio direto no CRM, inclusive sem telefone

## O problema
A clínica anuncia no Instagram com botões que levam ao WhatsApp e ao Direct. Os contatos que chegavam por esses anúncios não entravam no CRM, e a equipe perdia de onde cada paciente tinha vindo. O CRM não tem integração pronta com o Make; só uma API REST.

## O que fiz
- Um webhook recebe a mensagem que veio de um anúncio (o "referral" que a Meta manda junto) e um cenário cria o lead no CRM pela API REST.
- Campanha, conjunto e anúncio são resolvidos pela API de anúncios da Meta e gravados nas observações do lead, porque o CRM não tem campo de origem.
- Todo lead de anúncio recebe uma etiqueta própria, criada no CRM para isso.
- **Lead do Direct não tem telefone.** Em vez de perder o contato, o lead entra com o link da conversa no Direct e um aviso claro para a equipe responder por lá.
- Para receber o Direct, configurei o app da Meta com o caso de uso do Instagram e o webhook das mensagens.

## Como provei
Simulei um lead de anúncio com dados de teste: o lead foi criado no CRM com campanha, conjunto e anúncio resolvidos e com a etiqueta aplicada.

## O que eu levo
Nem todo dado vem completo. O sistema precisa decidir o que fazer com o lead pela metade, em vez de descartar.
