# 🛡️ TakeOver - Write-up | TryHackMe

![Plataforma](https://img.shields.io/badge/Platform-TryHackMe-red?style=for-the-badge&logo=tryhackme)
![Dificultad](https://img.shields.io/badge/Difficulty-Easy-green?style=for-the-badge)
![Categoría](https://img.shields.io/badge/Category-Enumeracion%20de%20Subdominio-blue?style=for-the-badge)

---

## 📝 1. Resumen Ejecutivo (Extracto)

**TakeOver** es un reto de dificultad **Fácil**  que simula un escenario real de reconocimiento de activos expuestos en internet. El objetivo principal es identificar subdominios ocultos o no documentados de una organización objetivo para encontrar puntos de entrada débiles o información expuesta.

### 🎯 Objetivos de aprendizaje:
La resolución de esta máquina permite consolidar conocimientos prácticos en las siguientes áreas de la seguridad ofensiva:
*   Metodología de Reconocimiento Web (Recon): Comprender la importancia del mapeo de activos y la superficie de ataque de una organización antes de realizar cualquier intento de explotación.
*   Enumeración Activa de Subdominios: Dominar el uso de herramientas de fuerza bruta (como <code>FFuF</code> o <code>Gobuster</code>) para el descubrimiento de subdominios y hosts virtuales (Vhosts) mediante la manipulación de cabeceras <i>Host</i>.
*   Análisis de Certificados SSL/TLS:  Aprender a inspeccionar certificados de seguridad en busca de campos como los <i>Subject Alternative Names (SANs)</i>, los cuales suelen revelar subdominios internos o de desarrollo que no están registrados en servidores DNS públicos.
*   Comprensión de DNS y Virtual Hosting: Asimilar cómo los servidores web (como Apache o Nginx) enrutan el tráfico basándose en el nombre de host solicitado, y cómo configurar localmente el archivo <code>/etc/hosts</code> para interactuar con ellos.
*   Subdomain Takeover (Teórico/Práctico): Familiarizarse con el concepto de secuestro de subdominios cuando estos apuntan a servicios de terceros que han sido dados de baja pero cuya zona DNS no ha sido actualizada.

---

## 📂 2. Recursos y Archivos (Loot)

Para resolver este reto, trabaje con los siguientes elementos:

**Descripción oficial en THM:** Soy el CEO y uno de los cofundadores de futurevera.thm. En Futurevera, creemos que el futuro está en el espacio. Realizamos mucha investigación espacial y escribimos blogs sobre este tema. Antes ayudábamos a estudiantes con preguntas relacionadas con el espacio, pero actualmente estamos reconstruyendo nuestro sistema de soporte.<br>
Recientemente, unos hackers de sombrero negro (black hat hackers) se pusieron en contacto con nosotros diciendo que podían tomar el control de nuestros sistemas y están exigiendo un gran rescate. Ayúdanos a descubrir qué es lo que pueden comprometer o tomar el control.

Nuestro sitio web se encuentra en:

https://futurevera.thm

Pista: No olvides agregar la MACHINE_IP al archivo /etc/hosts para que futurevera.thm resuelva correctamente. Por ejemplo: 

<code>echo "MACHINE_IP futurevera.thm" | sudo tee -a /etc/hosts</code>

---

## 🔍 3. Procedimiento y Análisis

### Paso 3.1: Análisis Estático Inicial
