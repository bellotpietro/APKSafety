# APKSafety
Una interfaz para navegar de forma segura 
git clone https://github.com/tu-usuario/social-media-safe-box.git
cd social-media-safe-box
touch social_media_safe_box.py
nano social_media_safe_box.py
git add social_media_safe_box.py
git commit -m "Add social media safe box script"
git push origin main
https://github.com/tu-usuario/social-media-safe-box
import tkinter as tk
from tkinter import messagebox
from PyQt5 import QtWidgets, QtWebEngineWidgets

# Lista de URLs permitidas (whitelist)
ALLOWED_URLS = [
    "https://www.facebook.com",
    "https://www.instagram.com",
    "https://www.twitter.com",
]

# Función para verificar si una URL está permitida
def is_url_allowed(url):
    for allowed_url in ALLOWED_URLS:
        if allowed_url in url:
            return True
    return False

# Función para abrir una red social en el navegador integrado
def open_social_media(url):
    if is_url_allowed(url):
        browser.setUrl(QtCore.QUrl(url))
    else:
        messagebox.showerror("Error", "Este enlace no está permitido.")

# Interfaz gráfica con Tkinter
root = tk.Tk()
root.title("Caja de Seguridad para Redes Sociales")
root.geometry("400x300")

# Botones para redes sociales
facebook_btn = tk.Button(root, text="Abrir Facebook", command=lambda: open_social_media("https://www.facebook.com"))
facebook_btn.pack(pady=10)

instagram_btn = tk.Button(root, text="Abrir Instagram", command=lambda: open_social_media("https://www.instagram.com"))
instagram_btn.pack(pady=10)

twitter_btn = tk.Button(root, text="Abrir Twitter", command=lambda: open_social_media("https://www.twitter.com"))
twitter_btn.pack(pady=10)

# Navegador integrado con PyQt
app = QtWidgets.QApplication([])
window = QtWidgets.QWidget()
layout = QtWidgets.QVBoxLayout()
browser = QtWebEngineWidgets.QWebEngineView()
layout.addWidget(browser)
window.setLayout(layout)
window.show()

# Iniciar la aplicación
root.mainloop()
