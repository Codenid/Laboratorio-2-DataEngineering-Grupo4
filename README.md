# Orquestación de Flujo de Datos con Gitflow, VS Code y Apache Airflow


## Objetivo
Desarrollar un DAG en Apache Airflow que suba un archivo a Azure Blob Storage, aplicando buenas prácticas de trabajo colaborativo usando Gitflow.

---

### Integrantes

- Nicole Arenas Lazo
- Edgard Inga Quillas
- Winston Flores Quispe

---

### Datos del Proyecto

| Campo | Valor |
|---|---|
| Grupo | G4 |
| Nombre del branch | `feature/dag-g4-WFQ` |
| Nombre del DAG | `g4_wfq` |
| Nombre del archivo DAG | `g4_wfq.py` |
| Blob Name | `raw/G4/archivo_subido.txt` |

---

### Descripción del Proyecto

El proyecto consistió en desarrollar un DAG personalizado en Apache Airflow que permita automatizar la subida de un archivo local hacia Azure Blob Storage/Data Lake.

Además, se aplicaron buenas prácticas de desarrollo colaborativo utilizando Gitflow, trabajando mediante ramas feature, commits, push y Pull Requests hacia la rama `develop`.

---

## Desarrollo del Proyecto

---

### 1. Actualización de la rama develop

#### Descripción

Antes de iniciar el desarrollo, se actualizó la rama `develop` para obtener la última versión del repositorio compartido.

#### Comandos ejecutados

```bash
git checkout develop
git pull origin develop
```

#### Resultado obtenido

* Se confirmó que la rama local estaba sincronizada con `origin/develop`.
* No existían cambios pendientes por descargar.

#### Evidencia

##### Pull de rama develop

![Pull rama develop](Pull%20rama%20develop.png)

---

### 2. Creación de la rama feature

#### Descripción

Se creó una rama de trabajo independiente siguiendo la nomenclatura solicitada para evitar conflictos entre integrantes.

#### Convención utilizada

```text
feature/dag-g4-WFQ
```

#### Comando ejecutado

```bash
git checkout -b feature/dag-g4-WFQ
```

#### Resultado obtenido

* Se creó correctamente la rama feature.
* El entorno quedó posicionado sobre la nueva rama de trabajo.

#### Evidencias

##### Creación de rama local

![Rama trabajo](Rama%20trabajo.png)

---

### 3. Creación del DAG personalizado

#### Descripción

Se creó un nuevo archivo DAG basado en el template proporcionado (`g0_atm.py`).

El nuevo DAG fue desarrollado dentro de la carpeta `dags/`.

#### Archivo creado

```text
dags/g4_wfq.py
```

---

#### Cambios realizados

##### Cambio de `dag_id`

```python
dag_id="g4_wfq"
```

##### Cambio de `BLOB_NAME`

```python
BLOB_NAME = "raw/G4/archivo_subido.txt"
```

#### Configuración aplicada

* Uso de `@dag` y `@task`
* Programación semanal usando cron
* Manejo básico de reintentos
* Uso de helper para agregar sufijo de fecha
* Upload automático hacia Azure Blob Storage

---

#### Evidencia

##### Creación y configuración del DAG

![Creacion DAG](creacion%20de%20dag.png)

---

### 4. Commit y Push del proyecto

#### Descripción

Después de validar el DAG, se agregaron los cambios al staging area, se creó el commit y posteriormente se realizó el push hacia GitHub.

---

#### Comandos ejecutados

##### Verificación de estado

```bash
git status
```

##### Agregado de archivo

```bash
git add dags/g4_wfq.py
```

##### Commit realizado

```bash
git commit -m "DAG del grupo 4 - WFQ"
```

##### Push hacia GitHub

```bash
git push origin feature/dag-g4-WFQ
```

---

#### Resultado obtenido

* El archivo fue agregado correctamente.
* Se registró el commit exitosamente.
* El branch fue publicado en GitHub.

---

#### Evidencia

##### Commit y Push exitoso

![Commit and Push](commit%20and%20push.png)

##### Rama publicada en GitHub

![Rama feature GitHub](rama%20features%20github.png)

---

### 5. Creación del Pull Request

#### Descripción

Luego de publicar la rama feature, se creó un Pull Request hacia la rama `develop`.

El Pull Request incluyó una descripción funcional del DAG desarrollado.

---

#### Configuración del Pull Request

| Campo         | Valor                |
| ------------- | -------------------- |
| Source Branch | `feature/dag-g4-WFQ` |
| Target Branch | `develop`            |

---

#### Resultado obtenido

* Pull Request creado exitosamente.
* Solicitud enviada para revisión/aprobación.
* Integración preparada hacia `develop`.

---

#### Evidencias

##### Creación del Pull Request

![Creacion Pull Request](Creacion%20del%20pull%20request.jpeg)

##### Pull Request enviado para aprobación

![Pull Request aprobado](Pull%20Request%20enviado%20para%20aprobaci%C3%B3n.jpeg)

---

### 6. Experimento: Ejecución del DAG en Apache Airflow + Azure

#### Descripción

Finalmente, el DAG fue ejecutado desde la interfaz de Apache Airflow para validar el funcionamiento completo del flujo.

---

##### Validaciones realizadas

| Validación                    | Resultado |
| ----------------------------- | --------- |
| DAG visible en Airflow        | Correcto  |
| DAG ejecutado                 | Correcto  |
| Task `call_upload` completada | Correcto  |
| Archivo subido a Azure        | Correcto  |
| Logs generados                | Correcto  |

---

##### Resultado observado

En los logs de Airflow se verificó:

* Conexión exitosa hacia Azure Blob Storage
* Lectura correcta del archivo local
* Upload exitoso del archivo
* Generación automática del sufijo de fecha

---

#### Evidencia

##### Ejecución exitosa del DAG en Airflow

![Ejecucion DAG](ejecuci%C3%B3n%20DAG%20sobre%20airflow%20%2B%20azure.jpeg)


##### Archivo cargado en Azure Blob Storage

![ddd](upload%20azure.png)

---


## Conclusiones


Apache Airflow permite automatizar flujos ETL de forma estructurada y reutilizable mediante DAGs y tareas desacopladas.

El uso de Gitflow facilita el trabajo colaborativo al permitir desarrollar funcionalidades de manera aislada mediante ramas feature y Pull Requests.

---
