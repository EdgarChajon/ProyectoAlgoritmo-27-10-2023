# ProyectoAlgoritmo-27-10-2023
Sistema de Votacion 
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Main.java to edit this template
 */
package proyecto2023;

import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
import java.lang.System.Logger;
import java.util.Scanner;
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.lang.System.Logger.Level;
import java.security.SecureRandom;
import java.time.LocalDateTime;
import java.time.Month;
import java.time.format.DateTimeFormatter;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Date;
import java.util.Iterator;
import static proyecto2023.Proyecto2023.generarIDElec;

/**
 *
 * @author Romario
 */
public class Proyecto2023 {
    static LocalDateTime fechaInicioInscripcion;
   static LocalDateTime fechaFinInscripcion;
   static LocalDateTime fechaIniciovotacion;
   static LocalDateTime fechaFinvotacion;
    
    

    /**
     * @param args the command line arguments
     */
    
    // Solicitud de contraseña para ingresar al menu principal por primera vez 
    public static void main(String[] args) {

     
        
        
        String Ruta = ".\\src\\proyecto2023\\contra.txt";
        String contraseña = "";
        try {
            FileReader fileReader = new FileReader(Ruta);
            BufferedReader bufferedReader = new BufferedReader(fileReader);
            contraseña = bufferedReader.readLine();
            bufferedReader.close();
        } catch (IOException e) {
            System.out.println(e);
        }

        Scanner ContraSis = new Scanner(System.in);

        System.out.println("Sistema de Votacion");
        do {
            System.out.println("Ingrese la contraseña del sistema");

            String contraUsu = ContraSis.nextLine();

            if (contraUsu.equals(contraseña)) {
                System.out.println("Contraseña Correcta");
                MenuPrincipal();

            } else {
                System.out.println("Vuelta ingresar la contraseña");
            }
        } while (true);
    }
// Menu principal inicio 
    public static void MenuPrincipal() {

        System.out.println("Seleccione una opcion");
        System.out.println("Menu principal del sistema");
        System.out.println("1. Agregar usuario del sistema");
        System.out.println("2. Administrador de votaciones");
        System.out.println("3. Registro de votantes");
        System.out.println("4. Auditor");
     
        Scanner opcionScanner = new Scanner(System.in);
        int posicion = opcionScanner.nextInt();

        switch (posicion) {
            case 1:
                ContraAgreUsuSis(); // para ingresar al menu agregar Usuario hay que poner contraseña
                break;
            case 2:
                AdministradorVotacionesContraseña();
                break;
            case 3:
                IngresomenuRegistroVo();
                break;
            case 4:
                Auditor();
                break;
        }

    }
    // para ingresar agregar usuario solicitara una contraseña 
    public static void ContraAgreUsuSis(){
        //Contraseña para ingresar al menu Agregar Usuarios del sistema
        String Ruta = ".\\src\\proyecto2023\\contraAdmin.txt";
        String contraseña = "";
        try {
            FileReader fileReader = new FileReader(Ruta);
            BufferedReader bufferedReader = new BufferedReader(fileReader);
            contraseña = bufferedReader.readLine();
            bufferedReader.close();
        } catch (IOException e) {
            System.out.println(e);
        }

        Scanner ContraSis = new Scanner(System.in);

        System.out.println("Sistema de Votacion");
        System.out.println("Agregar Usuario de Sistema");
        do {
            System.out.println("Ingrese la contraseña del sistema");

            String contraUsu = ContraSis.nextLine();

            if (contraUsu.equals(contraseña)) {
                System.out.println("Contraseña Correcta");
                AgregarUsuariodelSistema();

            } else {
                System.out.println("Vuelta ingresar la contraseña");
                
            }
        } while (true);
    
    
    }
    
    
// inicio de modificaciones para agregar Usuario al sistema 
    
    public static void AgregarUsuariodelSistema() {
        
        
        Scanner Dato = new Scanner(System.in);
        int opcion = 0;
        System.out.println("1.AGREGAR USUARIO AL SISTEMA");
        System.out.println("2.Modificar Contreña");
        System.out.println("3.Modificar Usuario");
        System.out.println("4.Regresar al menu principal");
         System.out.println("5.Reportes"); //pendiente
        opcion = Dato.nextInt();
        switch (opcion) {
            case 1:
                agregarusuario();
                break;
            case 2:
                Modificarcontrseña();
                break;
            case 3:
                ModificarUsuario();
                break;
            case 4:
                MenuPrincipal();
                break;
        }
    }
//  //agregar Usuario al sistema 
    public static void agregarusuario() {
        Scanner Dato = new Scanner(System.in);
        String nombre = "";
        String apellido = "";
        String sexo = "";
        String FechaNacimiento = "";
        int anoN = 0;
        long DPI = 0;
        String correo = "";
        String paisresidencia = "";
        String departamento = "";
        String municipio = "";
        String DireccionAc = "";
        String Contrasena = "";
        int resta = 0;
        String agregar = "";

        System.out.println("Ingrese dia y mes de nacimiento DD MM");
        FechaNacimiento = Dato.nextLine();
        System.out.println("Ingrese año de nacimiento");
        anoN = Dato.nextInt();
        Dato.nextLine();
        resta = 2023 - anoN;
        if (resta >= 18) {
            System.out.println("Continue ingresando datos");
            System.out.println("Ingrese los nombres ");
            nombre = Dato.nextLine();
            System.out.println("Ingrese apellidos");
            apellido = Dato.nextLine();
            System.out.println("Ingrese genero M o F");
            sexo = Dato.nextLine();
            System.out.println("Ingrese DPI");
            DPI = Dato.nextLong();
            Dato.nextLine();
            System.out.println("Ingrese correo electronico");
            correo = Dato.nextLine();
            System.out.println("Ingrese Pais de residencia actual");
            paisresidencia = Dato.nextLine();
            System.out.println("Ingrese Departamento");
            departamento = Dato.nextLine();
            System.out.println("Ingrese Municipio");
            municipio = Dato.nextLine();
            System.out.println("Ingrese direccion de vivienda");
            DireccionAc = Dato.nextLine();
            System.out.println("Asignar Rol ");
            System.out.println("1. Administrador de votaciones \n 2. Registrador de Votantes 3.Auditor 4. votante ");

            int opcionRol = Dato.nextInt();
            Dato.nextLine();
            String rol = "";
            switch (opcionRol) {
                case 1:
                    rol = "Administrador de Votaciones";
                    break;
                case 2:
                    rol = "Registrador de Votantes";
                    break;
                case 3:
                    rol = "Auditor";
                    break;
                case 4:
                    rol = "Votante";
                    break;
             
                default:
                    System.out.println("Opción de rol no válida.");
                    return;
            }
            System.out.println("Estado del Usuario: 1.Activo 2. inactivo");
            int opcion =Dato.nextInt();
            String estado ="";
            switch (opcion){
            case 1:
            estado= "Activo";
            break;
            case 2:
            estado= "Inactivo";
            break;
            default:
            System.out.println("Opción de no válida.");
            //return;
            }   
            
            
            String pass = generarContraseña();
            String Usuario = nombre + "|" + apellido + "|" + sexo + "|" + FechaNacimiento + "|" + String.valueOf(anoN) + "|" + String.valueOf(DPI) + "|" + correo + "|" + paisresidencia + "|" + departamento + "|" + municipio + "|" + DireccionAc + "|" + rol + "|" + pass + "|"+estado+"\n";
            String Ruta = ".\\src\\proyecto2023\\usuariosistema.txt";
            try {
                FileWriter usuariosistema = new FileWriter(Ruta, true);
                BufferedWriter bw = new BufferedWriter(usuariosistema);
                bw.write(Usuario);
                bw.close();
            } catch (IOException ex) {
                System.out.println(ex);
                //ogger.getLogger(Proyecto2023.class.getName()).log(Level.SEVERE, null, ex);
            }

        } else {
            System.out.println("Usuario menor de edad no puede emitir su voto");
        }System.out.println("Desea agregar otro Usuario: Si o No");
            Dato.nextLine();
        agregar = Dato.nextLine();

        switch (agregar.toLowerCase()) {
            case "si":
                agregarusuario();
                break;
            case "no":
                AgregarUsuariodelSistema();
                break;
        }
                  

        
    }

    // Modificar contraseña de Usuario del sistema 
    
    public static void Modificarcontrseña() {
        String Bcorreo = "";
        Scanner busqueda = new Scanner(System.in);
        String Ruta = ".\\src\\proyecto2023\\usuariosistema.txt";
        ArrayList<String> lineasArchivo = new ArrayList<>();

        try {
            FileReader fr = new FileReader(Ruta);
            BufferedReader br = new BufferedReader(fr);
            String linea;
            while ((linea = br.readLine()) != null) {
                lineasArchivo.add(linea);
            }
            br.close();

            System.out.println("Ingrese correo del usuario a modificar");
            Bcorreo = busqueda.nextLine();

            boolean usuarioEncontrado = false;
            for (int i = 0; i < lineasArchivo.size(); i++) {
                String[] partes = lineasArchivo.get(i).split("\\|");
                if (partes[6].equals(Bcorreo)) {
                    System.out.println("Correo localizado. Ingrese la nueva contraseña: ");
                    String nuevaContra = busqueda.nextLine();
                    partes[12] = nuevaContra;
                    lineasArchivo.set(i, String.join("|", partes));
                    System.out.println("Contraseña modificada");
                    usuarioEncontrado = true;
                    
                }
               
            }

            if (!usuarioEncontrado) {
                System.out.println("Usuario con correo " + Bcorreo + " no encontrado.");
              
            }

            FileWriter fw = new FileWriter(Ruta);
            BufferedWriter bw = new BufferedWriter(fw);
            for (String lineaArchivo : lineasArchivo) {
                if (lineaArchivo != null) {
                    bw.write(lineaArchivo);
                    bw.newLine();
                }
                 
            }
            bw.close();
            fw.close();

        } catch (IOException ex) {
            System.out.println("Error: " + ex.getMessage());

        }
        
        AgregarUsuariodelSistema();
    }

    // Modificar Usuario del sistema 
    
    public static void ModificarUsuario() {
        // pendiente      
        System.out.println("Modificar Usuario");
        String Bcorreo = "";
        Scanner busqueda = new Scanner(System.in);
        String Ruta = ".\\src\\proyecto2023\\usuariosistema.txt";
        ArrayList<String> lineasArchivo = new ArrayList<>();

        try {
            FileReader fr = new FileReader(Ruta);
            BufferedReader br = new BufferedReader(fr);
            String linea;
            while ((linea = br.readLine()) != null) {
                lineasArchivo.add(linea);
            }
            br.close();

            System.out.println("Ingrese correo del usuario a modificar");
            Bcorreo = busqueda.nextLine();

            boolean usuarioEncontrado = false;

            for (int i = 0; i < lineasArchivo.size(); i++) {
                String[] partes = lineasArchivo.get(i).split("\\|");
                if (partes[6].equals(Bcorreo)) {
                    System.out.println("Correo localizado");
                    System.out.println("Ingrese los datos a modificar");
                    
                    System.out.println("Ingrese Nombre");
                    partes[0]=busqueda.nextLine();
                    System.out.println("Ingrese apellido ");
                    partes [1] =busqueda.nextLine();
                    System.out.println("Ingrese correo");
                    partes[6] = busqueda.nextLine();
                    System.out.println("ingrese Rol");
                    System.out.println("1.Administrador de votaciones,2.Registrador de Votantes");
                    System.out.println("3. Auditor y 4. Votante");
                    int opcionRol = busqueda.nextInt();
                    String rol = "";
                    switch(opcionRol){
                    case 1:
                            rol = "Administrador de Votaciones";
                            break;
                        case 2:
                            rol = "Registrador de Votantes";
                            break;
                        case 3:
                            rol = "Auditor";
                            break;
                        case 4:
                            rol = "Votante";
                            break;
                     
                        default:
                            System.out.println("Opción de rol no válida.");
                            return;
                    }
                    partes[11] = rol;
                    System.out.println("Ingresa el estado del Usuario");
                    System.out.println("1.Activo, 2. Inactivo");
                    int opcion =busqueda.nextInt();
                    String estado ="";
                    switch (opcion){
                    case 1:
                    estado= "Activo";
                    break;
                    case 2:
                    estado= "Inactivo";
                    break;
                    default:
                    System.out.println("Opción de rol no válida.");
                    return;
                    }
                    partes[13]=estado;
                    
                    lineasArchivo.set(i, String.join("|", partes));
                    System.out.println("Información modificada");
                
                    usuarioEncontrado = true;
                    break;
                }
            }

            if (!usuarioEncontrado) {
                System.out.println("Correo no encontrado");
            }
        } catch (IOException ex) {
            System.out.println("Error: " + ex.getMessage());
        }
        try (FileWriter fw = new FileWriter(Ruta);
             BufferedWriter bw = new BufferedWriter(fw)) {
            for (String linea : lineasArchivo) {
                bw.write(linea);
                bw.newLine();
        }
        }catch (IOException ex) {
            System.out.println("Error al guardar la información en el archivo: " + ex.getMessage());
        
       
        }
        AgregarUsuariodelSistema();
    }
    
    //Fin de agregar Usuario al Sistema-----------------------------------------
    
    //Inicio Administrador de Votaciones----------------------------------------
    //Para ingresar nos va solicitar correo y contraseña 
    
    public static void AdministradorVotacionesContraseña(){
        
        Scanner busqueda = new Scanner(System.in);
    System.out.println("Ingrese correo para ingresar ");
    String Bcorreo = busqueda.nextLine();

    String Ruta = ".\\src\\proyecto2023\\usuariosistema.txt";
    ArrayList<String> lineasArchivo = new ArrayList<>();

    try (BufferedReader br = new BufferedReader(new FileReader(Ruta))) {
        String linea;
        while ((linea = br.readLine()) != null) {
            lineasArchivo.add(linea);
        }
    } catch (IOException ex) {
        System.out.println("Error al leer el archivo: " + ex.getMessage());
        return;
    }

    boolean usuarioEncontrado = false;
    for (int i = 0; i < lineasArchivo.size(); i++) {
        String[] partes = lineasArchivo.get(i).split("\\|");
        if (partes[6].equals(Bcorreo)) {
            System.out.println("Correo localizado, Ingrese contraseña");
            String Contra = busqueda.nextLine();
            if (partes[12].equals(Contra) && partes[13].equals("Activo") && partes[11].equals("Administrador de Votaciones")) {
                usuarioEncontrado = true;
               AdministradorVotacion();
                break; 
            }
        }
    }

    if (!usuarioEncontrado) {
        System.out.println("No se pudo acceder al menú de Registro de votantes.");
        System.out.println("Contacte a Soporte Tecnico");
        
    }

    try (BufferedWriter bw = new BufferedWriter(new FileWriter(Ruta))) {
        for (String lineaArchivo : lineasArchivo) {
            if (lineaArchivo != null) {
                bw.write(lineaArchivo);
                bw.newLine();
            }
        }
    } catch (IOException ex) {
        System.out.println("Error al escribir en el archivo: " + ex.getMessage());
    }
          
     MenuPrincipal();   
        
    }

    
    
    
    
    
    
    
    
    
    
    public static void AdministradorVotacion() {
        int gestion = 0;
        Scanner opcion = new Scanner(System.in);

        System.out.println("Administracion de votaciones");
        System.out.println("Selecciona la Gestion");
        System.out.println("1.Gestion elecciones");
        System.out.println("2.Gestion Candidatos");
        
        System.out.println("3.Volver al menu principal");
        
        System.out.println("Ingrese el numero de Gestion");
        gestion = opcion.nextInt();
        switch (gestion) {
            case 1:
                GestionElecciones ();
                break;
            case 2:
                GestionCandidatos();
                break;
            case 3:
                MenuPrincipal();
                break;
            
                default:
                System.out.println("Opción no válida.");
                return;
        }
    }
    
     public static void GestionElecciones (){
        int gestion = 0;
         Scanner opcion = new Scanner(System.in);
         
   
         System.out.println("1.Crear eleccion");
         System.out.println("2.Establecer tiempo de elecciones");
         
         System.out.println("3.Eliminar Elecciones");
         System.out.println("4. Regresar al menu anterior");
         gestion = opcion.nextInt();
        switch (gestion) {
            case 1: CrearEleccion();
            break;
            case 2: tiemporegistroVotantes();
            break;
            case 3: EliminarEleccion();
            break;
            case 4: AdministradorVotacion();
            break;
            
            default:
                System.out.println("Opcion no valida");
           
        }
        
        
     }
     
     public static void CrearEleccion(){
               Scanner Dato = new Scanner(System.in);
               String Tituloeleccion ="";
               String Proposito ="";
               String Descripcion="";
               System.out.println("Ingrese el titulo de la Eleccion");
               Tituloeleccion = Dato.nextLine();
               System.out.println("Ingrese Proposito");
               Proposito = Dato.nextLine();
               System.out.println("Ingrese Descripcion");
               Descripcion = Dato.nextLine();
               String IDElecciones = generarIDElec();
            String Usuario = Tituloeleccion+ "|" + Proposito+ "|" + Descripcion + "|" + IDElecciones + "|" + "DatoPendiente" + "|"+"DatoPendiente"+"\n";
            String Ruta = ".\\src\\proyecto2023\\Elecciones.txt";
            try {
                FileWriter usuariosistema = new FileWriter(Ruta, true);
                BufferedWriter bw = new BufferedWriter(usuariosistema);
                bw.write(Usuario);
                bw.close();
            } catch (IOException ex) {
                System.out.println(ex);
                //ogger.getLogger(Proyecto2023.class.getName()).log(Level.SEVERE, null, ex);
            
        }
         System.out.println("Eleccion Creada con ID"+IDElecciones);            
         GestionElecciones (); 
     }
        
     public static void tiemporegistroVotantes (){
    Proyecto2023   proyecto2023  = new Proyecto2023(); 
      LocalDateTime fechaActual = LocalDateTime.now();   
         Scanner scanner = new Scanner(System.in);
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm");
         System.out.println("Fecha y hora para Registro de vontantes");
        System.out.print("Ingresa la fecha y hora de inicio (YYYY-MM-dd HH:mm): ");
        String input = scanner.nextLine();
      
        
        try {
              fechaInicioInscripcion = LocalDateTime.parse(input, formatter);
            System.out.println("Fecha de inicio ingresada: " +  fechaInicioInscripcion);
        } catch (Exception e) {
            System.out.println("Error: La entrada de dato");
                    }
     System.out.println("Ingrese la Fecha fin y hora de registro de votantes (YYYY-MM-dd HH:mm):");
     String Fin = scanner.nextLine();
      try {
              fechaFinInscripcion= LocalDateTime.parse(Fin, formatter);
            System.out.println("Fecha fin ingresada: " +  fechaFinInscripcion);
        } catch (Exception e) {
            System.out.println("Error: La entrada de dato");

         
            
           
            
            
            
 
            
    
        
     //proyecto2023.fechaInicioInscripcion = LocalDateTime.of(2022, 10, 20, 8, 0);
        System.out.println(fechaInicioInscripcion);
        
       //proyecto2023.fechaFinInscripcion = LocalDateTime.of(2022, 11, 21, 8, 0);
        System.out.println(fechaFinInscripcion);
        
        //LocalDateTime fechaActual = LocalDateTime.now();
        System.out.println(fechaActual);
        
        
        //if (fechaActual.isAfter(proyecto2023.fechaInicioInscripcion) && fechaActual.isBefore(proyecto2023.fechaFinInscripcion)) {
            System.out.println("La fecha de hoy está entre las fechas de inicio y final.");
            
            
            
            
            
            
            
            
            
            
            
       // } else {
        //    System.out.println("La fecha de hoy no está entre las fechas de inicio y final.");
        //}
        
        
        
         
         
         
         
         
         
     
     
     
     
     
     
     
        }
        tiempovotaciones();
     }
     
     //Tiempo paa votar 
     
     public static void tiempovotaciones(){
         
    
    Proyecto2023 proyecto2023 = new Proyecto2023();
    LocalDateTime fechaActual = LocalDateTime.now();

    Scanner busqueda = new Scanner(System.in);
    System.out.println("Defina el tiempo para votaciones");
    System.out.println("Ingrese ID de Eleccion ");
    String BID = busqueda.nextLine();

    String Ruta = ".\\src\\proyecto2023\\Elecciones.txt";
    ArrayList<String> lineasArchivo = new ArrayList<>();

   try (BufferedReader br = new BufferedReader(new FileReader(Ruta))) {
    String linea;
    while ((linea = br.readLine()) != null) {
        lineasArchivo.add(linea);
    }
} catch (IOException ex) {
    System.out.println("Error al leer el archivo: " + ex.getMessage());
    return;
}

    boolean usuarioEncontrado = false;
    for (int i = 0; i < lineasArchivo.size(); i++) {
        String[] partes = lineasArchivo.get(i).split("\\|");
        if (partes[3].equals(BID)) {
            Scanner scanner = new Scanner(System.in);
            DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm");
            System.out.println("ID Localizado configure tiempo de Votacion");

            System.out.println("Fecha y hora para Inicio de Votaciones");
            System.out.print("Ingresa la fecha y hora de inicio de votaciones (YYYY-MM-dd HH:mm): ");
            partes[4] = scanner.nextLine();

            try {
                LocalDateTime fechaIniciovotacion = LocalDateTime.parse(partes[4], formatter);
                System.out.println("Fecha de inicio ingresada: " + fechaIniciovotacion);
            } catch (Exception e) {
                System.out.println("Error: La entrada de dato");
            }

            System.out.println("Ingrese la Fecha fin y hora de votaciones (YYYY-MM-dd HH:mm):");
            partes[5] = scanner.nextLine();

            try {
                LocalDateTime fechaFinvotacion = LocalDateTime.parse(partes[5], formatter);
                System.out.println("Fecha fin ingresada: " + fechaFinvotacion);
            } catch (Exception e) {
                System.out.println("Error: La entrada de dato");
            }

            lineasArchivo.set(i, String.join("|", partes));
            usuarioEncontrado = true;

            break;
        }
    }

    try (FileWriter fw = new FileWriter(Ruta);
         BufferedWriter bw = new BufferedWriter(fw)) {
        for (String linea : lineasArchivo) {
            bw.write(linea);
            bw.newLine();
        }
    } catch (IOException ex) {
        System.out.println("Error al escribir en el archivo: " + ex.getMessage());
    }


    
    
    
    
    
    
    /*try (BufferedWriter bw = new BufferedWriter(new FileWriter(Ruta))) {
        for (String lineaArchivo : lineasArchivo) {
            if (lineaArchivo != null) {
                bw.write(lineaArchivo);
                bw.newLine();*/
            
        
   // } catch (IOException ex) {
       // System.out.println("Error al escribir en el archivo: " + ex.getMessage());
    
         
         
         
         
   
     
    
    
    GestionElecciones ();
     }
      public static void EliminarEleccion(){
          
                  System.out.println("Eliminar Eleccion");
    String BID = "";
    Scanner busqueda = new Scanner(System.in);
    String Ruta = ".\\src\\proyecto2023\\Elecciones.txt";
    ArrayList<String> lineasArchivo = new ArrayList<>();

    try {
        FileReader fr = new FileReader(Ruta);
        BufferedReader br = new BufferedReader(fr);
        String linea;
        while ((linea = br.readLine()) != null) {
            lineasArchivo.add(linea);
        }
        br.close();

        System.out.println("Ingrese ID a eliminar");
        BID = busqueda.nextLine();

        boolean candidatoEncontrado = false;

        for (int i = 0; i < lineasArchivo.size(); i++) {
            String[] partes = lineasArchivo.get(i).split("\\|");
            if (partes[3].equals(BID)) {
                System.out.println("ID Localizado");
                System.out.println("¿Desea eliminar Eleccion? (Si/No)");
                String respuesta = busqueda.nextLine();
                if (respuesta.equalsIgnoreCase("Si")) {
                   
                    lineasArchivo.remove(i);
                    System.out.println("Candidato eliminado");
                }
                candidatoEncontrado = true;
                break;
            }
        }

        if (!candidatoEncontrado) {
            System.out.println("ID no encontrado");
        }
    } catch (IOException ex) {
        System.out.println("Error: " + ex.getMessage());
    }

    try (FileWriter fw = new FileWriter(Ruta);
         BufferedWriter bw = new BufferedWriter(fw)) {
        for (String linea : lineasArchivo) {
            bw.write(linea);
            bw.newLine();
        }
    } catch (IOException ex) {
        System.out.println("Error al guardar la información en el archivo: " + ex.getMessage());
    }
  
  GestionElecciones ();
      
       }  

          
          
          
          
          
          
          
          
          
         
          
      
     
     
     
 
     
     
     
     
     //Inicio de Registro, editar, eliminar Candidato--------------------------
    
     public static void GestionCandidatos(){
         int gestion = 0;
         Scanner opcion = new Scanner(System.in);
    
         System.out.println("1.Agregar Candidato");
         System.out.println("2.Modificar Candidato");
         System.out.println("3.Estado de candidato");
         System.out.println("4.Eliminar Candidato");
         System.out.println("5.Regresar al menu anterior");
         System.out.println("Ingrese el numero de Gestion");
        gestion = opcion.nextInt();
        switch (gestion) {
            case 1:
                AgregarCandidato();
                break;
            case 2:
                EditarCandidato();
                break;
            case 3:
                EstadoCantidado();
                break;
            case 4:
                 EliminarCandidato();
                break;
            case 5:
                AdministradorVotacion();
              
                default:
                System.out.println("Opción de rol no válida.");
                return;
        }  
         
     }
     
     public static void AgregarCandidato(){
         
         Scanner Dato = new Scanner(System.in);
        String nombre = "";
        String apellido = "";
        String sexo = "";
        String FechaNacimiento = "";
        int anoN = 0;
        long DPI = 0;
        String FormacionAcademica = "";
        String Experiencia = "";
        
        String ID = "";
        int resta = 0;
        String agregar = "";

        System.out.println("Ingrese dia y mes de nacimiento");
        FechaNacimiento = Dato.nextLine();
        System.out.println("Ingrese año de nacimiento");
        anoN = Dato.nextInt();
        Dato.nextLine();
        resta = 2023 - anoN;
        if (resta >= 18) {
            System.out.println("Continue ingresando datos");
            System.out.println("Ingrese los nombres ");
            nombre = Dato.nextLine();
            System.out.println("Ingrese apellidos");
            apellido = Dato.nextLine();
            System.out.println("Ingrese genero M o F");
            sexo = Dato.nextLine();
            System.out.println("Ingrese DPI");
            DPI = Dato.nextLong();
            Dato.nextLine();
            System.out.println("Ingrese Formacion");
            FormacionAcademica = Dato.nextLine();
            System.out.println("Ingrese Experiencia");
            Experiencia = Dato.nextLine();
            
    
            System.out.println("Estado del Usuario para eleccion: 1.Activo 2. inactivo");
            int opcion =Dato.nextInt();
            String estado ="";
            switch (opcion){
            case 1:
            estado= "Activo";
            break;
            case 2:
            estado= "Inactivo";
            break;
            default:
            System.out.println("Opción de no válida.");
            //return;
            }   
            
            String IDcandidato = generarID();
            String Usuario = nombre + "|" + apellido + "|" + sexo + "|" + FechaNacimiento + "|" + String.valueOf(anoN) + "|" + String.valueOf(DPI) + "|" + FormacionAcademica + "|" + Experiencia + "|" + "DatoPendiente"+ "|" + "DatoPendiente" + "|" +IDcandidato+ "|"+estado+"|"+"TituloEleccion"+"|"+"proposito"+"|"+"descripcion"+"|"+"IDeleccion"+"\n";
            String Ruta = ".\\src\\proyecto2023\\candidatos.txt";
            try {
                FileWriter usuariosistema = new FileWriter(Ruta, true);
                BufferedWriter bw = new BufferedWriter(usuariosistema);
                bw.write(Usuario);
                bw.close();
            } catch (IOException ex) {
                System.out.println(ex);
                //ogger.getLogger(Proyecto2023.class.getName()).log(Level.SEVERE, null, ex);
            }

        } else {
            System.out.println("Usuario menor de edad no puede emitir su voto");
        }System.out.println("Desea agregar otro Usuario: Si o No");
            Dato.nextLine();
        agregar = Dato.nextLine();

        switch (agregar.toLowerCase()) {
            case "si":
                AgregarCandidato();
                break;
            case "no":
                AdministradorVotacion();
                break;
        } 
         
         
     }
     public static void EditarCandidato(){
         System.out.println("Modificar Candidato");
        String BID = "";
        Scanner busqueda = new Scanner(System.in);
        String Ruta = ".\\src\\proyecto2023\\candidatos.txt";
        ArrayList<String> lineasArchivo = new ArrayList<>();

        try {
            FileReader fr = new FileReader(Ruta);
            BufferedReader br = new BufferedReader(fr);
            String linea;
            while ((linea = br.readLine()) != null) {
                lineasArchivo.add(linea);
            }
            br.close();

            System.out.println("Ingrese el ID de Candidato");
            BID = busqueda.nextLine();

            boolean usuarioEncontrado = false;

            for (int i = 0; i < lineasArchivo.size(); i++) {
                String[] partes = lineasArchivo.get(i).split("\\|");
                if (partes[10].equals(BID)) {
                    System.out.println("ID Localizado");
                    System.out.println("Ingrese los datos a modificar");
                    
                    System.out.println("Ingrese nombre");
                    partes[0]=busqueda.nextLine();
                    System.out.println("Ingrese apellido");
                    partes [1] =busqueda.nextLine();
                    System.out.println("Ingrese numero de DPI");
                    partes[5] = busqueda.nextLine();
                    System.out.println("Ingrese Formacion");
                    partes[6] = busqueda.nextLine();
                    System.out.println("Ingrese experiencia");
                    partes[7] = busqueda.nextLine();
                    System.out.println("Ingresa el estado del Candidato para eleccion");
                    System.out.println("1.Activo, 2. Inactivo");
                    int opcion =busqueda.nextInt();
                    String estado ="";
                    switch (opcion){
                    case 1:
                    estado= "Activo";
                    break;
                    case 2:
                    estado= "Inactivo";
                    break;
                    default:
                    System.out.println("Opción de rol no válida.");
                    return;
                    }
                    partes[11]=estado;
                    
                    lineasArchivo.set(i, String.join("|", partes));
                    System.out.println("Información modificada");
                
                    usuarioEncontrado = true;
                    break;
                }
            }

            if (!usuarioEncontrado) {
                System.out.println("ID no Encontrado");
                
            }
        } catch (IOException ex) {
            System.out.println("Error: " + ex.getMessage());
        }
        try (FileWriter fw = new FileWriter(Ruta);
             BufferedWriter bw = new BufferedWriter(fw)) {
            for (String linea : lineasArchivo) {
                bw.write(linea);
                bw.newLine();
        }
        }catch (IOException ex) {
            System.out.println("Error al guardar la información en el archivo: " + ex.getMessage());
        }
        GestionCandidatos();
        

            
        }
        
      
       public static void EstadoCantidado(){ 
       System.out.println("Modificar Estado");
       String BID = "";
        Scanner busqueda = new Scanner(System.in);
        String Ruta = ".\\src\\proyecto2023\\candidatos.txt";
        ArrayList<String> lineasArchivo = new ArrayList<>();

        try {
            FileReader fr = new FileReader(Ruta);
            BufferedReader br = new BufferedReader(fr);
            String linea;
            while ((linea = br.readLine()) != null) {
                lineasArchivo.add(linea);
            }
            br.close();

            System.out.println("Ingrese ID Candidato para eleccion");
            BID = busqueda.nextLine();

            boolean usuarioEncontrado = false;

            for (int i = 0; i < lineasArchivo.size(); i++) {
                String[] partes = lineasArchivo.get(i).split("\\|");
                if (partes[10].equals(BID)) {
                    System.out.println("ID Localizado");
                    System.out.println("Dado a modificar: ");
                    System.out.println("Ingresa el estado del Usuario");
                    System.out.println("1.Activo, 2. Inactivo");
                    int opcion =busqueda.nextInt();
                    String estado ="";
                    switch (opcion){
                    case 1:
                    estado= "Activo";
                    break;
                    case 2:
                    estado= "Inactivo";
                    break;
                    default:
                    System.out.println("Opción no válida.");
                    return;
                    }
                    partes[11]=estado;
                    
                    lineasArchivo.set(i, String.join("|", partes));
                    System.out.println("Información modificada");
                
                    usuarioEncontrado = true;
                    break;
        
           
                }
            }

            if (!usuarioEncontrado) {
                System.out.println("Correo no encontrado");
                GestionCandidatos();
            }
        } catch (IOException ex) {
            System.out.println("Error: " + ex.getMessage());
        }
        try (FileWriter fw = new FileWriter(Ruta);
             BufferedWriter bw = new BufferedWriter(fw)) {
            for (String linea : lineasArchivo) {
                bw.write(linea);
                bw.newLine();
        }
        }catch (IOException ex) {
            System.out.println("Error al guardar la información en el archivo: " + ex.getMessage());
        }
       GestionCandidatos();  
         
     }
       
       public static void EliminarCandidato(){
        System.out.println("Eliminar Candidato");
    String BID = "";
    Scanner busqueda = new Scanner(System.in);
    String Ruta = ".\\src\\proyecto2023\\candidatos.txt";
    ArrayList<String> lineasArchivo = new ArrayList<>();

    try {
        FileReader fr = new FileReader(Ruta);
        BufferedReader br = new BufferedReader(fr);
        String linea;
        while ((linea = br.readLine()) != null) {
            lineasArchivo.add(linea);
        }
        br.close();

        System.out.println("Ingrese ID Candidato a eliminar");
        BID = busqueda.nextLine();

        boolean candidatoEncontrado = false;

        for (int i = 0; i < lineasArchivo.size(); i++) {
            String[] partes = lineasArchivo.get(i).split("\\|");
            if (partes[10].equals(BID)) {
                System.out.println("ID Localizado");
                System.out.println("¿Desea eliminar este candidato? (Si/No)");
                String respuesta = busqueda.nextLine();
                if (respuesta.equalsIgnoreCase("Si")) {
                   
                    lineasArchivo.remove(i);
                    System.out.println("Candidato eliminado");
                }
                candidatoEncontrado = true;
                break;
            }
        }

        if (!candidatoEncontrado) {
            System.out.println("Candidato no encontrado");
        }
    } catch (IOException ex) {
        System.out.println("Error: " + ex.getMessage());
    }

    try (FileWriter fw = new FileWriter(Ruta);
         BufferedWriter bw = new BufferedWriter(fw)) {
        for (String linea : lineasArchivo) {
            bw.write(linea);
            bw.newLine();
        }
    } catch (IOException ex) {
        System.out.println("Error al guardar la información en el archivo: " + ex.getMessage());
    }
    GestionCandidatos();
 
           
       }
       
       //Fin de registro de candidatos------------------------------------------
       
    
      public static void opcionesElecciones (){
          
          
      }
    
    
    //Inicio Registrar Votante--------------------------------------------------
    // Para registrar un votante va solicitar correo y contraseña del ROl
    
     public static void IngresomenuRegistroVo(){  // solicitud de contraseña menu registro votante
       Scanner busqueda = new Scanner(System.in);
    System.out.println("Ingrese correo para ingresar ");
    String Bcorreo = busqueda.nextLine();

    String Ruta = ".\\src\\proyecto2023\\usuariosistema.txt";
    ArrayList<String> lineasArchivo = new ArrayList<>();

    try (BufferedReader br = new BufferedReader(new FileReader(Ruta))) {
        String linea;
        while ((linea = br.readLine()) != null) {
            lineasArchivo.add(linea);
        }
    } catch (IOException ex) {
        System.out.println("Error al leer el archivo: " + ex.getMessage());
        return;
    }

    boolean usuarioEncontrado = false;
    for (int i = 0; i < lineasArchivo.size(); i++) {
        String[] partes = lineasArchivo.get(i).split("\\|");
        if (partes[6].equals(Bcorreo)) {
            System.out.println("Correo localizado, Ingrese contraseña");
            String Contra = busqueda.nextLine();
            if (partes[12].equals(Contra) && partes[13].equals("Activo") && partes[11].equals("Registrador de Votantes")) {
                usuarioEncontrado = true;
               RegistroVotante();
                break; 
            }
        }
    }

    if (!usuarioEncontrado) {
        System.out.println("No se pudo acceder al menú de Registro de votantes.");
        System.out.println("Contacte a Soporte Tecnico");
        
    }

    try (BufferedWriter bw = new BufferedWriter(new FileWriter(Ruta))) {
        for (String lineaArchivo : lineasArchivo) {
            if (lineaArchivo != null) {
                bw.write(lineaArchivo);
                bw.newLine();
            }
        }
    } catch (IOException ex) {
        System.out.println("Error al escribir en el archivo: " + ex.getMessage());
    }
                      
      
      MenuPrincipal();                   
     }
    
    
    //inicio de registro y menu de votantes------------------------------------ 
        
        
     public static void RegistroVotante(){
         
         if (fechaInicioInscripcion == null || fechaFinInscripcion == null) {
        System.out.println("No está en el tiempo autorizado. Se tiene que configurar la fecha y hora para Registrar Votantes.");
        return;
    }
         
     LocalDateTime fechaActual = LocalDateTime.now();
        if (fechaActual.isAfter(fechaInicioInscripcion) && fechaActual.isBefore(fechaFinInscripcion)) {
        int gestion = 0;  
         
         Scanner opcion =new Scanner (System.in);
         
         System.out.println("1.Registrar  votante");
         System.out.println("2.Modificar un votante");
         System.out.println("3.Reinicio de contraseña");
         System.out.println("4.Estado de votante");
        System.out.println("5. volver al menu anterior");
        gestion = opcion.nextInt();
        switch (gestion){
            case 1:agregarvotante();
            break;
            case 2:modificarVotante();
            break;
            case 3:ReinicioVotante();
            break;
            case 4:EstadoVotante ();
            break;
            case 5: MenuPrincipal();
            break;
             default:
            System.out.println("Opciónno válida.");
            return;
           
        } 
           
        }else {
            System.out.println("No esta a tiempo ");
             return;    }
             
           
         
        
     
    }
        
         public static void agregarvotante(){
        Scanner Dato = new Scanner(System.in);
        String nombre = "";
        String apellido = "";
        String sexo = "";
        String FechaNacimiento = "";
        int anoN = 0;
        long DPI = 0;
        String correo = "";
        String paisresidencia = "";
        String departamento = "";
        String municipio = "";
        String DireccionAc = "";
        String Contrasena = "";
        int resta = 0;
        String agregar = "";

        System.out.println("Ingrese dia y mes de nacimiento");
        FechaNacimiento = Dato.nextLine();
        System.out.println("Ingrese año de nacimiento");
        anoN = Dato.nextInt();
        Dato.nextLine();
        resta = 2023 - anoN;
        if (resta >= 18) {
            System.out.println("Continue ingresando datos");
            System.out.println("Ingrese los nombres ");
            nombre = Dato.nextLine();
            System.out.println("Ingrese apellidos");
            apellido = Dato.nextLine();
            System.out.println("Ingrese genero M o F");
            sexo = Dato.nextLine();
            System.out.println("Ingrese DPI");
            DPI = Dato.nextLong();
            Dato.nextLine();
            System.out.println("Ingrese correo electronico");
            correo = Dato.nextLine();
            System.out.println("Ingrese Pais de residencia actual");
            paisresidencia = Dato.nextLine();
            System.out.println("Ingrese Departamento");
            departamento = Dato.nextLine();
            System.out.println("Ingrese Municipio");
            municipio = Dato.nextLine();
            System.out.println("Ingrese direccion de vivienda");
            DireccionAc = Dato.nextLine();
            
            
            String pass = generarContraseña();
            String Usuario = nombre + "|" + apellido + "|" + sexo + "|" + FechaNacimiento + "|" + String.valueOf(anoN) + "|" + String.valueOf(DPI) + "|" + correo + "|" + paisresidencia + "|" + departamento + "|" + municipio + "|" + DireccionAc + "|" +"Votante"+ "|" + pass + "|"+"Activo"+"\n";
            String Ruta = ".\\src\\proyecto2023\\votantes.txt";
            try {
                FileWriter usuariosistema = new FileWriter(Ruta, true);
                BufferedWriter bw = new BufferedWriter(usuariosistema);
                bw.write(Usuario);
                bw.close();
            } catch (IOException ex) {
                System.out.println(ex);
                //ogger.getLogger(Proyecto2023.class.getName()).log(Level.SEVERE, null, ex);
            }

        } else {
            System.out.println("Usuario menor de edad no puede emitir su voto");
        }
        System.out.println("Desea agregar otro Usuario: Si o No");
        agregar = Dato.nextLine();

        switch (agregar.toLowerCase()) {
            case "si":
                agregarvotante();
                break;
            case "no":
                RegistroVotante();
                //break; me manda a pedir la contraseña 
            
            
            
            
        }
        
       
             
         }
         public static void ReinicioVotante(){
             String Bcorreo = "";
        Scanner busqueda = new Scanner(System.in);
        String Ruta = ".\\src\\proyecto2023\\votantes.txt";
        ArrayList<String> lineasArchivo = new ArrayList<>();

        try {
            FileReader fr = new FileReader(Ruta);
            BufferedReader br = new BufferedReader(fr);
            String linea;
            while ((linea = br.readLine()) != null) {
                lineasArchivo.add(linea);
            }
            br.close();

            System.out.println("Ingrese correo del usuario a modificar");
            Bcorreo = busqueda.nextLine();

            boolean usuarioEncontrado = false;
            for (int i = 0; i < lineasArchivo.size(); i++) {
                String[] partes = lineasArchivo.get(i).split("\\|");
                if (partes[6].equals(Bcorreo)) {
                    System.out.println("Correo localizado. Ingrese la nueva contraseña: ");
                    String nuevaContra = busqueda.nextLine();
                    partes[12] = nuevaContra;
                    lineasArchivo.set(i, String.join("|", partes));
                    System.out.println("Contraseña modificada");
                    usuarioEncontrado = true;
                    
                }
            }

            if (!usuarioEncontrado) {
                System.out.println("Usuario con correo " + Bcorreo + " no encontrado.");
               
            }

            FileWriter fw = new FileWriter(Ruta);
            BufferedWriter bw = new BufferedWriter(fw);
            for (String lineaArchivo : lineasArchivo) {
                if (lineaArchivo != null) {
                    bw.write(lineaArchivo);
                    bw.newLine();
                }
            }
            bw.close();
            fw.close();

        } catch (IOException ex) {
            System.out.println("Error: " + ex.getMessage());

        }
         RegistroVotante();
    
             
         }
         
          public static void modificarVotante(){
             System.out.println("Modificar votante");
        String Bcorreo = "";
        Scanner busqueda = new Scanner(System.in);
        String Ruta = ".\\src\\proyecto2023\\votantes.txt";
        ArrayList<String> lineasArchivo = new ArrayList<>();

        try {
            FileReader fr = new FileReader(Ruta);
            BufferedReader br = new BufferedReader(fr);
            String linea;
            while ((linea = br.readLine()) != null) {
                lineasArchivo.add(linea);
            }
            br.close();

            System.out.println("Ingrese correo del usuario a modificar");
            Bcorreo = busqueda.nextLine();

            boolean usuarioEncontrado = false;

            for (int i = 0; i < lineasArchivo.size(); i++) {
                String[] partes = lineasArchivo.get(i).split("\\|");
                if (partes[6].equals(Bcorreo)) {
                    System.out.println("Correo localizado");
                    System.out.println("Ingrese los datos a modificar");
                    
                    System.out.println("Ingrese Pais");
                    partes[7]=busqueda.nextLine();
                    System.out.println("Ingrese Departamento");
                    partes [8] =busqueda.nextLine();
                    System.out.println("Ingrese municipio");
                    partes[9] = busqueda.nextLine();
                    System.out.println("Ingrese direccion de vivienda");
                    partes[10] = busqueda.nextLine();
                    System.out.println("Ingrese nuevo correo");
                    partes[6] = busqueda.nextLine();
                    System.out.println("Ingresa el estado del Usuario");
                    System.out.println("1.Activo, 2. Inactivo");
                    int opcion =busqueda.nextInt();
                    String estado ="";
                    switch (opcion){
                    case 1:
                    estado= "Activo";
                    break;
                    case 2:
                    estado= "Inactivo";
                    break;
                    default:
                    System.out.println("Opción de rol no válida.");
                    return;
                    }
                    partes[13]=estado;
                    
                    lineasArchivo.set(i, String.join("|", partes));
                    System.out.println("Información modificada");
                
                    usuarioEncontrado = true;
                    break;
                }
            }

            if (!usuarioEncontrado) {
                System.out.println("Correo no encontrado");
                
            }
        } catch (IOException ex) {
            System.out.println("Error: " + ex.getMessage());
        }
        try (FileWriter fw = new FileWriter(Ruta);
             BufferedWriter bw = new BufferedWriter(fw)) {
            for (String linea : lineasArchivo) {
                bw.write(linea);
                bw.newLine();
        }
        }catch (IOException ex) {
            System.out.println("Error al guardar la información en el archivo: " + ex.getMessage());
        }
        RegistroVotante();
              
          }
          
          public static void EstadoVotante (){
                 System.out.println("Modificar Estado");
                  String Bcorreo = "";
        Scanner busqueda = new Scanner(System.in);
        String Ruta = ".\\src\\proyecto2023\\votantes.txt";
        ArrayList<String> lineasArchivo = new ArrayList<>();

        try {
            FileReader fr = new FileReader(Ruta);
            BufferedReader br = new BufferedReader(fr);
            String linea;
            while ((linea = br.readLine()) != null) {
                lineasArchivo.add(linea);
            }
            br.close();

            System.out.println("Ingrese correo del usuario a modificar");
            Bcorreo = busqueda.nextLine();

            boolean usuarioEncontrado = false;

            for (int i = 0; i < lineasArchivo.size(); i++) {
                String[] partes = lineasArchivo.get(i).split("\\|");
                if (partes[6].equals(Bcorreo)) {
                    System.out.println("Correo localizado");
                    System.out.println("Ingrese los datos a modificar");
                    System.out.println("Ingresa el estado del Usuario");
                    System.out.println("1.Activo, 2. Inactivo");
                    int opcion =busqueda.nextInt();
                    String estado ="";
                    switch (opcion){
                    case 1:
                    estado= "Activo";
                    break;
                    case 2:
                    estado= "Inactivo";
                    break;
                    default:
                    System.out.println("Opción no válida.");
                    return;
                    }
                    partes[13]=estado;
                    
                    lineasArchivo.set(i, String.join("|", partes));
                    System.out.println("Información modificada");
                
                    usuarioEncontrado = true;
                    break;
        
           
                }
            }

            if (!usuarioEncontrado) {
                System.out.println("Correo no encontrado");
                RegistroVotante();
            }
        } catch (IOException ex) {
            System.out.println("Error: " + ex.getMessage());
        }
        try (FileWriter fw = new FileWriter(Ruta);
             BufferedWriter bw = new BufferedWriter(fw)) {
            for (String linea : lineasArchivo) {
                bw.write(linea);
                bw.newLine();
        }
        }catch (IOException ex) {
            System.out.println("Error al guardar la información en el archivo: " + ex.getMessage());
        }
        RegistroVotante();
              
          }
          
         // Fin de agregar o modificar votante ---------------------------------
        public static void contraseñaAuditor(){
            Scanner busqueda = new Scanner(System.in);
    System.out.println("Ingrese correo para ingresar ");
    String Bcorreo = busqueda.nextLine();

    String Ruta = ".\\src\\proyecto2023\\usuariosistema.txt";
    ArrayList<String> lineasArchivo = new ArrayList<>();

    try (BufferedReader br = new BufferedReader(new FileReader(Ruta))) {
        String linea;
        while ((linea = br.readLine()) != null) {
            lineasArchivo.add(linea);
        }
    } catch (IOException ex) {
        System.out.println("Error al leer el archivo: " + ex.getMessage());
        return;
    }

    boolean usuarioEncontrado = false;
    for (int i = 0; i < lineasArchivo.size(); i++) {
        String[] partes = lineasArchivo.get(i).split("\\|");
        if (partes[6].equals(Bcorreo)) {
            System.out.println("Correo localizado, Ingrese contraseña");
            String Contra = busqueda.nextLine();
            if (partes[12].equals(Contra) && partes[13].equals("Activo") && partes[11].equals("Auditor")) {
                usuarioEncontrado = true;
              Auditor() ;
                break; 
            }
        }
    }

    if (!usuarioEncontrado) {
        System.out.println("No se pudo acceder al menú de Registro de votantes.");
        System.out.println("Contacte a Soporte Tecnico");
        
    }

    try (BufferedWriter bw = new BufferedWriter(new FileWriter(Ruta))) {
        for (String lineaArchivo : lineasArchivo) {
            if (lineaArchivo != null) {
                bw.write(lineaArchivo);
                bw.newLine();
            }
        }
    } catch (IOException ex) {
        System.out.println("Error al escribir en el archivo: " + ex.getMessage());
    }
          
     MenuPrincipal();   
        
    }


        
          
          
          
          
          
      public static void Auditor(){
          System.out.println("Reportes de Votaciones"); 
          
          
          
          
          
      }
      // Generar ID Elecciones 
      private static final String CARACTERES_PERMITIDOS_ID_Elecciones="ZYWX123456789";
      public static String generarIDElec(){
          SecureRandom random = new SecureRandom();
        StringBuilder IDEleccion = new StringBuilder(16);

        for (int i = 0; i < 6; i++) {
            int index = random.nextInt(CARACTERES_PERMITIDOS_ID_Elecciones.length());
            IDEleccion.append(CARACTERES_PERMITIDOS_ID_Elecciones.charAt(index));
        }

        return IDEleccion.toString();
        
      }
      
      
      //Generar ID a los Cantidatos 
      private static final String CARACTERES_PERMITIDOS_ID="ABC123456789";
      public static String generarID(){
        SecureRandom random = new SecureRandom();
        StringBuilder IDCandidato = new StringBuilder(16);

        for (int i = 0; i < 5; i++) {
            int index = random.nextInt(CARACTERES_PERMITIDOS_ID.length());
            IDCandidato.append(CARACTERES_PERMITIDOS_ID.charAt(index));
        }

        return IDCandidato.toString();
      
          
       }
      
      
      
      
      
      

    private static final String CARACTERES_PERMITIDOS = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()-=_+";
//variable global estatica

    public static String generarContraseña() {
        SecureRandom random = new SecureRandom();
        StringBuilder contraseña = new StringBuilder(16);

        for (int i = 0; i < 16; i++) {
            int index = random.nextInt(CARACTERES_PERMITIDOS.length());
            contraseña.append(CARACTERES_PERMITIDOS.charAt(index));
        }

        return contraseña.toString();
    }

   
 
}

