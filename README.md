import tkinter as tk
from tkinter import ttk

class AgendaCourseApp:
    def __init__(self, master):
        self.master = master
        self.master.title("Agenda de Course")

        self.frame = tk.Frame(self.master)
        self.frame.pack()

        self.label_date = tk.Label(self.frame, text="Date:")
        self.label_date.grid(row=0, column=0, padx=5, pady=5, sticky="w")
        self.entry_date = tk.Entry(self.frame)
        self.entry_date.grid(row=0, column=1, padx=5, pady=5)

        self.label_activite = tk.Label(self.frame, text="Activité:")
        self.label_activite.grid(row=1, column=0, padx=5, pady=5, sticky="w")
        self.entry_activite = tk.Entry(self.frame)
        self.entry_activite.grid(row=1, column=1, padx=5, pady=5)

        self.button_ajouter = tk.Button(self.frame, text="Ajouter", command=self.ajouter_activite)
        self.button_ajouter.grid(row=2, columnspan=2, padx=5, pady=5)

        self.listbox = tk.Listbox(self.frame, width=50)
        self.listbox.grid(row=3, columnspan=2, padx=5, pady=5)

    def ajouter_activite(self):
        date = self.entry_date.get()
        activite = self.entry_activite.get()
        if date and activite:
            self.listbox.insert(tk.END, f"{date}: {activite}")
            self.entry_date.delete(0, tk.END)
            self.entry_activite.delete(0, tk.END)
        else:
            tk.messagebox.showerror("Erreur", "Veuillez remplir tous les champs.")

def main():
    root = tk.Tk()
    app = AgendaCourseApp(root)
    root.mainloop()

if __name__ == "__main__":
    main()

