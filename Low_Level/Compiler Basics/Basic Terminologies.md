## Frontend

- Lexical Analysis (Scanning) => takes Linear Stream of characters and turns them into Tokens (Words)
- Parser => takes Tokens and forms a Tree (Abstract Syntax Tree)(AST)
## Backend

- Binding or Resolution => For each identifier we find out where that name is defined and wire the two together. This is where scope comes into play
- Intermediate Representation (IR) =>code isn’t tightly tied to either the source or destination form (This allows support for multiple Languages)
- Constant folding => if some expression always evaluates to the exact same value, we can do the evaluation at compile time and replace the code for the expression with its result. If the user typed in: 
```
pennyArea = 3.14159 * (0.75 / 2) * (0.75 / 2);
``` 
We can do all of that arithmetic in the *compiler* and change the code to:
```
pennyArea = 0.4417860938;
```

- virtual machine code => Instead of instructions for some real chip (faster but ties code to specific Architecture), produce code for a hypothetical, idealized machine. called “p-code” for “portable”, but today, we generally call it *bytecode* because each instruction is often a single byte long. This makes you also write a VM to translate your Bytecode to Machine Code.

## Special Type of Compilers

- *Single-Pass Compilers* => restrict the design of the language. You have no intermediate data structures to store global information about the program, and you don’t revisit any previously parsed part of the code. That means as soon as you see some expression, you need to know enough to correctly compile it.
- Source-to-Source (Transcompiler) => in the back end, instead of doing all the work to lower the semantics to some primitive target language, you produce a string of valid source code for some other language that’s about as *high level* as yours.
- JIT => On the end user’s machine, when the program is loaded—either from source in the case of JS, or platform-independent bytecode for the JVM and CLR—you compile it to native for the architecture their computer supports. 