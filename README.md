# Tutorial Didático de Tkinter com Python

## Construindo Interfaces Gráficas com Python

**Material didático para aulas de programação**

> Baseado conceitualmente no tutorial **Python GUI Programming: Your Tkinter Tutorial**, da Real Python, adaptado e reorganizado para fins didáticos.
> Fonte de referência: [Real Python — Python GUI Programming: Your Tkinter Tutorial](https://realpython.com/python-gui-tkinter/?utm_source=chatgpt.com)

---

# 1. O que é Tkinter?

Até agora, muitos programas Python são executados no terminal:

```text
Digite seu nome: Dany
Olá, Dany!
```

Esse modelo é chamado de **interface de linha de comando**, ou CLI (*Command Line Interface*).

Com Tkinter podemos criar uma **interface gráfica**, ou GUI (*Graphical User Interface*).

Uma GUI permite que o usuário interaja com o programa utilizando:

* janelas;
* botões;
* caixas de texto;
* menus;
* listas;
* campos de entrada;
* caixas de diálogo;
* imagens;
* elementos visuais.

Em outras palavras:

```text
Programa tradicional

Usuário → Terminal → Python


Programa com GUI

Usuário
   ↓
Janela
   ↓
Botões / Campos / Menus
   ↓
Python
```


```mermaid
flowchart LR

    subgraph GUI["Programa com GUI"]
        direction TB

        G1["Usuário"]
        G2["Janela"]
        G3["Botões / Campos / Menus"]
        G4["Python"]

        G1 --> G2
        G2 --> G3
        G3 --> G4
    end

    subgraph CLI["Programa tradicional"]
        direction TB

        C1["Usuário"]
        C2["Terminal"]
        C3["Python"]

        C1 --> C2
        C2 --> C3
    end

    style GUI fill:#ffffff,stroke:#dddddd,stroke-width:1px
    style CLI fill:#ffffff,stroke:#dddddd,stroke-width:1px

    style G1 fill:#e3f2fd,stroke:#c5d9e8,stroke-width:1px
    style G2 fill:#e3f2fd,stroke:#c5d9e8,stroke-width:1px
    style G3 fill:#e3f2fd,stroke:#c5d9e8,stroke-width:1px
    style G4 fill:#e3f2fd,stroke:#c5d9e8,stroke-width:1px

    style C1 fill:#e3f2fd,stroke:#c5d9e8,stroke-width:1px
    style C2 fill:#e3f2fd,stroke:#c5d9e8,stroke-width:1px
    style C3 fill:#e3f2fd,stroke:#c5d9e8,stroke-width:1px
---

# 2. O que é Tkinter?

**Tkinter** é a biblioteca padrão do Python para criação de interfaces gráficas.

Ela funciona como uma interface Python para o toolkit gráfico **Tk**.

Uma das principais vantagens é que, em uma instalação adequada do Python, normalmente não precisamos instalar uma biblioteca externa para começar.

O Tkinter funciona em diferentes sistemas operacionais, incluindo:

* Windows
* Linux
* macOS

Isso torna o Tkinter interessante para aplicações desktop simples e para o ensino de programação de interfaces gráficas.

---

# 3. O modelo mental do Tkinter

Antes de começar a programar, é importante entender quatro conceitos:

```text
WINDOW
  │
  ├── FRAME
  │    ├── LABEL
  │    ├── ENTRY
  │    └── BUTTON
  │
  └── FRAME
       ├── LABEL
       └── TEXT
```

Podemos pensar em uma aplicação Tkinter como uma árvore de componentes.

## Principais conceitos

| Conceito     | Função                             |
| ------------ | ---------------------------------- |
| `Tk`         | Janela principal                   |
| `Frame`      | Agrupa componentes                 |
| `Label`      | Exibe texto                        |
| `Button`     | Executa uma ação                   |
| `Entry`      | Entrada de texto de uma linha      |
| `Text`       | Entrada de texto de várias linhas  |
| `Canvas`     | Área para desenhos                 |
| `ttk`        | Widgets com aparência mais moderna |
| `mainloop()` | Mantém a aplicação executando      |

---

# 4. Primeiro programa Tkinter

Vamos começar pelo menor programa possível.

```python
import tkinter as tk

window = tk.Tk()

window.mainloop()
```

Execute o programa.

Você deverá obter uma janela vazia.

---

# 5. Entendendo o código

## Importação

```python
import tkinter as tk
```

Estamos importando a biblioteca Tkinter.

O `as tk` cria um apelido.

Assim podemos escrever:

```python
tk.Tk()
```

em vez de:

```python
tkinter.Tk()
```

---

# 6. Criando a janela

```python
window = tk.Tk()
```

`Tk()` cria a janela principal da aplicação.

Podemos visualizar:

```text
tk.Tk()
   │
   └── cria a janela principal
```

A variável `window` passa a representar essa janela.

---

# 7. O que é `mainloop()`?

O comando:

```python
window.mainloop()
```

é fundamental.

Ele inicia o **loop de eventos** da aplicação.

Depois que a janela aparece, o programa precisa ficar observando eventos como:

* clique do mouse;
* teclado;
* movimentação do mouse;
* fechamento da janela;
* seleção de componentes;
* comandos dos botões.

Podemos imaginar:

```text
              ┌───────────────┐
              │   Tkinter     │
              │  mainloop()   │
              └───────┬───────┘
                      │
          ┌───────────┼───────────┐
          ↓           ↓           ↓
       clique       teclado     fechar
```

Sem `mainloop()`, a aplicação gráfica não permanecerá funcionando normalmente.

---

# 8. Adicionando nosso primeiro widget

Um **widget** é um componente visual da interface.

Vamos criar um `Label`.

```python
import tkinter as tk

window = tk.Tk()

label = tk.Label(
    text="Olá, Tkinter!"
)

label.pack()

window.mainloop()
```

Agora temos:

```text
┌──────────────────────────┐
│                          │
│       Olá, Tkinter!      │
│                          │
└──────────────────────────┘
```

---

# 9. O que é um Label?

O `Label` é utilizado para apresentar informações ao usuário.

Por exemplo:

```python
label = tk.Label(
    text="Nome:"
)
```

Podemos utilizá-lo para:

* títulos;
* mensagens;
* instruções;
* resultados;
* textos informativos.

---

# 10. Criando uma interface simples

Vamos melhorar nosso exemplo.

```python
import tkinter as tk

window = tk.Tk()

title = tk.Label(
    text="Meu primeiro programa"
)

title.pack()

message = tk.Label(
    text="Estou aprendendo Tkinter!"
)

message.pack()

window.mainloop()
```

A interface terá aproximadamente:

```text
┌────────────────────────────────┐
│                                │
│      Meu primeiro programa     │
│                                │
│    Estou aprendendo Tkinter!   │
│                                │
└────────────────────────────────┘
```

---

# 11. Personalizando um Label

Podemos alterar propriedades do widget.

```python
label = tk.Label(
    text="Olá!",
    foreground="white",
    background="blue"
)
```

Também podemos utilizar as abreviações:

```python
label = tk.Label(
    text="Olá!",
    fg="white",
    bg="blue"
)
```

---

# 12. Cores

Podemos utilizar nomes:

```python
bg="blue"
fg="white"
```

ou valores hexadecimais:

```python
bg="#1E90FF"
```

Exemplo:

```python
label = tk.Label(
    text="Tkinter",
    fg="white",
    bg="#1E90FF"
)
```

---

# 13. Fontes

Podemos especificar uma fonte:

```python
label = tk.Label(
    text="Tkinter",
    font=("Arial", 20)
)
```

Também podemos utilizar estilos:

```python
label = tk.Label(
    text="Título",
    font=("Arial", 20, "bold")
)
```

---

# 14. O widget Button

Um botão é criado com:

```python
button = tk.Button(
    text="Clique aqui"
)
```

Porém, somente criar o botão não é suficiente.

Precisamos colocá-lo na interface:

```python
button.pack()
```

Exemplo:

```python
import tkinter as tk

window = tk.Tk()

button = tk.Button(
    text="Clique aqui"
)

button.pack()

window.mainloop()
```

---

# 15. Botões precisam executar ações

A grande vantagem de uma GUI é a interação.

Queremos algo como:

```text
Usuário
   │
   │ clica
   ▼
[ Botão ]
   │
   ▼
função Python()
   │
   ▼
resultado
```

Para isso utilizamos **callbacks**.

---

# 16. Criando uma função

```python
def dizer_ola():
    print("Olá!")
```

Agora podemos associá-la ao botão:

```python
button = tk.Button(
    text="Clique aqui",
    command=dizer_ola
)
```

Programa completo:

```python
import tkinter as tk


def dizer_ola():
    print("Olá!")


window = tk.Tk()

button = tk.Button(
    text="Clique aqui",
    command=dizer_ola
)

button.pack()

window.mainloop()
```

---

# 17. Atenção ao `command`

Observe:

```python
command=dizer_ola
```

e não:

```python
command=dizer_ola()
```

O primeiro significa:

> "Quando o botão for clicado, execute essa função."

O segundo executaria a função imediatamente durante a criação do botão.

---

# 18. Capturando dados do usuário

Para receber uma pequena quantidade de texto utilizamos:

```python
Entry
```

Exemplo:

```python
entry = tk.Entry()

entry.pack()
```

Podemos criar:

```text
Nome:
┌────────────────────────────┐
│                            │
└────────────────────────────┘
```

---

# 19. Obtendo o conteúdo de Entry

O método:

```python
entry.get()
```

recupera o texto digitado.

Exemplo:

```python
import tkinter as tk


def mostrar_nome():
    nome = entry.get()
    print(nome)


window = tk.Tk()

entry = tk.Entry()
entry.pack()

button = tk.Button(
    text="Mostrar nome",
    command=mostrar_nome
)

button.pack()

window.mainloop()
```

---

# 20. Primeiro programa realmente interativo

Vamos agora apresentar o resultado na própria janela.

```python
import tkinter as tk


def mostrar_nome():
    nome = entry.get()
    resultado.config(text=f"Olá, {nome}!")


window = tk.Tk()

label = tk.Label(
    text="Digite seu nome:"
)

label.pack()

entry = tk.Entry()
entry.pack()

button = tk.Button(
    text="Enviar",
    command=mostrar_nome
)

button.pack()

resultado = tk.Label()
resultado.pack()

window.mainloop()
```

Fluxo:

```text
Usuário digita nome
        ↓
     Entry
        ↓
     Button
        ↓
  mostrar_nome()
        ↓
     Entry.get()
        ↓
 resultado.config()
```

---

# 21. Alterando um widget

Podemos alterar propriedades de um widget depois que ele foi criado.

Por exemplo:

```python
resultado.config(
    text="Olá!"
)
```

Também podemos utilizar:

```python
resultado.configure(
    text="Olá!"
)
```

`config()` e `configure()` podem ser utilizados para modificar opções do widget.

---

# 22. Widget Text

Quando precisamos trabalhar com várias linhas de texto, usamos:

```python
Text
```

Exemplo:

```python
text_box = tk.Text(
    width=40,
    height=10
)

text_box.pack()
```

A diferença principal é:

```text
Entry
┌───────────────────────┐
│ texto                 │
└───────────────────────┘
```

Enquanto:

```text
Text
┌───────────────────────┐
│ texto                 │
│ outra linha            │
│ mais uma linha         │
│                        │
└───────────────────────┘
```

---

# 23. Obtendo conteúdo de Text

Podemos utilizar:

```python
text_box.get("1.0", tk.END)
```

O índice:

```text
1.0
```

significa:

```text
linha 1, caractere 0
```

Exemplo:

```python
texto = text_box.get("1.0", tk.END)
```

---

# 24. Inserindo conteúdo

Em `Entry`:

```python
entry.insert(0, "Python")
```

Em `Text`:

```python
text_box.insert("1.0", "Olá, mundo!")
```

---

# 25. Apagando conteúdo

Para `Entry`:

```python
entry.delete(0, tk.END)
```

Para `Text`:

```python
text_box.delete("1.0", tk.END)
```

---

# 26. Frame

Quando uma aplicação começa a crescer, colocar todos os widgets diretamente na janela principal pode deixar o código difícil de organizar.

Para isso usamos `Frame`.

Um `Frame` é um **container**.

```python
frame = tk.Frame(window)
frame.pack()
```

Podemos colocar widgets dentro dele:

```python
label = tk.Label(
    frame,
    text="Nome:"
)

entry = tk.Entry(frame)

label.pack()
entry.pack()
```

Estrutura:

```text
Window
│
└── Frame
    ├── Label
    └── Entry
```

---

# 27. Por que usar Frame?

Imagine uma aplicação:

```text
┌───────────────────────────────┐
│         CADASTRO              │
│                               │
│ Nome:    [____________]       │
│ Email:   [____________]       │
│ Telefone:[____________]       │
│                               │
│       [ Salvar ]              │
└───────────────────────────────┘
```

Podemos dividir:

```text
Window
│
├── Frame título
│
├── Frame formulário
│
└── Frame botões
```

Isso melhora:

* organização;
* manutenção;
* reutilização;
* posicionamento;
* legibilidade.

---

# 28. Geometry Managers

Tkinter possui mecanismos para posicionar widgets.

Os principais são:

```text
pack()
grid()
place()
```

Eles são chamados de **Geometry Managers**.

---

# 29. `pack()`

O `pack()` organiza widgets de maneira relativamente simples.

Exemplo:

```python
label.pack()
button.pack()
```

Por padrão, os widgets são organizados verticalmente.

```text
┌───────────────────────┐
│       LABEL           │
│                       │
│       BUTTON          │
└───────────────────────┘
```

Podemos indicar uma direção:

```python
button.pack(side="left")
```

ou:

```python
button.pack(side="right")
```

---

# 30. Padding

Podemos adicionar espaço ao redor:

```python
button.pack(
    padx=10,
    pady=10
)
```

`padx` controla o espaço horizontal.

`pady` controla o espaço vertical.

---

# 31. `grid()`

O `grid()` organiza componentes em linhas e colunas.

É muito útil para formulários.

Exemplo:

```python
label_nome = tk.Label(
    text="Nome:"
)

label_nome.grid(
    row=0,
    column=0
)

entry_nome = tk.Entry()

entry_nome.grid(
    row=0,
    column=1
)
```

Visualmente:

```text
       coluna 0       coluna 1

linha 0   Nome:       [___________]

linha 1   Email:      [___________]

linha 2   Senha:      [___________]
```

---

# 32. Formulário usando Grid

```python
import tkinter as tk

window = tk.Tk()

tk.Label(
    window,
    text="Nome:"
).grid(row=0, column=0)

tk.Entry(
    window
).grid(row=0, column=1)

tk.Label(
    window,
    text="Email:"
).grid(row=1, column=0)

tk.Entry(
    window
).grid(row=1, column=1)

window.mainloop()
```

---

# 33. Padding com Grid

Também podemos usar:

```python
widget.grid(
    row=0,
    column=0,
    padx=10,
    pady=10
)
```

---

# 34. `place()`

O `place()` permite posicionamento por coordenadas.

Exemplo:

```python
button.place(
    x=100,
    y=50
)
```

É possível posicionar exatamente o widget.

Entretanto, deve ser utilizado com cuidado porque interfaces baseadas em coordenadas fixas podem apresentar problemas quando:

* a janela muda de tamanho;
* o sistema operacional muda;
* a fonte muda;
* a resolução muda;
* a interface precisa ser responsiva.

Para aplicações didáticas e formulários, `grid()` e `pack()` normalmente são opções melhores.

---

# 35. Regra importante sobre Geometry Managers

Evite utilizar diferentes geometry managers no **mesmo container**.

Por exemplo, não faça:

```python
label.pack()
button.grid(...)
```

na mesma janela.

Uma estratégia melhor é separar os componentes utilizando `Frame`.

```text
Window
│
├── Frame A → pack()
│
└── Frame B → grid()
```

Assim cada container possui sua própria estratégia de layout.

---

# 36. Eventos

Uma GUI é orientada a eventos.

Um evento pode ser:

* clique;
* tecla pressionada;
* movimento do mouse;
* entrada do mouse em uma região;
* saída do mouse;
* fechamento da janela.

Podemos pensar:

```text
EVENTO
   ↓
HANDLER
   ↓
FUNÇÃO
   ↓
AÇÃO
```

---

# 37. Eventos com `bind()`

Podemos utilizar `bind()` para associar eventos a funções.

Exemplo:

```python
def pressionou_tecla(event):
    print("Tecla pressionada!")


window.bind(
    "<Key>",
    pressionou_tecla
)
```

O argumento `event` contém informações sobre o evento.

---

# 38. Eventos do mouse

Exemplo:

```python
def clicou(event):
    print("Mouse clicado!")


window.bind(
    "<Button-1>",
    clicou
)
```

`<Button-1>` representa o clique com o botão esquerdo do mouse.

---

# 39. `command` versus `bind`

Uma distinção importante:

### `command`

Muito utilizado para ações de widgets como `Button`.

```python
button = tk.Button(
    text="Salvar",
    command=salvar
)
```

### `bind`

Utilizado para eventos mais gerais.

```python
window.bind(
    "<Return>",
    executar
)
```

Uma forma simples de memorizar:

```text
Button → command

Eventos gerais → bind()
```

---

# 40. Variáveis do Tkinter

Tkinter possui objetos especiais para representar valores da interface.

Os principais são:

```python
StringVar()
IntVar()
DoubleVar()
BooleanVar()
```

Por exemplo:

```python
nome = tk.StringVar()
```

Podemos associar ao `Entry`:

```python
entry = tk.Entry(
    textvariable=nome
)
```

Agora podemos obter:

```python
nome.get()
```

e alterar:

```python
nome.set("Dany")
```

---

# 41. Por que utilizar `StringVar`?

Considere:

```python
nome = tk.StringVar()

entry = tk.Entry(
    textvariable=nome
)
```

A variável passa a representar o estado daquele campo.

Podemos pensar:

```text
             StringVar
                │
        ┌───────┴───────┐
        ↓               ↓
      Entry          Python
```

Isso facilita a sincronização entre dados e interface.

---

# 42. Tkinter e programação orientada a objetos

Aplicações muito pequenas podem ser escritas diretamente.

Porém, à medida que o projeto cresce, é interessante utilizar classes.

Exemplo:

```python
import tkinter as tk


class App:
    def __init__(self, window):
        self.window = window

        self.label = tk.Label(
            window,
            text="Olá!"
        )

        self.label.pack()


window = tk.Tk()

app = App(window)

window.mainloop()
```

Agora a interface está organizada dentro de uma classe.

---

# 43. Por que utilizar classes?

Uma aplicação maior pode ter:

```text
App
│
├── tela principal
├── formulário
├── menu
├── banco de dados
├── eventos
└── funções
```

A orientação a objetos ajuda a separar responsabilidades.

---

# 44. Tkinter moderno: `ttk`

Tkinter possui também o módulo:

```python
tkinter.ttk
```

Ele fornece **themed widgets**.

Exemplo:

```python
import tkinter as tk
from tkinter import ttk
```

Agora podemos utilizar:

```python
label = ttk.Label(
    window,
    text="Olá!"
)
```

e:

```python
button = ttk.Button(
    window,
    text="Salvar"
)
```

Os widgets `ttk` geralmente apresentam uma aparência mais integrada ao sistema operacional.

---

# 45. `tkinter` versus `ttk`

Exemplo clássico:

```python
tk.Button(...)
```

Exemplo tematizado:

```python
ttk.Button(...)
```

Podemos utilizar ambos na mesma aplicação.

Uma prática recomendada é conhecer os dois modelos.

---

# 46. Caixa de diálogo

Tkinter também possui módulos auxiliares.

Por exemplo:

```python
from tkinter import messagebox
```

Podemos apresentar uma mensagem:

```python
messagebox.showinfo(
    "Informação",
    "Operação realizada!"
)
```

Ou um alerta:

```python
messagebox.showwarning(
    "Atenção",
    "Preencha todos os campos."
)
```

---

# 47. Perguntas ao usuário

Também podemos perguntar:

```python
resultado = messagebox.askyesno(
    "Confirmação",
    "Deseja continuar?"
)
```

O retorno será:

```python
True
```

ou:

```python
False
```

---

# 48. Exemplo: formulário de cadastro

Agora vamos juntar vários conceitos.

```python
import tkinter as tk
from tkinter import messagebox


def cadastrar():
    nome = entry_nome.get()
    email = entry_email.get()

    if not nome or not email:
        messagebox.showwarning(
            "Atenção",
            "Preencha todos os campos."
        )
        return

    messagebox.showinfo(
        "Cadastro",
        f"Cadastro realizado para {nome}."
    )


window = tk.Tk()

window.title("Cadastro")
window.geometry("400x250")

label_nome = tk.Label(
    window,
    text="Nome:"
)

label_nome.pack()

entry_nome = tk.Entry(
    window
)

entry_nome.pack()

label_email = tk.Label(
    window,
    text="Email:"
)

label_email.pack()

entry_email = tk.Entry(
    window
)

entry_email.pack()

button = tk.Button(
    window,
    text="Cadastrar",
    command=cadastrar
)

button.pack(pady=20)

window.mainloop()
```

---

# 49. Analisando a arquitetura

O programa possui:

```text
Janela
│
├── Label Nome
├── Entry Nome
├── Label Email
├── Entry Email
└── Button Cadastrar
```

Quando o usuário clica:

```text
Button
   ↓
cadastrar()
   ↓
entry.get()
   ↓
validação
   ↓
messagebox
```

Esse padrão aparece constantemente em aplicações GUI.

---

# 50. Projeto 1 — Conversor de temperatura

Vamos construir uma aplicação completa.

## Objetivo

O usuário informa uma temperatura em Celsius.

O programa converte para Fahrenheit.

A fórmula é:

```text
F = C × 9/5 + 32
```

---

# 51. Estrutura da aplicação

```text
┌─────────────────────────────────┐
│     Conversor de Temperatura    │
│                                 │
│ Celsius: [____________]         │
│                                 │
│       [ Converter ]             │
│                                 │
│ Resultado: 32 °F                │
└─────────────────────────────────┘
```

---

# 52. Código

```python
import tkinter as tk
from tkinter import ttk


def converter():
    celsius = float(celsius_entry.get())

    fahrenheit = celsius * 9 / 5 + 32

    resultado_label.config(
        text=f"{fahrenheit:.2f} °F"
    )


window = tk.Tk()

window.title("Conversor de Temperatura")

frame = ttk.Frame(
    window,
    padding=20
)

frame.grid()

ttk.Label(
    frame,
    text="Temperatura em Celsius:"
).grid(
    row=0,
    column=0,
    padx=5,
    pady=5
)

celsius_entry = ttk.Entry(
    frame
)

celsius_entry.grid(
    row=0,
    column=1,
    padx=5,
    pady=5
)

ttk.Button(
    frame,
    text="Converter",
    command=converter
).grid(
    row=1,
    column=0,
    columnspan=2,
    pady=10
)

resultado_label = ttk.Label(
    frame,
    text="Resultado:"
)

resultado_label.grid(
    row=2,
    column=0,
    columnspan=2
)

window.mainloop()
```

---

# 53. Melhorando o conversor

O código anterior possui um problema.

Se o usuário digitar:

```text
abc
```

teremos um erro:

```text
ValueError
```

Precisamos tratar a entrada.

---

# 54. Tratamento de erros

Podemos utilizar:

```python
try:
    celsius = float(
        celsius_entry.get()
    )
except ValueError:
    ...
```

Exemplo:

```python
def converter():
    try:
        celsius = float(
            celsius_entry.get()
        )

        fahrenheit = (
            celsius * 9 / 5 + 32
        )

        resultado_label.config(
            text=f"{fahrenheit:.2f} °F"
        )

    except ValueError:
        resultado_label.config(
            text="Digite um número válido."
        )
```

Agora nossa GUI é mais robusta.

---

# 55. Projeto 2 — Editor de texto

Um segundo projeto interessante é um pequeno editor.

Estrutura:

```text
┌─────────────────────────────────────┐
│ Arquivo                             │
├─────────────────────────────────────┤
│                                     │
│                                     │
│       Área de edição                │
│                                     │
│                                     │
├─────────────────────────────────────┤
│ Status                              │
└─────────────────────────────────────┘
```

Podemos utilizar:

```python
Text
```

para a área de edição.

---

# 56. Editor básico

```python
import tkinter as tk


window = tk.Tk()

window.title("Editor de Texto")

text_box = tk.Text(
    window,
    width=80,
    height=25
)

text_box.pack(
    padx=10,
    pady=10
)

window.mainloop()
```

Agora temos a base de um editor.

---

# 57. Salvando arquivos

Para trabalhar com arquivos podemos utilizar:

```python
from tkinter import filedialog
```

Depois:

```python
arquivo = filedialog.asksaveasfilename()
```

Podemos então utilizar o sistema de arquivos do Python:

```python
with open(
    arquivo,
    "w",
    encoding="utf-8"
) as file:

    file.write(
        text_box.get("1.0", tk.END)
    )
```

---

# 58. Abrindo arquivos

Podemos utilizar:

```python
arquivo = filedialog.askopenfilename()
```

Depois:

```python
with open(
    arquivo,
    "r",
    encoding="utf-8"
) as file:

    conteudo = file.read()
```

E colocar o conteúdo no `Text`:

```python
text_box.delete(
    "1.0",
    tk.END
)

text_box.insert(
    "1.0",
    conteudo
)
```

---

# 59. Estrutura conceitual de uma aplicação Tkinter

Uma aplicação pode ser pensada em quatro partes:

```text
┌─────────────────────────────────┐
│           INTERFACE             │
│                                 │
│ Labels / Buttons / Entries      │
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│             EVENTOS             │
│                                 │
│ click / key / menu / etc.       │
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│             LÓGICA              │
│                                 │
│ funções / regras / validações   │
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│             DADOS               │
│                                 │
│ arquivos / banco / APIs         │
└─────────────────────────────────┘
```

Essa separação é muito importante quando o projeto começa a crescer.

---

# 60. Exercícios

## Exercício 1 — Primeira janela

Crie uma aplicação que mostre:

```text
Olá, mundo!
```

---

## Exercício 2 — Saudação

Crie uma interface contendo:

```text
Nome: [____________]

[ Cumprimentar ]

Olá, João!
```

O nome deve ser obtido através de um `Entry`.

---

## Exercício 3 — Calculadora

Crie uma calculadora capaz de realizar:

```text
Número 1: [________]

Número 2: [________]

[ Somar ]

Resultado: ________
```

Implemente:

* soma;
* subtração;
* multiplicação;
* divisão.

---

## Exercício 4 — Validação

Modifique o exercício anterior para impedir:

* campos vazios;
* divisão por zero;
* valores que não sejam números.

---

## Exercício 5 — Formulário

Crie um formulário com:

```text
Nome
Email
Telefone
Cidade
```

e um botão:

```text
[ Cadastrar ]
```

Após o cadastro, apresente uma mensagem.

---

# 61. Desafio — Sistema de notas

Construa uma aplicação que receba:

```text
Aluno: [____________]

Nota 1: [____________]

Nota 2: [____________]

Nota 3: [____________]

[ Calcular média ]
```

O programa deve calcular:

```text
Média = (nota1 + nota2 + nota3) / 3
```

Depois deverá apresentar:

```text
Média: 8.5

Situação: APROVADO
```

Considere:

```text
média >= 7 → APROVADO

média >= 5 e < 7 → RECUPERAÇÃO

média < 5 → REPROVADO
```

---

# 62. Desafio intermediário — Lista de tarefas

Crie uma aplicação de tarefas:

```text
┌─────────────────────────────────────┐
│             TAREFAS                 │
│                                     │
│ [ Estudar Tkinter          ]        │
│                                     │
│ [ Adicionar ]                       │
│                                     │
│ ┌───────────────────────────────┐   │
│ │ Estudar Python                │   │
│ │ Fazer exercício               │   │
│ │ Preparar projeto              │   │
│ └───────────────────────────────┘   │
│                                     │
│ [ Remover ]                         │
└─────────────────────────────────────┘
```

O projeto deve permitir:

* adicionar tarefas;
* remover tarefas;
* limpar a lista;
* selecionar uma tarefa.

---

# 63. Desafio avançado — Cadastro de alunos

Crie uma aplicação contendo:

```text
Nome
Matrícula
Curso
Nota
```

O programa deve permitir:

* cadastrar;
* listar;
* editar;
* remover;
* pesquisar.

Uma possível arquitetura:

```text
App
│
├── Interface
│
├── Cadastro
│
├── Validação
│
└── Dados
```

---

# 64. Checklist de aprendizagem

Ao finalizar este tutorial, o aluno deverá ser capaz de:

* [ ] explicar o que é uma GUI;
* [ ] explicar o que é Tkinter;
* [ ] criar uma janela;
* [ ] utilizar `Tk()`;
* [ ] utilizar `mainloop()`;
* [ ] criar `Label`;
* [ ] criar `Button`;
* [ ] criar `Entry`;
* [ ] criar `Text`;
* [ ] utilizar `Frame`;
* [ ] organizar widgets com `pack()`;
* [ ] organizar widgets com `grid()`;
* [ ] compreender `place()`;
* [ ] utilizar `command`;
* [ ] utilizar `bind()`;
* [ ] trabalhar com eventos;
* [ ] recuperar dados de `Entry`;
* [ ] modificar widgets;
* [ ] utilizar `StringVar`;
* [ ] utilizar `messagebox`;
* [ ] utilizar `filedialog`;
* [ ] conhecer `tkinter.ttk`;
* [ ] organizar aplicações maiores com classes;
* [ ] construir uma aplicação gráfica funcional.

---

# 65. Mapa mental do Tkinter

```text
                         TKINTER
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
       JANELA             WIDGETS           EVENTOS
          │                 │                 │
        Tk()        ┌───────┼────────┐      bind()
          │         │       │        │        │
     mainloop()   Label   Entry    Button   command
                  │       │        │
                  │       │        └── ação
                  │       │
                  │       └── entrada
                  │
                  └── informação

                            │
                            ▼

                     LAYOUT / GEOMETRIA
                            │
                 ┌──────────┼──────────┐
                 │          │          │
               pack()     grid()     place()

                            │
                            ▼

                         ttk
                            │
                   Widgets tematizados

                            │
                            ▼

                     APLICAÇÕES
                            │
                ┌───────────┼───────────┐
                │           │           │
            Conversor    Editor     Cadastro
```

---

# 66. Projeto final do curso

Como projeto final, recomenda-se desenvolver uma aplicação desktop completa.

Uma sugestão é:

## Sistema de Cadastro de Alunos

A aplicação deverá possuir:

### Tela principal

```text
┌────────────────────────────────────────┐
│          SISTEMA ACADÊMICO             │
├────────────────────────────────────────┤
│ Nome:       [____________________]     │
│ Matrícula:  [____________________]     │
│ Curso:      [____________________]     │
│                                        │
│ [Cadastrar] [Editar] [Excluir]         │
│                                        │
│ ┌────────────────────────────────────┐ │
│ │ Nome       Matrícula       Curso   │ │
│ │ João       001             Python  │ │
│ │ Maria      002             Flutter │ │
│ └────────────────────────────────────┘ │
└────────────────────────────────────────┘
```

---

# 67. Requisitos do projeto final

A aplicação deverá:

1. Criar uma janela principal.
2. Utilizar `Frame`.
3. Utilizar `Label`.
4. Utilizar `Entry`.
5. Utilizar `Button`.
6. Utilizar pelo menos um widget `ttk`.
7. Utilizar `grid()` para organização.
8. Utilizar funções para os eventos.
9. Validar os dados.
10. Apresentar mensagens ao usuário.
11. Permitir cadastrar registros.
12. Permitir excluir registros.
13. Permitir editar registros.
14. Separar interface e lógica sempre que possível.

---

# 68. Organização recomendada do projeto

Quando a aplicação crescer, podemos organizar os arquivos:

```text
projeto_tkinter/
│
├── main.py
│
├── interface.py
│
├── models.py
│
├── services.py
│
├── database.py
│
└── assets/
    └── imagens/
```

Para projetos pequenos, entretanto, não é necessário criar essa estrutura imediatamente.

O mais importante é primeiro compreender:

```text
janela
  ↓
widget
  ↓
layout
  ↓
evento
  ↓
função
  ↓
resultado
```

---

# 69. O ciclo de uma aplicação Tkinter

O fluxo fundamental pode ser resumido assim:

```text
1. Importar Tkinter
        ↓
2. Criar janela
        ↓
3. Criar widgets
        ↓
4. Organizar widgets
        ↓
5. Definir eventos
        ↓
6. Executar mainloop()
        ↓
7. Usuário interage
        ↓
8. Evento é disparado
        ↓
9. Função é executada
        ↓
10. Interface é atualizada
```

---

# 70. Resumo final

Tkinter permite transformar programas Python tradicionais em aplicações gráficas.

Os conceitos fundamentais são:

```text
Tk()
```

Cria a janela principal.

```text
Label
```

Apresenta informações.

```text
Entry
```

Recebe uma linha de texto.

```text
Text
```

Recebe múltiplas linhas.

```text
Button
```

Executa ações.

```text
Frame
```

Organiza componentes.

```text
pack()
grid()
place()
```

Controlam o posicionamento.

```text
command
```

Liga um widget a uma função.

```text
bind()
```

Permite trabalhar com eventos.

```text
ttk
```

Fornece widgets tematizados.

```text
mainloop()
```

Mantém a aplicação executando e processando eventos.

---

# 71. A ideia mais importante

Não pense em Tkinter apenas como uma coleção de comandos.

Pense em uma aplicação Tkinter como um **sistema orientado a eventos**:

```text
             USUÁRIO
                │
                ▼
        ┌───────────────┐
        │   INTERFACE   │
        └───────┬───────┘
                │
             EVENTO
                │
                ▼
        ┌───────────────┐
        │    CALLBACK   │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │ LÓGICA PYTHON │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │ ATUALIZA GUI  │
        └───────────────┘
```

Esse modelo mental é a base para compreender aplicações desktop em Tkinter.

---

# Referência principal

**Real Python — Python GUI Programming: Your Tkinter Tutorial**

https://realpython.com/python-gui-tkinter/

O artigo original aborda progressivamente a criação da primeira janela, widgets, gerenciamento de geometria, eventos, conversor de temperatura e editor de texto. Este material reorganiza esses conceitos em uma sequência mais adequada para utilização em aula e acrescenta exercícios e desafios.
