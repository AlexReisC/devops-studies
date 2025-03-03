# Shell Script
Shell Script é uma linguagem de script usada para automatizar tarefas no terminal do Linux/Unix.

Um **Shell Script** é um arquivo contendo comandos do terminal que podem ser executados como um programa. Ele usa interpretadores como `bash`, `sh` ou `zsh`.

## Introdução

### Criando um shell script
1.Crie um arquivo arquivo `.sh`:
```bash
touch meu_script.sh
```

2. Abra o arquivo no editor.
3. Adicione o código:
```bash
#!/bin/bash
echo "Olá mundo!"
```
Shell scripts começam com um `shebang`, ele informa que o script deve ser interpretado pelo Bash. Você pode usar outra interpretador shell como `#!/bin/sh`.

`echo` é um comando usado para exibir uma mensagem no terminal.

4. Dê permissão de execução ao script:
```bash
chmod +x meu_script.sh
```

5. Execute o script:
```bash
./meu_script.sh
```

### Variáveis e Entrada do Usuário
Podemos criar variáveis e interagir com o usuário:
```bash
#!/bin/bash
nome="Alex"
echo "Olá, $nome!"

echo "Qual é o seu nome?"
read usuario
echo "Bem-vindo, $usuario!"
```
Variáveis são definidas com `=` sem espaços ao redor dp `=`. Para usar uma variável colocamos `$` antes de seu nome. Podemos fazer atribuições do tipo:
```bash
pais=Brasil
novo_pais=$pais
```

O comando `read` permite capturar uma entrada do usuário.

### Condicionais
```bash
#!/bin/bash
echo "Digite um número"
read numero

if [ $numero -gt 10 ]; then
    echo "O númeor é maior que 10."
else
    echo "O número é menor ou igual a 10."
fi
```
No shell script usamos `[]` para testar condições. Operadores comuns são:
* -eq -> igual a (==)
* -ne -> diferente de (!=)
* -gt -> maior que (>)
* -lt -> menor que (<)
* -ge -> maior ou igual (>=)
* -le -> menor ou igual (<=)
* -a -> AND (operador lógico)
* -o -> OR (operador lógico)

### Laços de repetição

**For loop**
```bash
#!/bin/bash
for i in {1..5}; do
    echo "Número: $i"
done
```

**While loop**
```bash
#!/bin/bash
contador=1
while [ $contador -le 5 ]; do
    echo "Contador: $contador"
    ((contador++))
done
```
Usamos `((expressão++))` para incrementar valores.

### Funções
Podemos criar funções:
```bash
#!/bin/bash
diz_ola() {
    echo "Olá, $1!"
}

diz_ola "Alex"
diz_ola "Maria"
```
O `$1` é usado para indicar o primeiro argumento passado, e não está restrito ser usado em funções.

### Trabalhando com arquivos e diretórios
Criar, ler e manipular arquivos:
```bash
#!/bin/bash
echo "Criando um arquivo..."
echo "Este é um arquivo de teste." > teste.txt

echo "Conteúdo do arquivo:"
cat teste.txt
```
A expressão `echo "texto" > texto.txt` escreve um text dentro de um arquivo.

`cat`é usado para exibir o conteúdo de um arquivo.

Existem muitos outros comandos e coisas possiveís que se pode fazer comm shell script mas esta é uma introdução básica.
