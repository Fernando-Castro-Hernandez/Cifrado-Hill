# Tecnológico de Software
## Jesus Fernando Castro Hernandez
## Grupo: 1-A 
## Materia: Fundamentos de Álgebra
## Actividad 21

# 🔐 Encriptador Hill (Hill Cipher)

Este proyecto es una implementación web interactiva del **Cifrado Hill**, un algoritmo de criptografía de sustitución poligráfica basado en álgebra lineal. Desarrollado con **HTML5, CSS3 y JavaScript (ES6)**.


## 📋 Descripción del Proyecto

La aplicación permite a los usuarios cifrar y descifrar mensajes utilizando una matriz clave de 2x2. A diferencia de los cifrados simples de sustitución, el Cifrado Hill opera sobre grupos de letras, lo que lo hace más resistente al análisis de frecuencia básico.

El objetivo de este desarrollo fue crear una herramienta visual que no solo realice el cálculo, sino que muestre la representación matricial del mensaje en tiempo real.

## 🚀 Instrucciones de Uso

Para probar este proyecto localmente:

1.  **Clonar el repositorio:**
    ```bash
    git clone https://github.com/Fernando-Castro-Hernandez/Cifrado-Hill.git    
    ```
2.  **Ejecutar:**
    * Navega a la carpeta del proyecto.
    * Abre el archivo `index.html` en tu navegador web preferido (Chrome, Firefox, Edge).
    * No se requiere instalación de dependencias ni servidores backend (Node.js, Python, etc.), ya que toda la lógica se ejecuta en el lado del cliente (Vanilla JS).

3.  **Pasos para operar:**
    * **Escribir Mensaje:** Ingresa el texto a cifrar (se convierte automáticamente a mayúsculas).
    * **Definir Clave:** Introduce los 4 valores numéricos para la matriz clave $2 \times 2$.
    * **Acción:** Presiona "Encriptar" para obtener el texto cifrado o "Desencriptar" para revertir el proceso.

## 🧮 Fundamentos Matemáticos

El núcleo del algoritmo se basa en la aritmética modular y operaciones matriciales sobre el alfabeto inglés (A=0, B=1, ..., Z=25), operando en módulo 26.

### 1. El Alfabeto y Mapeo
Se utiliza el alfabeto inglés estándar de 26 caracteres.


### 2. Encriptación
El mensaje se divide en vectores de tamaño 2 ($P$). La encriptación se realiza multiplicando la matriz clave ($K$) por el vector del mensaje:

$$ C = K \cdot P \pmod{26} $$

Donde:
* $C$ es el vector del texto cifrado.
* $K$ es la matriz clave $2 \times 2$.
* $P$ es el vector del texto plano.

### 3. Desencriptación (Álgebra Lineal Modular)
Para recuperar el mensaje original, se debe multiplicar el texto cifrado por la **matriz inversa** de la clave ($K^{-1}$) en módulo 26.

$$ P = K^{-1} \cdot C \pmod{26} $$

**Cálculo de la Inversa Modular:**
El desafío técnico implementado en JavaScript fue calcular $K^{-1}$ correctamente para números enteros modulares:
1.  Se calcula el determinante: $det = (ad - bc)$.
2.  Se verifica que $det \neq 0$ y que sea coprimo con 26 (existe inverso modular).
3.  Se encuentra el inverso multiplicativo del determinante ($det^{-1}$) tal que $(det \cdot det^{-1}) \equiv 1 \pmod{26}$.
4.  Se aplica la matriz adjunta multiplicada por $det^{-1}$.

## 🛠️ Personalización y Características Técnicas

Este proyecto incluye varias mejoras y manejos de errores personalizados:

* **Manejo de Módulo Negativo:** JavaScript calcula el residuo (`%`) de forma distinta a la definición matemática de módulo para números negativos. Se implementó una función `mod(n, m)` personalizada para corregir esto durante el cálculo de la matriz inversa.
* **Padding Automático:** Si el mensaje tiene un número impar de caracteres, el algoritmo agrega automáticamente una 'X' (23) al final para completar el último par de la matriz.
* **Visualización de Matrices:** El sistema muestra en tiempo real cómo el texto ingresado se transforma en vectores numéricos antes de ser procesado.
* **Validación Robusta:** El sistema detecta automáticamente si la matriz ingresada no es invertible (determinante 0 o sin inverso modular) y alerta al usuario para evitar errores de cálculo.

---
*Desarrollado por **Fer** - Estudiante de Desarrollo de Software*
