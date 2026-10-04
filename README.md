# Natural Resources · Grade 9
Secuencia didáctica interactiva (inicio · desarrollo · cierre) para GitHub Pages + Supabase.

## Publicar (5 pasos)
1. Sube **todo el contenido de esta carpeta** a un repositorio de GitHub (en la raíz).
2. Repo → **Settings → Pages** → Source: *Deploy from a branch* → `main` / `(root)` → Save.
3. En supabase.com crea un proyecto gratis y en **SQL Editor** ejecuta `sql/1_schema.sql` y luego `sql/2_schema_v2.sql`.
4. Supabase → Authentication → Providers → Email: desactiva **Confirm email**. Copia URL y clave *anon public* (Settings → API) en `config.js` y haz commit.
5. Cada docente crea su cuenta en la página y luego, en SQL Editor:
```sql
update profiles set role='docente'
where id in (select id from auth.users where email in ('c1@...','c2@...','c3@...','c4@...'));
```
Una docente entra a **⚙️ Admin** y pulsa **Cargar contenido inicial** (solo la primera vez).

## Fotos del equipo
`docente1.jpg` … `docente4.jpg` son marcadores: reemplázalos con las fotos reales usando el mismo nombre.

## Archivos
- `index.html` página completa · `config.js` datos de Supabase · `sql/` base de datos

## Grados (v3)
Ejecuta también `sql/3_schema_v3_grados.sql`. El estudiante elige su grado al crear la cuenta; solo ve las actividades de su grado.
Los docentes cambian de grado con el selector de arriba, copian actividades entre grados y corrigen el grado de un estudiante en Admin → "Estudiantes y grados".
Los grados disponibles se editan en `index.html` (constante `GRADES`).

## Preescolar
Los grados van de Preescolar (0) a 11.º. Preescolar trae actividades de arranque con emojis, audio y quizzes cortos (Admin → grado Preescolar → "Cargar contenido inicial"). No requiere SQL nuevo.
