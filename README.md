# Comparaci-n-de-Programaci-n-Tradicional-y-POO-en-Python
Programación Tradicional
En este enfoque se utilizan funciones para organizar el código. La lógica se divide en tres partes principales:
1.	Entrada de datos: se piden las temperaturas de los 7 días.
2.	Cálculo del promedio: se suma todo y se divide por la cantidad de días.
3.	Ejecución principal: se coordina el flujo del programa.
   
def ingresar_temperaturas():
    temperaturas = []
    print("Ingrese las temperaturas de la semana (7 días):")
    for i in range(7):
        temp = float(input(f"Día {i+1}: "))
        temperaturas.append(temp)
    return temperaturas

def calcular_promedio(temperaturas):
    return sum(temperaturas) / len(temperaturas)

def main():
    temperaturas = ingresar_temperaturas()
    promedio = calcular_promedio(temperaturas)
    print(f"\nEl promedio semanal de temperatura es: {promedio:.2f} °C")

if __name__ == "__main__":
    main()
    
Ventajas: simple, directo y fácil de entender. 
 Limitaciones: el código puede volverse difícil de mantener si el programa crece

 Programación Orientada a Objetos (POO)
Aquí se utiliza el paradigma de clases y objetos. Se aplican conceptos como encapsulamiento y herencia:
•	Cada día se representa como un objeto (ClimaDiario).
•	La semana se maneja como una colección de días (ClimaSemanal).
•	Se crea una clase hija (ClimaSemanalDetallado) que hereda y agrega funcionalidad

class ClimaDiario:
    def __init__(self, temperatura):
        self.__temperatura = temperatura  # Encapsulamiento

    def obtener_temperatura(self):
        return self.__temperatura

class ClimaSemanal:
    def __init__(self):
        self.dias = []

    def ingresar_temperaturas(self):
        print("Ingrese las temperaturas de la semana (7 días):")
        for i in range(7):
            temp = float(input(f"Día {i+1}: "))
            dia = ClimaDiario(temp)
            self.dias.append(dia)

    def calcular_promedio(self):
        total = sum(dia.obtener_temperatura() for dia in self.dias)
        return total / len(self.dias)

class ClimaSemanalDetallado(ClimaSemanal):
    def mostrar_detalle(self):
        print("\nTemperaturas registradas:")
        for i, dia in enumerate(self.dias, start=1):
            print(f"Día {i}: {dia.obtener_temperatura()} °C")

if __name__ == "__main__":
    clima = ClimaSemanalDetallado()
    clima.ingresar_temperaturas()
    clima.mostrar_detalle()
    promedio = clima.calcular_promedio()
    print(f"\nEl promedio semanal de temperatura es: {promedio:.2f} °C")

Ventajas: más organizado, escalable y reutilizable. 
Limitaciones: requiere mayor conocimiento y puede parecer más complejo al inicio.
Conclusión
•	La programación tradicional es útil para programas pequeños y rápidos.
•	La POO es más adecuada cuando el sistema necesita crecer, ya que permite reutilizar código y aplicar conceptos como herencia y polimorfismo.
•	Como estudiante de segundo semestre, este ejercicio me ayudó a entender mejor las diferencias entre ambos paradigmas y a practicar buenas prácticas de programación en Python.

