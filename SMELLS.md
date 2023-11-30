# Smells

Página que cataloga os odores disponíveis em <a href="refactoring improving the design of existing code.pdf">link</a>.

Documentação feita por @luisafzn, @camillevitroia e @KamillaStreb. Posteriormente aprimorado pelo Leandro Dalla Nora.

Também está disponível no seguinte site: https://refactoring.guru/pt-br/refactoring/smells

## Duplicated Code

Se você vir a mesma estrutura de código em mais de um lugar, você pode ter certeza de que seu programa será melhor se
você encontrar uma maneira de unificá-los. O problema de código duplicado mais simples é quando você tem a mesma
expressão em dois métodos de mesma classe. Então tudo o que você precisa fazer é extrair o método e invocar o código de
ambos lugares.
- Bad example:
```
int array_a[];
int array_b[];
 
int sum_a = 0;

for (int i = 0; i < 4; i++)
   sum_a += array_a[i];

int average_a = sum_a / 4;
 
int sum_b = 0;

for (int i = 0; i < 4; i++)
   sum_b += array_b[i];

int average_b = sum_b / 4;
```

- Good example:
```
int calc_average_of_four(int* array) {
   int sum = 0;
   for (int i = 0; i < 4; i++)
       sum += array[i];

   return sum / 4;
}

int array1[];
int array2[];

int average1 = calc_average_of_four(array1);
int average2 = calc_average_of_four(array2);
```

## Long Method

Os programas objeto que vivem melhor e por mais tempo são aqueles com métodos curtos. Desde os primórdios da
programação, as pessoas perceberam que quanto mais longo for um procedimento, mais
mais difícil é entender.

[Exemplo](https://makolyte.com/refactoring-the-long-method-code-smell/)


## Long Parameter List

Nos nossos primeiros dias de programação, fomos ensinados a passar como parâmetros tudo o que era necessário para uma
rotina. Objetos mudam essa situação porque se você não tem algo que precisa,
você sempre pode pedir a outro objeto para obtê-lo para você. Assim com objetos você não passa em todas as necessidades
do método; em vez disso, você passa o suficiente para que o método possa obter tudo o que precisa. Em programas
orientados a objetos, listas de parâmetros tendem a ser muito menores do que em programas tradicionais.

[Exemplo](https://luzkan.github.io/smells/long-parameter-list) 


## Large Class

Quando uma classe está tentando fazer muito, geralmente aparece como muitas variáveis de instância. Quando a classe tem
muitas variáveis de instância, o código duplicado não pode ficar muito atrás. Por estes motivos, ela é a união destes e demais fatores.

Isto ocorre pois é muito mais fácil adicionar o que falta em uma classe já existente.

Seus problemas consistem em: dificuldade na leitura e entendimento do código, dificuldade em editar e testar o código.


## Divergent Change

A mudança divergente ocorre quando uma classe é comumente alterada de diferentes maneiras para diferentes razões.
Qualquer alteração para lidar com uma variação deve mudar uma única classe, e toda a digitação na nova classe deve
expressar a variação.

[Exemplo](https://luzkan.github.io/smells/divergent-change)

## Shotgun Surgery

É semelhante à mudança divergente, mas é o oposto. Você cheira isso quando toda vez você faz um tipo de mudança, você
tem que fazer muitas pequenas mudanças em muitas classes diferentes. Quando as mudanças estão em todo lugar, elas são
difíceis de encontrar, e é fácil perder uma importante mudança.

* A mudança divergente é uma classe que sofre muitos tipos de mudanças, e a cirurgia de espingarda é uma mudança que
  altera muitas classes.

## Feature Envy

O ponto principal dos objetos é que eles são uma técnica para empacotar dados com os processos usados nesses dados. Um
smell clássico é um método que parece mais interessado em uma classe diferente daquela que ele realmente está dentro. O
foco mais comum da envy são os dados. Perdemos a conta das vezes
vimos um método que invoca meia dúzia de métodos de obtenção em outro objeto para calcular algum valor.

## Data Clumps

Os data items tendem a ser como crianças; eles gostam de andar em grupos juntos. Muitas vezes você verá os mesmos três
ou quatro itens de dados juntos em vários lugares: campos em algumas classes, parâmetros em muitas assinaturas de
métodos. Grupos de dados que ficam juntos realmente deveriam ser transformados em seu próprio objeto. O primeiro passo é
procurar onde os aglomerados aparecem como campos.

## Primitive Obsession

Tipos primitivos são seus blocos de construção. Os registros sempre trazem uma certa quantidade de despesas gerais. Eles
podem significar tabelas em um banco de dados ou podem ser difíceis de criar quando quiser para apenas uma ou duas
coisas. Uma das coisas valiosas sobre os objetos é que eles borram ou até quebram a linha entre o primitivo e as turmas
maiores.

## Switch Statements

O problema com as instruções switch é essencialmente o da duplicação. Muitas vezes você encontra a mesma instrução
switch espalhada por um programa em lugares diferentes. Se você adicionar uma nova cláusula para o switch, você precisa
encontrar todos esses switch, instruções e alterá-los.

## Parallel Inheritance Hierarchies

Toda vez que existir uma subclasse de uma classe, vai ter que ter uma subclasse de outra. Você pode reconhecer esse
smell porque os prefixos dos nomes de classe em uma hierarquia são os mesmos que os prefixos em outra hierarquia.

## Lazy Class

Classes que não estão sendo bem utilizadas precisam ser eliminadas.

## Speculative Generality

Exclua métodos ou classes em que os únicos usuários são casos de teste (não utilizados).

## Temporary Field

Objeto no qual uma variável de instância é definida apenas em determinadas circunstâncias. Exemplo: um algoritmo precisa
de várias variáveis. Como o implementador não queria passar uma lista enorme de parâmetros, ele os colocou em campos,
que só são válidos durante o algoritmo, depois tornam-se inúteis.

## Message Chains

Quando um cliente solicita vários objetos, como uma longa linha de métodos getThis, ou como uma sequência de temps, o
cliente está acoplado à estrutura da navegação.

## Middle Man

Uma das principais características dos objetos é o encapsulamento - ocultando detalhes internos do resto do mundo. O
encapsulamento geralmente vem com delegação. No entanto, isso pode ir longe demais. Você olha para a interface de uma
classe e descobre que metade dos métodos estão delegando a esta outra classe.

## Inappropriate Intimacy

Às vezes as aulas se tornam muito íntimas e passam muito tempo investigando cada parte íntimas dos outros. Podemos não
ser puritanos quando se trata de pessoas, mas achamos que nossas aulas devem seguir regras estritas e puritanas. As
classes super intimistas precisam ser desfeitas como os amantes eram nos tempos antigos.

## Alternative Classes with Different Interfaces

Use Rename Method em qualquer método que faça a mesma coisa, mas tenha assinaturas diferentes para o que eles fazem.
Muitas vezes isso não vai longe o suficiente. Nestes casos as classes ainda não estão fazendo o suficiente.

## Incomplete Library Class

Construtores de classes de biblioteca raramente são oniscientes. Não os culpamos por isso; afinal podemos raramente
descobrir um projeto até que o tenhamos construído, então os construtores de bibliotecas têm um trabalho muito difícil.
O problema é que muitas vezes é de má forma, e geralmente impossível, modificar uma classe de biblioteca para fazer algo
que você gostaria que ele fizesse.

## Data Class

São classes que possuem campos, obtendo e configurando métodos para os campos e nada mais. Essas classes são detentoras
de dados burros e quase certamente estão sendo manipuladas com muitos detalhes por outras classes. Em estágios iniciais,
essas classes podem ter campos públicos.
As classes de dados são como crianças. Eles estão bem como ponto de partida, mas para participar como um adulto objeto,
eles precisam assumir alguma responsabilidade.

## Refused Request

As subclasses herdam os métodos e dados de seus pais. Mas e se eles não quiserem ou precisarem do que lhes é dado? Eles
recebem todos esses grandes presentes e escolhem apenas alguns para brincar. Então nós dizemos que se o legado recusado
estiver causando confusão e problemas, siga o conselho tradicional. No entanto, não sinta que precisa fazer isso o tempo
todo. Nove em cada dez vezes este cheiro é muito fraco para ser vale a pena limpar. O cheiro de legado recusado é muito
mais forte se a subclasse estiver reutilizando o comportamento, mas não deseja suportar a interface da superclasse.

## Comments

A razão pela qual mencionamos comment aqui é que os comentários costumam ser usados como desodorante. É surpreendente a
frequência com que você olha densamente código comentado e observe que os comentários estão lá porque o código é ruim.
Os comentários nos levam a um código ruim que tem todos os cheiros podres que discutimos no restante deste artigo.

- Bad example:
```
int func(int t, int v[t]){ // v é vetor e t é tamanho
    int aux, m; // m é mediana
    for(i = 0; i < t-1; i++){
        for(j = i+1; j < t; j++){
            if(v[i] > v[j]){
                aux = v[i];
                v[i] = v[j];
                v[j] = aux;
            }
        }
    }

    if(t%2){
        m = v[t/2];
    } else {
        m = (v[t/2-1]+v[t/2])/2;
    }
    return m;
}    
```

- Good example:
```
int calcula_mediana(int tamanho, int vet[tamanho]){
    int aux, mediana; 

    for(i = 0; i < tamanho-1; i++)
    {
        for(j = i+1; j < tamanho; j++)
        {
            if(v[i] > v[j])
            {
                aux = v[i];
                v[i] = v[j];
                v[j] = aux;
            }
        }
    }

    if(tamanho%2)
    {
        mediana = v[tamanho/2];
    }
    else 
    {
        mediana = (v[tamanho/2-1]+v[tamanho/2])/2;
    }
    
    return mediana;
}    
```