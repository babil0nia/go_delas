# Projeto_go_elas

## Descrição Geral do Sistema - Go Elas

## Problemática
Atualmente, as mulheres enfrentam grandes desafios no mercado de trabalho, pela falta de oportunidades, desigualdade de gênero ou falta de visibilidade. Muitas mulheres têm dificuldade em acessar vagas de emprego, crescer profissionalmente ou se manter em uma escala de trabalho que não é mais compatível quando se tem filhos. Diante deste cenário, a +delas surge como uma resposta para combater esses problemas, criando um espaço que facilita a autonomia financeira e pessoal das mulheres, oferecendo-lhes oportunidades para se destacarem em suas áreas de atuação.

## Solução
A plataforma Go Elas será um site que conecta mulheres prestadoras de serviços autônomos a pessoas que desejam contratar esses serviços. As mulheres terão a liberdade de escolher o dia e a hora em que desejam trabalhar, desde que haja uma negociação feita com o contratante que deseja o serviço da mesma. O sistema permitirá que elas definam suas áreas de atuação, horários disponíveis e condições de trabalho, promovendo a autonomia e flexibilidade. Além disso, a +delas tem como visão atrair mulheres desempregadas, aumentando suas oportunidades de geração de renda e contribuindo para o crescimento da economia local.


## Com a nossa plataforma conseguiremos aumentar o desenvolvimento econômico e pessoal:
Oferecendo oportunidades para que as mulheres possam ter uma autonomia financeira, um ambiente voltado para a educação e gerenciamento de renda e expandir suas habilidades e conexões profissionais.

Empoderamento Pessoal:
Promover a confiança e a autoestima das mulheres, incentivando-as a alcançar seus objetivos.

Autonomia: Proporcionar às mulheres a capacidade de gerenciar seu próprio tempo e trabalho, aumentando sua independência financeira de acordo com sua rotina e limitações.

## Cadastro.
A usuária se cadastra com informações básicas (nome, e-mail, área de atuação) e cria uma senha.

## Jornada do empreemdedor (Caso seja prestadora) (Opcional).
A usuária acessa uma seção chamada Jornada do Empreendedor, com conteúdos rápidos e essenciais, por exemplo:
- Como se comunicar com seus clientes, Auto-Divulgação, Precificação de Serviços e assusntos voltados a educação financeira.
- Tarefa Prática: Ao final de cada resumo, ela realiza um quiz sobre o resumo, e no final, registra o seu serviço utilizando o que foi visto na trilha.
(Vamos usar essa tarefa da trilha como o nosso default pra definir a avaliação inicial pra quem não tem nenhum serviço prestado)

## Criação de perfil. 
- Perfil básico: A usuária monta um perfil com as informações obtidas nas atividades da trilha.

## Funcionalidades

## 📚 Trilhas de Aprendizado de Soft Skills

Conteúdos estruturados para ajudar as usuárias a desenvolverem habilidades interpessoais e comportamentais, como:

Comunicação eficaz

Resolução de conflitos

Postura em entrevistas de emprego

## 💰 Educação Financeira

Materiais exclusivos para ensinar conceitos básicos de gestão financeira e planejamento, ajudando as usuárias a ter uma visão de futuro para seu dinheiro.

## 🎓 Mentorias Personalizadas

Sessões focadas em orientação para:

Elaboração de currículos

Preparação para entrevistas de emprego

Outras áreas essenciais para a inserção no mercado de trabalho

## 🗺️ Mapeamento de Colaboradoras de Serviços

Filtragem de colaboradoras de serviços de acordo com sua região, utilizando a API do Google.

## 📅 Calendário de Eventos

Listagem de todos os eventos importantes na cidade do Recife, permitindo agrupar todas as atividades relevantes em um só lugar.

## 🤖 Chatbot para Acessibilidade

Assistente virtual para auxiliar no letramento digital e oferecer suporte às usuárias.

## ⭐ Avaliação de Serviços

Opção para que os usuários avaliem os serviços prestados, determinando um número de estrelas e deixando comentários.

## 🎯 Testes Vocacionais (Apenas se o Senac entrar no projeto)

Ferramenta para ajudar as usuárias a identificarem seus pontos fortes e áreas de interesse profissional.

## 👩‍💻 Fórum Feminino

Um espaço seguro para que as mulheres troquem experiências, vivências e se ajudem no processo de desenvolvimento pessoal e profissional.

## Agendamento e contratação.
- Agendamento facilitado: Assim que um cliente encontra o serviço desejado e prestadora, ele entra em contato com a mesma através do botão do whatsapp para definir o melhor horário para ambos.

## Avaliação e feedback.
- Após a prestação do serviço, o cliente tem a opção de avaliar a usuária, adicionando uma nota ou comentário curto.
- Perfil Atualizado: A avaliação aparece no perfil da usuária, ajudando a construir sua reputação e atrair novos clientes.

## 🚀 Como Rodar o Aplicativo  

Para executar o projeto localmente utilizando Docker, siga os passos abaixo:  

1. Certifique-se de ter o [Docker](https://www.docker.com/) e o [Maven](https://maven.apache.org/) instalados em sua máquina.  
2. No diretório raiz do projeto, execute o seguinte comando para limpar e empacotar a aplicação:  
   mvn clean package
Em seguida, construa e inicie os contêineres Docker com o comando:
bash
docker compose up --build

### 🏆 Principais Tecnologias  

- ## Fluxos de dados.
- Os diagramas abaixo representam os principais fluxos operacionais da plataforma +delas, detalhando tanto a experiência dos usuários (clientes e prestadoras de serviços) quanto as conexões internas entre as entidades do banco de dados, desde o cadastro até a finalização do serviço contratado.

![Fluxo de dados de cadastro ](https://github.com/babil0nia/maisDelas/blob/master/+Delas%20(3).jpg?raw=true)

- ## Fluxos de dados da contratação do serviço.
  
 ![Fluxo de dados de cadastro ](https://github.com/babil0nia/maisDelas/blob/master/%2BDelas%20Contrata%C3%A7%C3%A3o.jpg)

  
## Banco de dados
```mermaid
erDiagram
    usuario {
        int idusuario PK
        string nome
        string email
        string senha
        string telefone UNIQUE
        string tipo
        string rua
        string bairro
        string cep
        timestamp datacriacao
        char documento UNIQUE
        string portfolio
        string genero
    }

    favorito {
        int idfavorito PK
        int idservicos FK
        int idusuario FK
        timestamp datafavoritamento
    }

    servicos {
        int idservicos PK
        text descricao
        decimal preco
        string titulo
        timestamp datacriacao_servico
        string categoria
        int idfavorito FK
    }

    contratacao {
        int idcontratacao PK
        int idusuario FK
        int idservicos FK
        string status
        timestamp datacontratacao
        string comentarios
    }

    contratacao_has_usuarios {
        int contratacao_idcontratacao PK, FK
        int usuarios_id PK, FK
    }

    avaliacao {
        int idavaliacao PK
        int idcontratacao FK
        int nota
    }

    interacao_ia {
        int idinteracao PK
        int idusuario FK
        text pergunta
        text resposta
        timestamp data_interacao
    }

    usuario ||--o{ favorito : "salva"
    usuario ||--o{ contratacao : "realiza"
    usuario ||--o{ interacao_ia : "interage"
    servicos ||--o{ contratacao : "é contratado"
    favorito }|--|| servicos : "referencia"
    contratacao ||--o{ avaliacao : "recebe"
    contratacao ||--|{ contratacao_has_usuarios : "envolve"
    usuario ||--|{ contratacao_has_usuarios : "participa"
