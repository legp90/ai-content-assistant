# ⚡ AI Assistant Lab (ai-content-assistant)

Un entorno interactivo premium y laboratorio de contenido técnico desarrollado con **React, TypeScript y Tailwind CSS**. Este espacio fue diseñado para simular un espacio de trabajo de ingeniería, permitiendo estructurar prompts y gestionar historiales de generación en una interfaz moderna y optimizada de alta fidelidad.

---

## 🚀 Características Clave

* **Diseño UI Premium:** Interfaz oscura (Zinc-950) de alta scannability construida con Tailwind CSS, optimizada para largas jornadas de desarrollo.
* **Tipado Estricto con TypeScript:** Arquitectura de datos sólida mediante interfaces para el control del historial de consultas (`HistoryItem`) y estados de la aplicación.
* **Barra Lateral de Historial:** Gestión dinámica de estados en React para almacenar, listar y recuperar consultas previas con marcas de tiempo en tiempo real.
* **Copiado Rápido con un Clic:** Botón interactivo integrado con la API del portapapeles del navegador para extraer el *output* generado de forma inmediata.
* **Resiliencia de Conexión (Arquitectura Fallback):** Sistema de contingencia inteligente que simula las respuestas del núcleo técnico si la API externa excede sus límites de cuota, garantizando un entorno 100% interactivo.

---

## 🛠️ Stack Tecnológico

* **Frontend:** React (Componentes Funcionales & Hooks de Estado)
* **Lenguaje:** TypeScript (Tipado Estricto)
* **Estilos:** Tailwind CSS (Arquitectura Utility-First & Animaciones de pulso)
* **Herramienta de Construcción:** Vite (Entorno de desarrollo ultra rápido)
* **Despliegue:** Vercel (CI/CD Automatizado ligado a la nube)

---

## 🧠 Arquitectura Destacada: El Motor de Fallback

Una de las implementaciones más maduras de este proyecto es su capacidad de resiliencia frente a fallos de servicios externos (como bloqueos de cuota regionales o límites de API Key en Google AI Studio):

```typescript
// Fragmento de la lógica de contingencia implementada
try {
  const response = await fetch(`https://generativelanguage.googleapis.com/...`);
  if (!response.ok) throw new Error('Quota Exceeded');
  // ...procesamiento de datos reales
} catch (error) {
  console.warn('Activando motor de respaldo por límite de cuota en Google.');
  const simulatedText = generateLocalResponse(prompt);
  setAiResponse(simulatedText);
  setEngineMode('Simulated Core');
}