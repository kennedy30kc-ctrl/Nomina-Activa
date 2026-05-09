<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Nómina Activa - Comunidad Financiera</title>
<style>
  /* Reset básico */
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: #f9fafb;
    color: #1b3e18;
    line-height: 1.6;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  /* Contenedor principal */
  .container {
    max-width: 1100px;
    margin: 0 auto;
    padding: 1rem 2rem 4rem 2rem;
    flex-grow: 1;
  }

  /* Header con logo grande actualizado */
  header {
    background-color: #1b3e18;
    padding: 1.5rem 2rem;
    display: flex;
    align-items: center;
    gap: 1.2rem;
    border-radius: 0 0 35px 35px;
    box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    flex-wrap: wrap;
    justify-content: center;
  }
  header img.logo {
    max-height: 100px;
    width: auto;
    flex-shrink: 0;
    user-select: none;
  }
  header h1 {
    color: white;
    font-weight: 900;
    font-size: 3rem;
    font-family: 'Montserrat', sans-serif;
    text-shadow: 2px 2px 7px rgba(0,0,0,0.35);
    user-select: none;
  }
  header p.tagline {
    flex-basis: 100%;
    text-align: center;
    font-size: 1.2rem;
    font-style: italic;
    color: #adebad;
    margin-top: 0.3rem;
  }

  /* Botones grandes con íconos */
  .button-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1.8rem;
    margin-top: 2rem;
  }
  .big-button {
    background: white;
    border-radius: 25px;
    box-shadow: 0 12px 25px rgba(27, 62, 24, 0.15);
    cursor: pointer;
    width: 220px;
    padding: 1.8rem 1rem;
    text-align: center;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    user-select: none;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.7rem;
  }
  .big-button:hover {
    transform: translateY(-6px);
    box-shadow: 0 18px 40px rgba(27, 62, 24, 0.3);
  }
  .big-button-icon {
    font-size: 5rem;
    color: #1b3e18;
  }
  .big-button-text {
    font-weight: 900;
    color: #1b3e18;
    font-size: 1.3rem;
  }

  /* Formularios y panel contenido */
  .form-panel {
    background: white;
    max-width: 700px;
    margin: 2rem auto 0;
    padding: 2rem 2.5rem 3rem;
    border-radius: 20px;
    box-shadow: 0 20px 40px rgba(27,62,24,0.12);
    display: none;
    animation: fadeInUp 0.5s ease forwards;
  }
  .form-panel.active {
    display: block;
  }
  .form-panel h2 {
    text-align: center;
    color: #1b3e18;
    margin-bottom: 1rem;
    font-weight: 900;
    font-size: 2.2rem;
  }
  .info-box {
    background: #f0f7e9;
    border-left: 5px solid #9ccf62;
    padding: 1rem 1.5rem;
    margin-bottom: 1.5rem;
    font-style: italic;
    color: #405c1e;
    border-radius: 8px;
    font-size: 1rem;
  }

  form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  label {
    font-weight: 700;
    color: #235215;
    margin-bottom: 0.3rem;
  }
  input[type="text"],
  input[type="email"],
  input[type="tel"],
  input[type="file"],
  textarea,
  select {
    padding: 0.7rem 1rem;
    border-radius: 10px;
    border: 1.5px solid #a6cda7;
    font-size: 1rem;
    outline-color: #1b3e18;
    resize: vertical;
    font-family: inherit;
    transition: border-color 0.3s ease;
  }
  input[type="text"]:focus,
  input[type="email"]:focus,
  input[type="tel"]:focus,
  select:focus,
  textarea:focus {
    border-color: #95d44a;
  }
  textarea {
    min-height: 80px;
  }
  input[type="file"] {
    padding: 0.3rem 0.6rem;
  }
  button.submit-btn {
    margin-top: 1.4rem;
    background: #adebad;
    color: #1b3e18;
    padding: 1rem 20px;
    border-radius: 30px;
    font-weight: 900;
    font-size: 1.2rem;
    border: none;
    cursor: pointer;
    box-shadow: 0 10px 25px rgba(172, 217, 106, 0.55);
    transition: all 0.3s ease;
  }
  button.submit-btn:hover {
    background: #c9f681;
    box-shadow: 0 15px 30px rgba(172, 217, 106, 0.85);
    transform: translateY(-3px);
  }

  /* Animación */
  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(15px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  /* Footer */
  footer {
    background-color: #1b3e18;
    color: #adebad;
    text-align: center;
    padding: 1.5rem 1rem;
    font-size: 0.95rem;
    font-weight: 600;
    user-select: none;
  }

  /* WhatsApp Floating Button */
  .whatsapp-float {
    position: fixed;
    bottom: 30px;
    right: 30px;
    background-color: #25D366;
    width: 60px;
    height: 60px;
    border-radius: 50%;
    box-shadow: 0 8px 15px rgba(37, 211, 102, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    z-index: 1100;
    transition: background-color 0.3s ease;
    text-decoration: none;
  }
  .whatsapp-float:hover {
    background-color: #1ebe57;
  }
  .whatsapp-icon {
    fill: white;
    width: 30px;
    height: 30px;
  }

  /* Responsive */
  @media (max-width: 800px) {
    .button-grid {
      flex-direction: column;
      align-items: center;
    }
    .big-button {
      width: 90%;
      max-width: 320px;
    }
    .form-panel {
      margin: 2rem 1rem 3rem;
      padding: 1.5rem 1.8rem 2.5rem;
      max-width: 100%;
    }
    header h1 {
      font-size: 2.4rem;
    }
  }
</style>
</head>
<body>

<header role="banner">
  <img src="https://i.imgur.com/xbdwpra.png" alt="Logo de Nómina Activa" class="logo" />
  <h1>Nómina Activa</h1>
  <p class="tagline">Una comunidad sólida de préstamos responsables y crecientes</p>
</header>

<div class="container" role="main">

  <!-- Botones grandes -->
  <div class="button-grid" aria-label="Opciones principales de la comunidad Nómina Activa">
    <button class="big-button active" data-form="prestamos" aria-pressed="true" aria-controls="form-prestamos" type="button">
      <div class="big-button-icon" aria-hidden="true">💰</div>
      <span class="big-button-text">Solicitar Préstamo</span>
    </button>
    <button class="big-button" data-form="estado" aria-pressed="false" aria-controls="form-estado" type="button">
      <div class="big-button-icon" aria-hidden="true">📊</div>
      <span class="big-button-text">Estado del Crédito</span>
    </button>
    <button class="big-button" data-form="cronogramas" aria-pressed="false" aria-controls="form-cronogramas" type="button">
      <div class="big-button-icon" aria-hidden="true">📅</div>
      <span class="big-button-text">Cronograma de Pago</span>
    </button>
    <button class="big-button" data-form="recibos" aria-pressed="false" aria-controls="form-recibos" type="button">
      <div class="big-button-icon" aria-hidden="true">🧾</div>
      <span class="big-button-text">Solicitar Recibos</span>
    </button>
    <button class="big-button" data-form="pazySalvo" aria-pressed="false" aria-controls="form-pazySalvo" type="button">
      <div class="big-button-icon" aria-hidden="true">✅</div>
      <span class="big-button-text">Solicitar Paz y Salvo</span>
    </button>
    <button class="big-button" data-form="contacto" aria-pressed="false" aria-controls="form-contacto" type="button">
      <div class="big-button-icon" aria-hidden="true">📞</div>
      <span class="big-button-text">Contacto / WhatsApp</span>
    </button>
  </div>

  <!-- Formularios mostrados segun botón -->

  <!-- Formulario Solicitar Préstamo -->
  <section id="form-prestamos" class="form-panel active" tabindex="-1" aria-live="polite" aria-label="Formulario solicitar préstamo">
    <h2>Solicitar Préstamo y Avance de Crédito</h2>
    <div class="info-box">
      Comienza con pequeños préstamos; tu buen historial te permitirá avanzar hasta créditos mayores para motos y herramientas.
    </div>
    <form id="formPrestamos" enctype="multipart/form-data" method="POST" action="https://formspree.io/f/xbdwprae" aria-describedby="info-prestamos" aria-live="polite">
      <label for="nombre-prestamos">Nombre Completo *</label>
      <input type="text" id="nombre-prestamos" name="NombreCompleto" required placeholder="Tu nombre completo" />

      <label for="profesion-prestamos">Profesión / Oficio *</label>
      <input type="text" id="profesion-prestamos" name="Profesion" required placeholder="Tu profesión o actividad" />

      <label for="empresa-prestamos">Empresa donde Trabajas</label>
      <input type="text" id="empresa-prestamos" name="Empresa" placeholder="Empresa o negocio" />

      <label for="direccion-prestamos">Dirección *</label>
      <input type="text" id="direccion-prestamos" name="Direccion" required placeholder="Tu dirección" />

      <label for="correo-prestamos">Correo Electrónico *</label>
      <input type="email" id="correo-prestamos" name="_replyto" required placeholder="ejemplo@correo.com" />

      <label for="telefono-prestamos">Teléfono / WhatsApp *</label>
      <input type="tel" id="telefono-prestamos" name="Telefono" required placeholder="+573182294763" />

      <label for="documentos-prestamos">Adjuntar documento de identificación (cédula, INE, etc.)</label>
      <input type="file" id="documentos-prestamos" name="Documentos" accept="image/*,.pdf,.doc,.docx" multiple />

      <label for="mensaje-prestamos">¿Qué necesitas financiar o solicitar? *</label>
      <textarea id="mensaje-prestamos" name="Mensaje" rows="4" placeholder="Cuéntanos más" required></textarea>

      <button class="submit-btn" type="submit">Enviar Solicitud</button>
    </form>
  </section>

  <!-- Formulario Estado Crédito -->
  <section id="form-estado" class="form-panel" tabindex="-1" aria-live="polite" aria-label="Formulario consultar estado de crédito">
    <h2>Consultar Estado del Crédito</h2>
    <form id="formEstado" method="POST" action="https://formspree.io/f/xbdwprae" aria-describedby="info-estado" aria-live="polite">
      <label for="nombre-estado">Nombre Completo *</label>
      <input type="text" id="nombre-estado" name="NombreCompleto" required placeholder="Tu nombre completo" />

      <label for="correo-estado">Correo Electrónico *</label>
      <input type="email" id="correo-estado" name="_replyto" required placeholder="ejemplo@correo.com" />

      <label for="telefono-estado">Teléfono / WhatsApp *</label>
      <input type="tel" id="telefono-estado" name="Telefono" required placeholder="+573182294763" />

      <button class="submit-btn" type="submit">Consultar Estado</button>
    </form>
  </section>

  <!-- Formulario Cronograma -->
  <section id="form-cronogramas" class="form-panel" tabindex="-1" aria-live="polite" aria-label="Formulario solicitar cronograma de pago">
    <h2>Solicitar Cronograma de Pago</h2>
    <form id="formCronogramas" method="POST" action="https://formspree.io/f/xbdwprae" aria-describedby="info-cronogramas" aria-live="polite">
      <label for="nombre-cronogramas">Nombre Completo *</label>
      <input type="text" id="nombre-cronogramas" name="NombreCompleto" required placeholder="Tu nombre completo" />

      <label for="correo-cronogramas">Correo Electrónico *</label>
      <input type="email" id="correo-cronogramas" name="_replyto" required placeholder="ejemplo@correo.com" />

      <label for="telefono-cronogramas">Teléfono / WhatsApp *</label>
      <input type="tel" id="telefono-cronogramas" name="Telefono" required placeholder="+573182294763" />

      <button class="submit-btn" type="submit">Solicitar Cronograma</button>
    </form>
  </section>

  <!-- Formulario Recibos -->
  <section id="form-recibos" class="form-panel" tabindex="-1" aria-live="polite" aria-label="Formulario solicitar recibos de pago">
    <h2>Solicitar Recibos de Pago</h2>
    <form id="formRecibos" method="POST" action="https://formspree.io/f/xbdwprae" aria-describedby="info-recibos" aria-live="polite">
      <label for="nombre-recibos">Nombre Completo *</label>
      <input type="text" id="nombre-recibos" name="NombreCompleto" required placeholder="Tu nombre completo" />

      <label for="correo-recibos">Correo Electrónico *</label>
      <input type="email" id="correo-recibos" name="_replyto" required placeholder="ejemplo@correo.com" />

      <label for="telefono-recibos">Teléfono / WhatsApp *</label>
      <input type="tel" id="telefono-recibos" name="Telefono" required placeholder="+573182294763" />

      <button class="submit-btn" type="submit">Solicitar Recibos</button>
    </form>
  </section>

  <!-- Formulario Paz y Salvo -->
  <section id="form-pazySalvo" class="form-panel" tabindex="-1" aria-live="polite" aria-label="Formulario solicitar paz y salvo">
    <h2>Solicitar Paz y Salvo</h2>
    <p>Tu solicitud será enviada a nuestro WhatsApp o correo y te contactaremos pronto.</p>
    <form id="formPazYS" method="POST" action="https://formspree.io/f/xbdwprae" aria-describedby="info-pazySalvo" aria-live="polite">
      <label for="nombre-pazys">Nombre Completo *</label>
      <input type="text" id="nombre-pazys" name="NombreCompleto" required placeholder="Tu nombre completo" />

      <label for="correo-pazys">Correo Electrónico *</label>
      <input type="email" id="correo-pazys" name="_replyto" required placeholder="ejemplo@correo.com" />

      <label for="telefono-pazys">Teléfono / WhatsApp *</label>
      <input type="tel" id="telefono-pazys" name="Telefono" required placeholder="+573182294763" />

      <button class="submit-btn" type="submit">Enviar Solicitud</button>
    </form>
  </section>

  <!-- Formulario Contacto simple -->
  <section id="form-contacto" class="form-panel" tabindex="-1" aria-live="polite" aria-label="Formulario contacto general">
    <h2>Contacto - WhatsApp y Correo</h2>
    <p>Puedes contactarnos directamente por WhatsApp o correo electrónico.</p>
    <p><strong>WhatsApp:</strong> <a href="https://wa.me/573182294763" target="_blank" rel="noopener noreferrer" style="color:#25D366;">+57 318 229 4763</a></p>
    <p><strong>Correo:</strong> <a href="mailto:nomina.activa.col@gmail.com" style="color:#1b3e18;">nomina.activa.col@gmail.com</a></p>
  </section>

</div>

<!-- Botón flotante WhatsApp -->
<a href="https://wa.me/573182294763" target="_blank" rel="noopener noreferrer" 
   class="whatsapp-float" aria-label="Chatear por WhatsApp con Nómina Activa">
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="whatsapp-icon" aria-hidden="true"><path d="M20.52 3.48a11.93 11.93 0 00-16.9 0 11.92 11.92 0 00-3.06 10.58l-1.47 5.07 5.23-1.38a11.9 11.9 0 0010.2 3.06 11.95 11.95 0 007.28-4.21 11.92 11.92 0 00-1.3-16.12zm-8.37 17.6a9.14 9.14 0 01-4.66-1.43l-.33-.21-3.09.81.83-3.01-.22-.33a9.13 9.13 0 114.47 3.17zM16.36 14c-.27-.13-1.6-.78-1.85-.87-.25-.09-.43-.13-.62.13s-.71.87-.87 1.05c-.16.18-.32.2-.6.07a7.84 7.84 0 01-2.31-1.4 8.89 8.89 0 011.68-2.32c.16-.17 0-.33-.03-.46-.04-.12-.62-1.51-.85-2.06-.22-.54-.45-.46-.62-.47-.16 0-.35 0-.54 0s-.5.07-.76.36a3.17 3.17 0 00-1 1.2 4.27 4.27 0 00.28 2.67 9.02 9.02 0 005.27 5.34c.75.32 1.34.26 1.85.16a4.47 4.47 0 001.37-.78 3.39 3.39 0 001.22-1.42c.12-.22.12-.41.08-.56-.04-.1-.26-.15-.53-.27z"/></svg>
</a>

<footer role="contentinfo">
  &copy; 2024 Nómina Activa - Comunidad Financiera. Todos los derechos reservados.
</footer>

<script>
  const buttons = document.querySelectorAll('.big-button');
  const forms = document.querySelectorAll('.form-panel');

  buttons.forEach(button => {
    button.addEventListener('click', () => {
      buttons.forEach(btn => {
        btn.classList.remove('active');
        btn.setAttribute('aria-pressed', 'false');
      });
      button.classList.add('active');
      button.setAttribute('aria-pressed', 'true');

      const formToShow = button.getAttribute('data-form');
      forms.forEach(form => {
        if(form.id === 'form-' + formToShow) {
          form.classList.add('active');
          form.focus();
        } else {
          form.classList.remove('active');
        }
      });
      const visibleForm = document.querySelector('.form-panel.active');
      visibleForm.scrollIntoView({behavior: 'smooth', block: 'start'});
    });
  });

  const allForms = document.querySelectorAll("form");
  allForms.forEach(form => {
    form.addEventListener("submit", e => {
      e.preventDefault();
      alert("¡Solicitud enviada! Nuestro equipo se pondrá en contacto contigo pronto. Gracias por confiar en Nómina Activa.");
      form.reset();
    });
  });
</script>

</body>
</html>
