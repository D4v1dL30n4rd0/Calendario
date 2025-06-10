# Calendario

import calendar

def dibujar_calendario_en_consola(mes, año):
    # Mostrar el encabezado centrado con el nombre del mes y el año
    nombre_mes = calendar.month_name[mes]
    print(f"\n{nombre_mes} {año}".center(50))
    
  Encabezado de los días
    print("+" + "-------+" * 7)
    print("| Lun  | Mar  | Mié  | Jue  | Vie  | Sáb  | Dom  |")
    print("+" + "-------+" * 7)

  Generar las semanas del mes (0 = días vacíos)
    cal = calendar.Calendar(firstweekday=0)  # Lunes como primer día
    semanas = cal.monthdayscalendar(año, mes)

  Dibujar cada semana
    for semana in semanas:
        fila = ""
        for dia in semana:
            if dia == 0:
                fila += "|       "
            else:
                fila += f"|  {dia:2}   "
        fila += "|"
        print(fila)
        print("+" + "-------+" * 7)

# Solicitar datos al usuario
try:
    mes = int(input("Ingresa el mes (1-12): "))
    año = int(input("Ingresa el año (por ejemplo, 2025): "))
    if 1 <= mes <= 12:
        dibujar_calendario_en_consola(mes, año)
    else:
        print("Mes inválido. Debe estar entre 1 y 12.")
except ValueError:
    print("Entrada inválida. Debes ingresar números.")
