Trabalho de Raciocínio Lógico Algorítmico - RLA

Nosso programa irá mostrar no HTML, por meio da tag document.write(), os dados requeridos na proposta do trabalho, (calcule a média simples vetorial, ordene corretamente o vetor média e apresentar a quantidade de alunos aprovados e reprovados.), na execução do trabalho em grupo iniciamos aprendendo a lógica de programação no JavaScript para compreender o que a proposta estava requerindo, estava pedindo.

Primeiramente declaramos uma variável chamada  turma ela será uma array que irá conter os dados dos alunos como: nome do aluno, a nota da 1° avaliação(denominada como nota1), a nota da 2º avaliação(denominada como nota2), e a media do aluno que será determinada pela soma da nota1 e nota2 dividido(/) por 2.

 let turma = {nome: "nomeDoAluno"}

Esta é a nossa array turma, ela contém somente o nomes dos alunos por que as notas serão fornecidas pelo usuário por meio de um prompt, e adicionadas a arry. A média segue o mesmo princípio contudo ela não será fornecida pelo usuário ela será determinada pela soma da nota1 e nota2 dividido(/) por 2.

Para que o usuario coloque as notas de todos os alunos nos criamos um laço de repatição for(), que irar ficar em um "loop" até que o usuario tem fornecido as duas notas de todos os aluno ficando desta forma:

    for(let aluno of turma) {
        aluno.nota1 = parseFloat(prompt("Digite a nota da Avaliação 1 do aluno: " + aluno.nome));
            while(isNaN(aluno.nota1) || aluno.nota1 < 0 || aluno.nota1 > 10) {
                aluno.nota1 = parseFloat(prompt("Resposta fornecida está Inválida! Digite novamente uma nota de 0 a 10 para o aluno: " + aluno.nome))
            };

        aluno.nota2 = parseFloat(prompt("Digite a nota da Avaliação 2 do aluno: " + aluno.nome));
            while(isNaN(aluno.nota2) || aluno.nota2 < 0 || aluno.nota2 > 10) {
                aluno.nota2 = parseFloat(prompt("Resposta fornecida está Inválida! Digite novamente uma nota de 0 a 10 para o aluno: " + aluno.nome))
            };

        aluno.media = (aluno.nota1 + aluno.nota2) / 2;
    }

Nesta linha( 
    aluno.nota1 = parseFloat(prompt("Digite a nota da Avaliação 1 do aluno: " + aluno.nome));
        while(isNaN(aluno.nota1) || aluno.nota1 < 0 || aluno.nota1 > 10) {
            aluno.nota1 = parseFloat(prompt("Resposta fornecida está Inválida! Digite novamente uma nota de 0 a 10 para o aluno: " + aluno.nome))
        }; 
)

Nós estamos adicionando a aluno o atributo nota 1, que será adicionada a nossa arry turma, o parseFloat(...) determina que ele pode receber uma respos com ponto flutuante dentro dele nostemos o nosso prompt que irá pedir para o usuario digite a nota do do aluno na primeira avaliação, este é o nosso prompt, dentro dele tem o aluno.nome, ele, irá ate a nossa arry e pegara o nome do aluno na pasição 0, e como estamos em um laçõ for() toda vez que ele iniciar uma nova "rodada" o valor de aluno já será outro assim fazendo com que cada aluno receba as suas notas.

Logo abaixo nos temos um while, ele está aqui para ser um autenticação segura para o codigo não ter nenhuma brecha, qual brecha seria? uma letra ou carctere especial, ou não conter nada o usuario acabou dando enter sem querer que seria o "isNaN"(( is not a number ) isso nao é um numero ), numeros acima de 10(dez) ou abaixo de 0(zero) como estamos nos referindo de notas com limite de nota. Caso uma dessas condições tenha sido atendida ele ira roda o prompt com a menssagem( "Resposta fornecida está Inválida! Digite novamente uma nota de 0 a 10 para o aluno: " + aluno.nome ), isto se repete para a segunda nota.

Nesta linha ainda dentro do laço for() que está pedindo as notas dos alunos nos temos a linha( aluno.media = (aluno.nota1 + aluno.nota2) / 2; ), ela irá calcular a média do aluno com base nas notas que o suario forneceu via prompt, e irá adicionar a arry turma.

importante resatar que aluno.nota1, aluno.nota2 e aluno.media estão sendo nos blocos{} de cada nome na arry turma. 

Finalizando o laço for() que pede ao usuario as notas de todos os aluno o codigo ira segir para a contagem de aprovados e reprovados.

    let aprovados = 0;
    let reprovados = 0;

    for(let i = 0; i < turma.length; i++){
        if(turma[i].media > 5){
            aprovados++;
        }else{
            reprovados++;
        }
    }

primeiro nos declaramos as variaveis "aprovados" e "reprovados" inicialmente com 0(zero). logo depois ele inicia um laço for() que ira verifivar se o aluno teve a media acima de 5(cinco), caso o aluno tem ela sera aprvovado, caso o aluno não tenha conseguido atingir uma nota acima de 5 ele sera reprovado os "aprovados++" servem para imcrementar aluno passou acresenta +1 a variavel aprovados, aluno não passou acresenta +1 a variavel reprovados. O ( turma[i].media > 5 ) ele atua para que a cada repetição do codigo o if ferifique individualmente cada aluno na arry turma.

Para a ordenação das medias a proposta requisita que o grupo não utilize metodos de ordenação prontos, a proposta tambem dá duas alternativas para o grupo escolher( o método bolha ou o método de ordenação por seleção) o grupo decidio optar pelo método bolha.

    for(let i = 0; i < turma.length -1; i++){
        for(let j = 0; j < turma.length -1 -i; j++){
            if(turma[j].media > turma[j+1].media){
            let aux = turma[j]
            turma[j] = turma[j+1]
            turma[j+1] = aux
            }
        }
    }

No método bolha o laço for() ele ira compara o primeiro com o seguinte se o seguinte for menor que primeiro o primeiro "sobe", é o que nos estamos fazendo no laço for(...) acima. Para que todas as médias estarão ordenadas da menor para a maior nos criamos dois for() um dentro do outro dentro do segundo for() nos temos um if(...) que vai comparar se o os numeros, para ajudar nesta comparação criamos uma variavel axiliar para gurdar temporariamente o valor do maior numero enquanto ele recebe outro valor