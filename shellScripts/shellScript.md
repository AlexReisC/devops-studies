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

4. Dê permissão de execução ao script:
```bash
chmod +x meu_script.sh
```

5. Execute o script:
```bash
./meu_script.sh
```

### Variáveis e Entrada do Usuário
```bash
#!/bin/bash
nome="Alex"
echo "Olá, $nome!"

echo "Qual é o seu nome?"
read usuario
echo "Bem-vindo, $usuario!"
```

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

### Funções
```bash
#!/bin/bash
diz_ola() {
    echo "Olá, $1!"
}

diz_ola "Alex"
diz_ola "Maria"
```

### Trabalhando com arquivos e diretórios
```bash
#!/bin/bash
echo "Criando um arquivo..."
echo "Este é um arquivo de teste." > teste.txt

echo "Conteúdo do arquivo:"
cat teste.txt
```
