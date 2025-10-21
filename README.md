# Django MySQL CRUD - Proyecto de Productos

Proyecto Django para aprender operaciones CRUD con MySQL utilizando el ORM de Django.

## 📋 Descripción

Este proyecto implementa un sistema básico de gestión de productos con Django y MySQL, demostrando las cuatro operaciones fundamentales: Crear, Leer, Actualizar y Eliminar (CRUD).

## 🚀 Tecnologías

- Python 3.13.5
- Django 5.x
- MySQL
- mysqlclient

## 📦 Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/moisesdatasci/mi_proyecto.git
cd mi_proyecto
```

### 2. Crear entorno virtual

```bash
python -m venv venv

# Activar entorno virtual
# Windows:
venv\Scripts\activate

# Linux/Mac:
source venv/bin/activate
```

### 3. Instalar dependencias

```bash
pip install django mysqlclient
```

### 4. Configurar base de datos

Crea una base de datos en MySQL:

```sql
CREATE DATABASE mi_base_datos CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

Edita `mi_proyecto/settings.py` con tus credenciales:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'mi_base_datos',
        'USER': 'tu_usuario',
        'PASSWORD': 'tu_contraseña',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

### 5. Aplicar migraciones

```bash
python manage.py makemigrations
python manage.py migrate
```

## 🎯 Modelo de Datos

### Producto

| Campo | Tipo | Descripción |
|-------|------|-------------|
| nombre | CharField | Nombre único del producto |
| descripcion | TextField | Descripción detallada |
| precio | DecimalField | Precio con 2 decimales |
| stock | IntegerField | Cantidad disponible |
| fecha_creacion | DateTimeField | Fecha de creación automática |

## 💻 Uso

### Abrir Django Shell

```bash
python manage.py shell
```

### Operaciones CRUD

#### Crear un producto

```python
from productos.models import Producto

producto = Producto.objects.create(
    nombre="Laptop Dell",
    descripcion="Laptop de alta gama con 16GB RAM",
    precio=850000,
    stock=15
)
print(f"Producto creado: {producto.nombre}")
```

#### Leer productos

```python
# Obtener un producto por ID
producto = Producto.objects.get(id=1)
print(f"Nombre: {producto.nombre}")
print(f"Precio: ${producto.precio}")

# Obtener todos los productos
productos = Producto.objects.all()
for p in productos:
    print(f"{p.nombre} - ${p.precio}")
```

#### Actualizar un producto

```python
producto = Producto.objects.get(id=1)
producto.precio = 1000000
producto.save()
print(f"Precio actualizado: ${producto.precio}")
```

#### Eliminar un producto

```python
producto = Producto.objects.get(id=1)
producto.delete()
print("Producto eliminado exitosamente")
```

## 🛠️ Comandos útiles

```bash
# Crear superusuario para el admin
python manage.py createsuperuser

# Ejecutar servidor de desarrollo
python manage.py runserver

# Acceder al admin
http://localhost:8000/admin
```

## 📁 Estructura del Proyecto

```
mi_proyecto/
│
├── manage.py
├── mi_proyecto/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
└── productos/
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── views.py
    ├── tests.py
    └── migrations/
```
## 👤 Autor

**Moisés**

- GitHub: [@moisesdatasci](https://github.com/moisesdatasci)

## 📚 Recursos de Aprendizaje

- [Documentación oficial de Django](https://docs.djangoproject.com/)
- [Django ORM Tutorial](https://docs.djangoproject.com/en/stable/topics/db/queries/)
- [MySQL Documentation](https://dev.mysql.com/doc/)

---

⭐️ Si este proyecto te fue útil, dale una estrella en GitHub!
