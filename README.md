# Python-Escritura-de-archivos
La escritura de archivos en Python consiste en abrir un archivo en modo de escritura (write), agregar contenido al archivo y, finalmente, cerrar el archivo. Python proporciona funciones integradas para realizar estas operaciones de manera simple y eficiente.

Para escribir en un archivo, tienes que abrirlo en modo “w” (de write, escritura)
como segundo parámetro:

      >>> fsal = open('salida.txt', 'w')
      >>> print(fsal)
      <_io.TextIOWrapper name='salida.txt' mode='w' encoding='cp1252'>

Cuando trabajamos con archivos en Python, es importante entender cómo funciona la escritura y qué implicaciones tiene abrir un archivo en diferentes modos. Aquí está una explicación detallada del proceso de escritura de archivos en Python.

### Abrir un Archivo en Modo de Escritura
Si abres un archivo en modo de escritura ('w'), el contenido existente del archivo se borra. Esto es útil cuando deseas reemplazar el contenido de un archivo, pero debes tener cuidado para no perder datos importantes accidentalmente. Si el archivo no existe, Python crea un nuevo archivo.

### El Método write()
El método write() del manejador de archivos se utiliza para escribir datos en el archivo. Este método toma una cadena de texto como argumento y escribe esa cadena en el archivo. Devuelve el número de caracteres escritos.

    linea1 = "Aquí está el zarzo,\n"
    num_caracteres = fsal.write(linea1)
    print(num_caracteres)  # Imprime: 24


### Seguimiento de la Posición en el Archivo
El manejador de archivos mantiene un seguimiento de la posición actual en el archivo. Cada vez que se llama a write(), el texto se agrega en la posición actual y la posición se actualiza automáticamente. Si se llama a write() nuevamente, el nuevo texto se agrega al final del texto existente.

      linea2 = "que sube al cielo,\n"
      fsal.write(linea2)

### Manejo de Finales de Línea
Cuando escribes en un archivo, debes asegurarte de gestionar los finales de línea. El método write() no agrega un carácter de salto de línea (\n) automáticamente, a diferencia de la función print() que sí lo hace. Por lo tanto, debes agregar manualmente el carácter de salto de línea si deseas que el texto se escriba en líneas separadas.

    linea1 = "Aquí está el zarzo,\n"
    fsal.write(linea1)  # Escribe 'Aquí está el zarzo,\n'
    
    linea2 = "que sube al cielo,\n"
    fsal.write(linea2)  # Escribe 'que sube al cielo,\n'

### Cierre de Archivos en Python
Cuando trabajas con archivos en Python, es esencial cerrar los archivos después de terminar de escribir en ellos. Cerrar un archivo asegura que todos los datos se escriban físicamente en el disco y evita la pérdida de datos en caso de una interrupción inesperada, como un corte de energía.

#### Importancia de Cerrar Archivos

Cerrar un archivo es importante porque:
Asegura la Escritura Completa: Cuando escribes datos en un archivo, los datos pueden almacenarse en un búfer temporal. Cerrar el archivo asegura que todos los datos del búfer se escriban en el disco.
Libera Recursos del Sistema: Mantener un archivo abierto consume recursos del sistema. Cerrar el archivo libera estos recursos.
Evita Pérdida de Datos: En caso de un corte de energía o un fallo del programa, cerrar el archivo asegura que los datos se escriban correctamente y no se pierdan.
Método close()
El método close() se utiliza para cerrar un archivo. Aquí hay un ejemplo simple:


      fsal = open('archivo_ejemplo.txt', 'w')  # Abrir el archivo en modo de escritura
      fsal.write("Aquí está el zarzo,\n")      # Escribir datos en el archivo
      fsal.write("que sube al cielo,\n")
      fsal.close()                            # Cerrar el archivo

