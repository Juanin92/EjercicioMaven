# TaskMaster

**TaskMaster** es una aplicación Java de consola diseñada para gestionar tareas pendientes. Este proyecto fue desarrollado como parte del ejercicio final del Módulo 3 del curso de DevOps, enfocado en la automatización del ciclo de construcción con **Apache Maven** y su integración en pipelines de CI/CD.

## 📌 Descripción

TaskMaster permite a los usuarios agregar tareas desde la línea de comandos y visualizar la lista actual de tareas. El desarrollo del proyecto sirvió para aprender a:

- Automatizar procesos con Maven.
- Gestionar dependencias.
- Ejecutar pruebas automatizadas.
- Empaquetar aplicaciones listas para distribución.
- Configurar perfiles de entorno.
- Integrar Maven en flujos de trabajo de CI/CD con GitHub Actions.

## ⚙️ Comandos Usados con Maven

| Comando             | Descripción                                                  |
|---------------------|--------------------------------------------------------------|
| `mvn clean`         | Elimina archivos generados en compilaciones anteriores.      |
| `mvn compile`       | Compila el código fuente Java.                               |
| `mvn test`          | Ejecuta pruebas unitarias con JUnit.                         |
| `mvn package`       | Empaqueta la aplicación en un archivo `.jar`.                |
| `mvn install`       | Instala el artefacto en el repositorio local de Maven.       |
| `mvn exec:java`     | Ejecuta la aplicación desde Maven usando el plugin exec.     |
| `mvn exec:java -Pdev -Denv.name=Dev` | Ejecuta la aplicación con un perfil personalizado.           |
| `mvn clean compile exec:java -Pdev` | Compila y ejecuta la aplicación con un perfil personalizado. |

## 📦 Dependencias y Plugins Utilizados

### Dependencias

```xml
<dependencies>
  <dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.13</version>
    <scope>test</scope>
  </dependency>
  <dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
    <version>3.12.0</version>
  </dependency>
</dependencies>

### Plugins
<build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.8.1</version>
        <configuration>
          <source>11</source>
          <target>11</target>
        </configuration>
      </plugin>
      <plugin>
        <groupId>org.codehaus.mojo</groupId>
        <artifactId>exec-maven-plugin</artifactId>
        <version>3.1.0</version>
        <configuration>
          <mainClass>com.equipo.taskmaster.App</mainClass>
          <systemProperties>
            <systemProperty>
              <key>env.name</key>
              <!--suppress UnresolvedMavenProperty -->
              <value>${env.name}</value>
            </systemProperty>
          </systemProperties>
        </configuration>
      </plugin>
    </plugins>
  </build>