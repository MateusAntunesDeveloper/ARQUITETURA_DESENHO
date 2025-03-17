# ARQUITETURA_DESENHO
ARQUITETURA_REDES_TKINTER_NEWW
import tkinter as Tkinter_func

class Aplicacao:
    def __init__(self, janela):
        self.janela = janela
        
        # Criando a segunda janela com Toplevel
        self.janela2 = Tkinter_func.Toplevel(janela)
        self.janela.title("Arquitetura de Rede - Janela 1")
        self.janela2.title("Detalhes - Janela 2")
        
        # Inicializando o canvas da Janela 1
        self.canvas = Tkinter_func.Canvas(self.janela, width=600, height=400)
        self.canvas.pack()

        # Adicionando componentes de rede na Janela 1
        self.servidor = self.canvas.create_rectangle(50, 100, 150, 150, fill="lightblue", outline="black")
        self.container = self.canvas.create_rectangle(200, 100, 300, 150, fill="lightgreen", outline="black")
        self.computador1 = self.canvas.create_rectangle(400, 50, 500, 100, fill="lightyellow", outline="black")
        self.computador2 = self.canvas.create_rectangle(400, 200, 500, 250, fill="lightyellow", outline="black")

        # Adicionando linhas de conexão
        self.canvas.create_line(150, 125, 200, 125, arrow=Tkinter_func.LAST)  # Conexão entre Servidor e Container
        self.canvas.create_line(300, 125, 400, 75, arrow=Tkinter_func.LAST)  # Conexão entre Container e Computador 1
        self.canvas.create_line(300, 125, 400, 225, arrow=Tkinter_func.LAST)  # Conexão entre Container e Computador 2
        
        # Adicionando texto nos componentes
        self.canvas.create_text(100, 125, text="Servidor", font=("Arial", 10))
        self.canvas.create_text(250, 125, text="Container", font=("Arial", 10))
        self.canvas.create_text(450, 75, text="Computador 1", font=("Arial", 10))
        self.canvas.create_text(450, 225, text="Computador 2", font=("Arial", 10))

        # Rótulo de informações da Janela 2
        self.info_label = Tkinter_func.Label(self.janela2, text="Clique em um componente para mais informações.", font=("Arial", 12))
        self.info_label.pack()

        # Binding dos componentes para mostrar as informações
        self.canvas.tag_bind(self.servidor, "<Button-1>", lambda e: self.mostrar_info("Servidor"))
        self.canvas.tag_bind(self.container, "<Button-1>", lambda e: self.mostrar_info("Container"))
        self.canvas.tag_bind(self.computador1, "<Button-1>", lambda e: self.mostrar_info("Computador 1"))
        self.canvas.tag_bind(self.computador2, "<Button-1>", lambda e: self.mostrar_info("Computador 2"))

    def mostrar_info(self, componente):
        # Atualiza o texto na Janela 2 com informações sobre o componente
        if componente == "Servidor":
            texto = "Servidor: Armazena e gerencia os dados da rede."
        elif componente == "Container":
            texto = "Container: Executa aplicações de forma isolada e portátil."
        elif componente == "Computador 1":
            texto = "Computador 1: Estação de trabalho conectada à rede."
        elif componente == "Computador 2":
            texto = "Computador 2: Outra estação de trabalho conectada à rede."
        else:
            texto = "Componente desconhecido."
        
        # Atualiza o rótulo de informações na Janela 2
        self.info_label.config(text=f"Componente: {componente}\n{texto}")

# Criação da Janela Principal
janela = Tkinter_func.Tk()

# Instanciando a classe Aplicacao e passando a Janela Principal
app = Aplicacao(janela)

# Iniciando o loop da interface gráfica
janela.mainloop()
