# Recuperação de senha

**RF**

- O usuário deve poder recuperar sua senha, informando seu email;
- O usuário deve receber e-mail com instruções de recuperação de senha;
- O usuário deve poder resetar sua senha;

**RNF**

- Utilizar Mailtrap para testar envio de e-mails em desenvolvimento
- Utilizar Amazon SES para envios em produção;
- O envio de e-mails devem acontecer em segundo plano (background job);

**RN**

- O link enviado por e-mail para resetar senha, deve expirar em 2h;
- O usuário precisa confirmar a nova senha ao resetar sua senha;

# Atualização do perfil

**RF**

- O usuário deve poder atualizar seu perfil, sendo seu nome, email e senha

**RN**

- O usuário não pode alterar seu e-mail para um e-mail já uttilizado
- Para atualizar sua senha, o usuário deve informar a senha antiga
- Para atualizar sua senha, o usuário deve confirmar a nova senha

# Formulário de proposta

**RF**

- O usuário não precisa estar autenticado para envio dos dados
- O formulário deve compor os seguintes campos: nome, e-mail, fone, whatsApp, quilometragem, cidade do veículo, observação, foto do carro (anexo), lista com opções de motivos da venda do carro
- Os dados do formulário devem persistir no banco de dados da aplicação
- Deve ser informado ao vendedor o número da proposta criada, para posterior consulta, após a submissão do formulário
- Para usuários que informarem o e-mail, deve ser enviado notificação com o número da proposta

**RNF**

- Os dados de novas propostas devem ser armazenadas no Postgres;
- Utilizar Amazon S3 para armazenar anexos (imagens) em produção;
- Utilizar Amazon SES para envios em produção;

**RN**

- Os dados de e-mail, Whatsapp, observação e foto do carro são opcionais
- Os demais dados do formulário são obrigatórios
- O vendeddor receberá número da proposta criada para consulta 

# Consulta de proposta (Confirmar esta funcionalidade)

**RF**

**RNF**

**RN**


# Painel do comprador

**RF**

- O usuário deve poder visualizar as propostas não concluídas;
- O painel deve ser composto por quadros que agrupam propostas com status em comum, sendo estes: Aguardando análise, Em análise, Em Negociação, Aguardando aprovação

**RNF**

- As propsotas em aberto devem ser armazenados em cache;
- As notificações de novas propostas devem ser armazenadas no MongoDB;
- As notificações de novas propostas devem ser enviadas em tempo-real em Socket.io;

**RN**

- A notificação deve ter um status de lida ou não lida para que o comprador possa controlar (???);

# Painel do avaliador

**RN**

**RNF**

**RN**

# Processo das propostas

**RF**

- O usuário deve poder listar todas os propostas cadastradas, filtrando por período de consulta;
- O usuário deve poder listar todas os propostas cadastradas, filtrando por status;
- O usuário deve poder listar todas os propostas cadastradas, filtrando por modelo de carro;
- O usuário deve poder listar todas os propostas cadastradas, filtrando por cidade e bairro;
- O usuário deve poder listar a proposta cadastrada, filtrando pela placa do carro;
- O usuário deve poder criar uma nova proposta;
- O usuário deve poder alterar uma nova proposta, modificando seus status, observações e dados de vistoria;
- O sistema deve notificar o vendedor quando a proposta for atualizada para status que dependam de retorno do vendedor
- O sistema deve calcular prazo para primeiro contato do comprador para o dia seguinte

**RNF**

- A listagem de propostas deve ser armazenada em cache;
- Utilizar Mailtrap para testar envio de e-mails em desenvolvimento
- Utilizar Amazon SES para envios em produção;
- O envio de e-mails devem acontecer em segundo plano (background job);
- O valor do carro deve ser retornado por API que retorne dado da FIPE
- Os dados gerais do carro deve ser retornado por API fornecida pelo DETRAN ou terceiros homologados

**RN**

- Cada proposta deve possuir um status que represente a situação atual da proposta, sendo estes: Aguardando análise, Em análise, Em Negociação, Aguardando aprovação, Continuar Negociação, Aprovada e Reprovada;
- Propostas em cotinuação de negociação devem ser agendadas o novo contato com o cliente para tentar nova negociação
- Na proposta deve ser definido agendamento de visita de avaliação e formulário de avaliação
- O usuário não pode cadastrar uma proposta de um carro com proposta ativa;
- O usuário não pode cadastrar uma proposta com um modelo de carro inexistente;
- O usuário não pode cadastrar uma proposta com uma placa de carro inexistente;
