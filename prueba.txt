import csv

estudiantes = []

def nota_presentacion(n1,n2,n3,n4):
    return n1*0.3, n2*0.3, n3*0.3, n4*0.1

def nota_final(nE):
    return nota_presentacion * 0.6 + nE * 0.4

def validacion_rut():
    print("Por hacer")


def agr_estudiante(): 
    nombre = str(input("Ingresar nombre del estudiante: "))
    rut = int(input("Ingresar rut de estudiante: "))
    dv = int(input("Ingrese el digito verificador de su rut: "))
    n1 = float(input("Ingrese nota 1: "))
    n2 = float(input("Ingrese nota 2: "))
    n3 = float(input("Ingrese nota 3: "))
    n4 = float(input("Ingrese nota 4: "))
    nE = float(input("Ingrese nota examen: "))

    rut = str
    dv = str

    rutCOMPLETO = rut + "-" + dv

    estudiante ={
        'nombre' : nombre,
        'rut' : rut,
        'dv' : dv,
        'n1' : n1,
        'n2' : n2,
        'n3' : n3,
        'n4' : n4,
        'nE' : nE,
        'nP' : nP,
        'nF' : nF
    }



    estudiantes.append(estudiante)

    
def mstr_estudiantes():
    if not estudiante in estudiantes:
        print("No hay estudiantes registrados. ")
    else:
        for estudiante in estudiantes:
            print(f"n/{estudiante['nombre']},n/ {estudiante['rut']}-{estudiante['dv']},n/ Nota 1:{estudiante['n1']},n/ Nota 2:{estudiante['n2']},n/ Nota 3:{estudiante['n3']},n/ Nota 4:{estudiante['n4']},n/ Nota final:{estudiante['nP']}")


def bscr_estudiante():
    if not estudiantes:
        print("No hay estudiantes para buscar.")
        encontrado = False
    else:
        buscar = input("Digite el rut del estudiante que desea buscar(xxxxxxxx-x): ")
        for estudiante in estudiantes:
            if estudiante[1] == buscar:
                print("Estudiante identificado.")
                print(f"Nombre: {estudiante[0]}, Rut: {estudiante[1]}, Nota 1:{estudiante[2]}, Nota 2:{estudiante[3]}, Nota 3:{estudiante[4]}, Nota 4:{estudiante[5]}")


def imptr_csv():
    with open("Nuevo_archivo.csv","w", newline="") as archivo_csv:
        escritor_csv = csv.writer(archivo_csv)
        escritor_csv.writerow(["Nombre", "rut", "Nota 1", "Nota 2", "Nota 3", "Nota 4", "Nota presentacion","Nota examen", "Nota final"])
        for estudiante in estudiantes:
            escritor_csv.writerow(['nombre', 'rut', 'n1', 'n2', 'n3', 'n4', 'nP'])


def menu_principal():
    while True:
        print("     ----Menu principal----     ")
        print("")
        print("1)Registrar estudiante. ")
        print("2)Mostrar todos los estudiantes. ")
        print("3)Buscar estudiante por rut. ")
        print("4)Transformar a plantilla CSV. ")
        print("5)Cerrar programa. ")

        opcion = input("Ingrese una opcion: ")

        if opcion == '1':
            agr_estudiante()
        elif opcion == '2':
            mstr_estudiantes()
        elif opcion == '3':
            bscr_estudiante()
        elif opcion == '4':
            imptr_csv()
            
menu_principal()