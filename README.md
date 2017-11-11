### Introdução
*Novamente, desculpa pela formatação. Eu tentei tê-la mais concisa possível. Sinta-se à vontade para brincar com Playground, e se detectar problemas, comente abaixo. Para eu consertá-la o mais rápido possível. .*


### 1. Inicializador Conveniente
> Ex) Pega o número das mãos e dos pés de um humano

```swift
// Jeito Original
class Humano {
  var dedoMao: Int
  var dedoPe: Int

  init(dedoMao: Int, dedoPe: Int) {
    self.dedoMao = finger
    self.dedoPe = toe
  }
}

var joao = Humano(dedoMao: 10, dedoPe: 10)
joao.dedoMao // 10
joao.dedoPe // 10
```

A maior parte dos humanos tem 10 dedos nas mãos e nos pés. Não serial legal termos uma pré inicialização, ou um valor padrão ?

```swift
// Jeito legal
class Humano {
  var dedoMao: Int
  var dedoPe: Int
  init(dedoMao: Int, dedoPe: Int) {
    self.dedoMao = dedoMao
    self.dedoPe =
  }
  convenience init() {
    self.init(dedoMao: 10, toe: 10) // referência ao bloco inicializador acima
  }
}

var matheus = Human()
matheus.dedoMao // 10
matheus.dedoPe // 10
```

### 2. Conversões de Tipo (Type Cast) 
> Ex) Merge [Int] and [String] array into [Any]

Quando você faz uma chamada de API do Facebook, você receberia uma série de URLs de fotos de perfil [String] e o número de gostos [Int] para cada um.

Você quer unir esses dois tipos diferentes de arrays em uma única matriz apenas por causa da portabilidade.

Lembre-se, expliquei a lógica na publicação anterior.

menos variáveis → menos problemas de vida (versão mais curta)

```swift
// Conversão superior (Upcasting) "as"
var curtidas = [123, 342, 231] as [Any]
var fotos = ["Praia", "Garotas", "Chill"] as [Any]
// misturando
for curtida in curtidas {
 fotos.append(curtida) }
fotos // ["Praia", "Garotas", "Chill", 123, 342, 231]
```

Você acabou de fazer uma conversão superior (upcast) dos dois arrays para o tipo Any, você acabou de mistura-los, Com o resultado você pode levar *tudo* em um único array chamado "fotos", não é legal isso ?

Agora é hora de realizar uma conversão inferior (downcast). Em outros palavras, hora de converter de [Any] → [String] or [Int]

```swift
// Cast inferior (Downcasting) "as?"
for i in fotos {
 if let numero = i as? Int {
  print(numero) } // 123, 342, 231

 if let string = i as? String {
  print(string) } // "Praia", "Garotas", "Chill"
}
```

### 3. Switch vs If-Else
> Ex) Recomendamos bebidas saudáveis para diferentes faixas etárias


### Agrupamento por idade
1-7: Leite

8-80: Refrigerante

81-150: Água

Além: ??

```swift
// Código Usual
var minhaIdade = 20
if minhaIdade >= 1 && minhaIdade <= 7 {
 print("🍼")
} else if minhaIdade >= 8 && minhaIdade <= 80 {
 print("🍺")
} else if minhaIdade >= 81 && minhaIdade <= 150 {
 print("🚿")
} else {
 print("Pera ai... Você ta vivo, sério ?")
}
```

Pare de repetir.

A propósito apenas para mostrar algo a respeito, Eu tenho pesquisado e encontrei a pessoa com mais anos de vida chegou aos 122 anos de idade e 164 dias de acorco com Wikipedia

De qualquer jeito, vamos focar

```swift
// Código TOP
switch myAge {
 case 2...7: print("🍼")
 case 8...80: print("🍺") // X procure o emoji certo
 case 81...150: print("🚿")
 default: print("Pera ai... Você ta vivo, sério ?")
}
```

### 4. Função com parâmetros customizáveis
> Ex) imprima a direção da viajem
> 
Imprime a origem e o destino de um viajante

```swift
func getD(origemUsuario: String, destinoUsuario: String) {
 print("de \(origemUsuario), para: \(destinoUsuario)")}
getD(origemUsuario: "🇺🇸", destinoUsuario: "🇰🇷") // de 🇺🇸 para: 🇰🇷
```

### 5. Parâmetros Variáveis
> Ex) procure o significado de múltiplas entradas

Então, você quer ter uma função que tenha valores de entradas infinitas??

Então vamos lá. 👌

```swift
var total: Double = 0
func media(numbers: Double...) -> Double {

  for numero in numeros { total += numero }

  return total / Double(numero.count) }

media(numbers: 1, 3, 5, 7, 11) // 5.4
media(numbers: 1, 4, 8, 16, 25) // 16.2
media(numbers: 111, 222, 333) // 249
```

### 6. EMOJI 👑
> Ex) Inspiração

Eu uso emoji com freqüência. Isso me permite expressar minha personalidade e meu caráter mais do que com o meu inglês limitado.

Quantas vezes você viu aqueles exemplos aborrecidos, "foo", "aClass", "bClass", "boo"?

Vamos apenas apimentar as coisas.

Mais uma vez, vamos focar.

```swift
// Tradicional
func oQueBobAma(primeiro: String, segundo: String) {
 print("Eu aproveito \(primeiro), e amo \(segundo) ") }
```

Ensinar a um filho de 3 anos a codificar em Swift 3

```swift
// 👶 Code
func meDigaOQueBobAma(💛: String, 💙: String) {
 print("I gosto de \(💛), e amo \(💙) ") }
meDigaOQueBobAma(💛: "teaching", 💙: "community")
```

### 7. Programação Funcional
> Ex) Quadrado de números de um array

```swift
// Maneira amplamente utilizada
var quadradoPrimeirosCincoInteirosPositivos: [Int] = []

for i in 1...5 { quadradoPrimeirosCincoInteirosPositivos.append(i * i) }

print(quadradoPrimeirosCincoInteirosPositivos) // [1, 4, 9, 16, 25]
```

Use “map”

```swift
let intervaloCincoNumeros = [Int](1...5)

let quadradoCincoNumeros = intervaloCincoNumeros.map { $0 * $0 }
quadradoCincoNumeros // [1, 4, 9, 16, 25]
```

### 8. Subscripts
> Ex) Encontrando Atalhos

```swift
// Jeito normal para acessar a propriedade
class DayOfWeek {
 var dias = ["Domingo", "Segunda", "Terça", "Quarta", "Quinta", "Sexta"]
}

var diaDaSemana = DiaDaSemana()
diaDaSemana.dias[0] // “Sun”
diaDaSemana.dias[1] // “Mon”
```

Jeito rápido para acessar “Sol” e “Lua”.

```swift
// Jeito Legal 🕶
class novoDiaSemana {
 var dias = ["Domingo", "Segunda", "Terça", "Quarta", "Quinta", "Sexta"]
 
 subscript(indice: Int) -> String {
  return dias[indice] }
}

var novoDiaSemana = NovoDiaSemana()
novoDiaSemana[0] // “Domingo”
novoDiaSemana[1] // “Segunda”
```

### 9. Propiedades Observadoras (Property Observers Observers) 
> Ex) Converte Fahrenheit para Celsius

```swift
// o que 99% faria
var celsius = 0

func converteFToC(F: Double) -> Double {
 return (F - 32) * (5 / 9) }

converteFToC(F: 300) // 148.9
```

De novo, não é necessário criar um função.

```swift
// willSet & didSet

var celsius: Double = 0
var fahrenheit: Double = 100 {
 willSet { print("Você está prestes a converter") }
 didSet { celsius = (fahrenheit - 32) * (5 / 9) } }

fahrenheit = 300 // "Você está prestes a converter"
celsius // 148.9

fahrenheit = 200 // "Você está prestes a converter"
celsius // 93.3
```

"WillSet" é executado imediatamente antes do valor Fahrenheit for definido. "DidSet" é executado imediatamente após o valor Fahrenheit ter sido definido.

### 10.Qual a sua dica para se tornar um ninja?
Agora é sua vez. Eu poderia ter concluído os restantes 10% do artigo. Mas, eu também quero aprender com você. Por favor, compartilhe seu jeito ninja secreto com essa amada comunidade.🎙

*“Ensinar é aprender. Ensinar não é transmitir conhecimentos”*

### Ultimas Observações
Bom pessoal é tudo um aprendizado novo pra mim, iniciei meus aprendizados em swift há apenas 5 meses, espero que eu possa estar trazendo algo relevante para vocês e que possamos estar melhorando a cada dia nessa jornada Pokemon.
Não se esqueçam de conferir o meu blog clicando [aqui](https://vikingscode.com "aqui"), lá tem outras dicas e coisas que vou abordar com o tempo.
Não se esqueçam de conferir o blog do Bob clicando [aqui](http://bobthedeveloper.io "aqui"), lá tem o melhor curso de swift que já fiz até hoje.
