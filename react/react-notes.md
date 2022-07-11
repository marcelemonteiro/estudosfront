# React

## JSX

JSX é uma **extensão React para Javascript** que fornece uma maneira de estruturar a renderização de componentes usando uma sintaxe parecida com HTML (parece um acoplamento de tags HTML com JS). 

Para inserir qualquer expressão JSX basta colocar entre chaves ({ }).

```jsx
return )
	<div>{arr.map(el => <p>{el}</p>}</div>
);
```

JSX também é uma **expressão**, portanto é possível utilizá-la dentro de blocos de condição if/if else e também em laços de repetifição for/while, pode ser atribuída a uma variável, passada como argumentos para uma função e ser retornada por uma função.

Curiosidade: O JSX representa objetos. O Babel compila o JSX para chamadas `React.createElement()`.   

## Elementos

Elementos são os menores blocos de contrução de aplicativos React. Um elemento descreve o que você quer ver na tela. 

O React DOM é responsável por atualizar o DOM para exibir os elementos React.

O React somente atualiza o necessário, pois é React DOM compara o elemento novo e seus filhos com os anteriores e somente aplica as modificações necessárias na DOM para levá-lo ao estado necessário.

## Componentes

Os componentes permitem você dividir a UI (Interface do usuário) em partes **independentes e reutilizáveis.**  

Eles são como funções JS, aceitam argumentos (props) e retornam elemento React.

```jsx
export default function meuComponente(props) {
	return <p>Olá</p>
}
```

Um componente pode ser descrito como uma função JS, mas também pode ser utilizado com classes. 

<aside>
💡 Sempre inicie os nomes dos componentes com letra MAIÚSCULA, para são serem confundidos com tags do DOM pelo React.

</aside>

<aside>
💡 Todos os componentes React tem que agir como funções puras em relação às suas props. Ou seja, não é possível alterar o valor de um prop.

</aside>

### State

É um propriedade do componente onde colocamos dados que, quando mudarmos, devem causar um nova renderização. 

```jsx
this.setState((state, props) => {
	counter: state.counter + props
});
```

<aside>
💡 O state nunca deve ser alterado diretamente, sempre use **setState()** para alterar o valor do state.

</aside>

<aside>
💡 As atualizações do state podem ser assíncronas. O React pode agrupar várias chamadas setState() em uma única atualização. Como o this.props e o this.state podem ser atualizados de forma assíncrona, você não deve confiar em seus valores para calcular o próximo state.

</aside>

<aside>
💡 O state é uma propriedade local, ou seja, não é acessível a nenhum outro componente → Fluxo de dados top-down ou unidirecional.

</aside>

### Children

São os elementos filhos de um componente. Podem ser acessados a partir das props. 

```jsx
<Component>Blá</Component>
// "Blá" = props.children
```

## Eventos

<aside>
💡 Para evitar um comportamento padrão → `event.preventDefault()`

</aside>

### Bind

Em Javascript os métodos da classe não são vinculados por padrão. Se você esquecer de fazer o bind de um método (handleClick, por ex) e passá-lo para um onClick, o this será undefined quando a função for chamada. 

No construtor: `this.handleClick = this.handleClick.bind(this)`

Um forma de contornar isso e não precisar do bind é usando arrow function: `onClick={() => this.handleClick()}`

Mas uma callback diferente vai ser criada toda vez que o componente for renderizado!

<aside>
💡 Para evitar que um componente seja renderiado basta retornar null.

</aside>

```jsx
// ex: O Componente só será renderizado quando tiver uma determinada prop
if (!props.nome) {
	return null;
}
```

## Lista de elementos

Basta iterar com uma função `map()`. 

<aside>
💡 Cada item gerado dessa forma deve ter uma **key**. Ela serve para ajudar o React a identificar quais itens sofreram alterações.

</aside>

## Formulários

**Componentes controlados →** Componente que renderiza um formulário também controla o que acontece nesse formulário nas entradas subsequentes do usuário. Um input cujo valor é controlado pelo React dessa maneira é chamado de componente controlado. 

Em React o input, textarea e select funcionam de forma semelhante. Os três possuem uma propriedade **value**. 

## Elevando o state (state lift)

O **compartilhamento do state** é alcançado ao movê-lo para o elemento pai comum aos componentes que precisam dele. 

## State x Props

**State →** utilizado para valores dinâmicos.

**Props →** utilizados para passar valores entre componentes. São valores que os componentes recebem do componente pai. São como argumentos de uma função.

## Hooks

São uma nova adiação ao React 16.8. Eles permitem que você use o state e outros recursos do React sem escrever uma classe. 

Hooks são basicamente funções que permitem a você ligar-se aos recursos do state e ciclo de vida do React a partir de componentes funcionais. 

O React fornece alguns hooks, mas você também pode criar os seus próprios. 

### Regras dos hooks

- Apenas chame hooks no nível mais alto do código. Não chame dentro de loops, condições ou funções aninhadas.
- Apenas chame hooks em componentes funcionais, nunca de funções comuns.

### Beneficíos dos hooks

- Reutilizar lógicas de state (hooks costumizados)
- Não usar classes kkkkkkk

### Effect hook

Permite executar **efeitos colaterias** (operação que podem afetar outros componentes e não podem ser feita durante a renderização, ex: obtenção de dados [data fetching], subscriptions ou mudanças manuais na DOM) em componentes funcionais. 

Ele funciona exatamente como os ciclos de vida componentDidMount, componentDidUpdate e componentWillAmount combinados. E é executado depois da primeira renderização e depois de toda atualização. 

<aside>
💡 **Efeitos com limpeza:** Em uma classe geralmente você configura uma subscription no componentDidMount e limpa no componentWillAmount. Com hooks basta retornar uma função que o React irá executá-la quando for a hora de limpar (quando o component desmonta).

</aside>

<aside>
💡 **“Pulando” efeitos:** Você pode dizer ao React para pular a aplicação de um efeito se certos valores não tiverem mudado entre as renderizações. Para fazer isso, passe um array como segundo argumento opcional ao useEffect().

</aside>

```jsx
useEffect(() => {

}, [x]}
```