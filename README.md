# Ejercicio 2: Análisis de reseñas de videojuegos con LLMs

Módulo de Prompt Engineering (Máster IA, Pontia).

Pipeline en dos pasos con dos LLMs distintos, ejecutados con la API de Groq sobre las 100 reseñas más largas de `videogames_reviews.csv`:

1. **Filtrado** (`openai/gpt-oss-20b`): descarta reseñas sin contenido informativo (spam, texto sin sentido, memes).
2. **Extracción estructurada** (`openai/gpt-oss-120b`): para cada reseña relevante extrae sentimiento, aspectos positivos y negativos, dificultad, problemas técnicos y relación calidad-precio. La salida es siempre en español.

Las decisiones de prompts, modelos, tamaño de batch y gestión de límites (8.000 tokens/min) están justificadas en el propio notebook.

## Contenido

- `Ejercicio 2.ipynb`: notebook completo y ejecutado.
- `resultado_paso2_relevantes.csv`: reseñas que pasan el filtro.
- `resultado_final.csv`: resultado final estructurado.
- `videogames_reviews.csv`: dataset de entrada.
- `analisis_videojuegos_resultados.csv`: ejemplo de resultado proporcionado en el enunciado.

## Cómo ejecutarlo

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
echo "GROQ_API=tu_clave" > .env
jupyter notebook "Ejercicio 2.ipynb"
```


La ejecución completa tarda más de una hora por el límite de tokens por minuto de la cuenta de Groq (en la ejecución entregada fueron unos 85 minutos, contando los reintentos por errores de la API).
