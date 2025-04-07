# aula06pilha

Começando com as classes No e Pilha que foram fornecidas
class No:
    def __init__(self, valor):
        self.valor = valor
        self.proximo = None

class Pilha:
    def __init__(self):
        self.topo = None

    def push(self, valor):
        Adiciona um valor na pilha
        novo_no = No(valor)
        novo_no.proximo = self.topo
        self.topo = novo_no

    def pop(self):
         Remove um valor do topo da pilha
        if self.topo is not None:
            removido = self.topo
            self.topo = self.topo.proximo
            return removido.valor
        raise Exception("Pilha vazia.")

    def peek(self):
        # Acessa o valor no topo sem remover
        if self.topo is not None:
            return self.topo.valor
        raise Exception("Pilha vazia.")

    def is_empty(self):
        # Verifica se a pilha está vazia
        return self.topo is None

# Função para reverter strings usando a pilha
def reverter_string(string):
    pilha = Pilha()  # Instanciando uma pilha

     Colocar os caracteres da string na pilha
    for caractere in string:
        pilha.push(caractere)

    Retirar os caracteres da pilha para formar a string invertida
    string_invertida = ""
    while not pilha.is_empty():
        string_invertida += pilha.pop()

    return string_invertida

# Testando o programa com várias strings
testes = [
    "Olá mundo!",      # String simples
    "12345",           # Números
    "!@#$%",           # Caracteres especiais
    "Com espaços.",    # Com espaços
    "Emoji 😃🛠️"       # Testando emojis
]

print("Testando reversão de strings:\n")
for teste in testes:
    print(f"Original: {teste}")
    print(f"Invertida: {reverter_string(teste)}\n")
