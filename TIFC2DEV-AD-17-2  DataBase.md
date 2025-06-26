# 📘 Guía para Usar una Base de Datos Clave-Valor en VS Code con `quick.db`

Esta guía muestra cómo simular una base de datos tipo Replit usando Node.js y `quick.db` desde la terminal interactiva.

🔗 [Quick.DB](https://www.npmjs.com/package/quick.db)

## ✅ Requisitos

- Node.js 18 o superior
- VS Code
- Terminal integrada

## 1️⃣ Abrir el Proyecto

Descarga y abre el proyecto base [AD-17-2](./AD-17-2/) en VS Code.

## 2️⃣ Instalar Dependencias

```bash
npm install quick.db better-sqlite3
```

## 3️⃣ Crear el Archivo de Base de Datos

Crea un archivo llamado `index.js` con el siguiente contenido:

```js
import { QuickDB } from "quick.db";

const db = new QuickDB();

globalThis.db = db;
```

## 4️⃣ Iniciar una Consola Interactiva con `await`

En la terminal, ejecuta:

```bash
node --experimental-repl-await
```

Verás algo como:

```
Welcome to Node.js v20.x.x
>
```

## 5️⃣ Importar tu archivo para tener acceso a `db`

Dentro de la consola escribe:

```js
await import('./index.js')
```

## 6️⃣ Probar los Métodos de la Base de Datos

### ❌ Sin `await`:

```js
db.set("message", "Hola")
```

### ✅ Con `await`:

```js
await db.set("message", "Hola")
await db.get("message")
```

### Guardar otro valor:

```js
await db.set("name", "Kim")
await db.get("name")
```

## 7️⃣ Ver Todo el Contenido

```js
const data = await db.all()
data
```

### Acceder a claves dentro del objeto:

```js
data.find(d => d.id === "message").value
```

## 8️⃣ Borrar Claves

```js
await db.delete("name")
await db.delete("message")
```

O eliminar todo:

```js
await db.deleteAll()
```
