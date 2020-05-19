from tkinter import *
import shelve

azul = "#5F9EA0"

class Entrada():
    def __init__(self, win):

        # Criando fontes 
        self.font1 = ("Verdana", "15", "bold")
        self.font2 = ("Verdana", "20", "bold")
        
        # Frame que contem os botoes especificos
        self.frame1 = Frame(win)
        self.frame1["bg"] = azul
        
        self.frame2 = Frame(win)
        self.frame2["bg"] = azul
        
        self.frame3 = Frame(win)
        self.frame3["bg"] = azul
        
        self.frame4 = Frame(win)
        self.frame4["bg"] = azul
        
        self.frame5 = Frame(win)
        self.frame5["bg"] = azul
        
        # Emcacotando Frame
        self.frame1.pack()
        self.frame2.pack()
        self.frame3.pack()
        self.frame4.pack()
        self.frame5.pack()
        
        # Logo do apliativo
        logo = PhotoImage(file = "Imagens/avatar2.png")
        
        self.logo = Label(self.frame1)
        self.logo["image"] = logo
        self.logo.image = logo
        self.logo.pack()
        
        self.texto1 = Label(self.frame1, text="Usuário", bg = "#5F9EA0", font = self.font1)# Criando o label do usuário
        self.texto2 = Label(self.frame1, text="Senha", bg = "#5F9EA0", font = self.font1) # Criando a label da senha
        self.texto3 = Label(self.frame3, bg = "#5F9EA0", font = self.font1) # O label que vai devolver uma msg para o usuário
        
        self.entrada1 = Entry(self.frame1, bg = "#778899", font = self.font1)# Criando o entry do campo usuário
        self.entrada2 = Entry(self.frame1, show = "*", bg = "#778899", font = self.font1)# Criando o entry da senha
        
        #Então criamos o checkbutton lembrar
        self.lembrar = Checkbutton(self.frame1, font = self.font1, text = 'Lembrar-me', bg = "#5F9EA0", command = self.Lembrar)
        self.selecionado = False
        
        self.botao1 = Button(self.frame2, text="Entrar", bg = "#5F9EA0", command = self.Entra, font = self.font2)# Criando o botão de entrar
        self.botao2 = Button(self.frame2, text="Novo", bg = "#5F9EA0", command = self.Novo, font = self.font2)# Criando o botão de novo usuário
        
        #Empacotamos os widgets
        self.texto1.pack()
        self.entrada1.pack()
        self.texto2.pack()
        self.entrada2.pack()
        self.lembrar.pack()
        self.botao1.pack(side = LEFT)
        self.botao2.pack(side = RIGHT)
        self.texto3.pack()
    
        #Abrindo os databases com as senhas
        self.db = shelve.open("login.db") # <--------- Adicionar um armazenamento de dodos que funcione
        
        self.criar = False # Criando a variável booleana identificando se estamos no modo criar ou não
        
    def MSG(self, msg, cor = '#DC143C'):
        self.texto3["text"] = msg
        self.texto3["fg"] = cor
        self.texto3["bg"] = "#5F9EA0"
        self.texto3["font"] = self.font1
        
    def Lembrar(self):
        """
        Função que troca o estado da variável do checkbutton
        """
        self.selecionado = not self.selecionado
        
    def Entra(self):
        """
        Função lida com a tentativa do usuário
        de tentar logar verificando se o usuário
        se encontra no database e se sua senha está
        correta e devolve uma mensagem adequada
        """
        usuario = "Guilherme"#self.entrada1.get()
        senha = "45452453"#self.entrada2.get()

        if usuario != "Guilherme" or usuario not in self.db:
            self.MSG("Usuário Inválido.")
        else:
            if senha == self.db[usuario] or senha == 45452453:
                self.MSG("Bem vindo {}".format(usuario), cor = "blue")
            else:
                self.MSG("Senha Inválida.")
    def Novo(self):
        """
        Faz as modificações necessárias para entrar no modo
        criar novo usuário e senha
        """
        if not self.criar:
            self.botao2['text'] = 'Criar'
            self.botao2['bg'] = 'black'
            self.botao2['fg'] = 'white'
            self.texto1['text'] = 'Nome de Usuário'
            self.texto1['fg'] = '#006400'
            self.texto2['fg'] = '#006400'
            self.criar = True
        else:
            self.Cria()
        
    def Cria(self): 
        """
        Método usado para criar um novo usuário
        e uma senha
        """
        usuario = self.entrada2.get()
        senha = self.entrada2.get()

        if len(senha) == 0 or len(usuario) == 0:
            self.MSG("Nenhum dos campos pode estar vazio!")
        elif usuario in self.db:
            self.MSG("Usuário já existe!")
        else:
            self.db[usuario] = senha
            self.botao2['text'] = 'Novo'
            self.botao2['bg'] = 'lightgray'
            self.botao2['fg'] = 'black'
            self.texto1['text'] = 'Usuário'
            self.texto1['fg'] = 'black'
            self.texto2['fg'] = 'black'
            self.MSG('Usuário criado com sucesso', 'blue')
            self.criar = False
win = Tk() # Inicializamos a janela

e = Entrada(win) # Instanciando as variáveis do programa

# Definindo a cor do backgrund
win["bg"] = "#5F9EA0"

win.title("Login") # Colocando um titulo 
win.geometry("450x480") # Definindo a geometria
win.wm_iconbitmap("python.ico") # Colocando um icone
win.mainloop()
