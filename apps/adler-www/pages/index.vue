<template>
  <div class="w-full min-h-screen bg-gray-200">
    <article class="prose mx-auto py-20">
      <p><img src="/img/adler-logo-AI.jpeg" alt="Adler OS Logo" class="w-40 h-40 border border-gray-100 shadow" /></p>
      <h1>Adler OS</h1>
      <p>
        <strong>Vision:</strong> Adler OS strebt nach einer digitalen Verwaltung in Deutschland, die effizient,
        transparent und bürgernah ist. Unser Ziel ist es, den Bürgern und Kommunen eine Open-Source-Plattform
        bereitzustellen, die modernste Technologien mit höchsten Standards in Datenschutz und Sicherheit vereint, und
        eine zukunftsfähige, digitale Verwaltung schafft. Wir glauben an eine Verwaltung von morgen, die den digitalen
        Alltag für alle Menschen in Deutschland vereinfacht und aktiv die Barrieren des analogen Systems abbaut.
      </p>

      <p>
        <strong>Mission:</strong> Adler OS ist eine Non-Profit-Initiative, die eine Open-Source-Softwareplattform
        entwickelt, speziell für die Bedürfnisse deutscher Kommunen und Bürger. Mit Adler OS stellen wir den Kommunen
        eine flexible und kosteneffiziente Lösung zur Verfügung, die ihnen vollständige Kontrolle über ihre
        Verwaltungsdaten und IT-Prozesse ermöglicht, ohne an proprietäre Anbieter gebunden zu sein. Unser Ansatz setzt
        auf offene Standards, um Interoperabilität und die Sicherheit zu gewährleisten, und ermuntert zur
        gemeinschaftlichen Weiterentwicklung – sowohl durch Kommunen als auch durch die Zivilgesellschaft.
      </p>

      <h2>Ziele und Grundprinzipien:</h2>

      <ul>
        <li>
          <strong>Bürgerzentriert:</strong> Unsere Softwareentwicklung beginnt und endet beim Nutzer. Wir konzentrieren
          uns auf intuitive und einfache Anwendungen, die den Alltag der Bürger verbessern und Verwaltungsvorgänge
          optimieren.
        </li>

        <li>
          <strong>Transparenz und Vertrauen:</strong> Als Open-Source-Plattform sind unsere Codes öffentlich zugänglich
          und jederzeit nachvollziehbar. Dies fördert Vertrauen, minimiert Sicherheitsrisiken und erlaubt
          kontinuierliche Anpassungen durch eine breite Entwicklergemeinschaft.
        </li>

        <li>
          <strong>Nachhaltigkeit und Effizienz:</strong> Die Open-Source-Lösung von Adler OS ermöglicht Kommunen eine
          kostengünstige, langfristig nutzbare digitale Infrastruktur, die unabhängig von externen, oft teuren
          Lizenzmodellen ist.
        </li>

        <li>
          <strong>Gemeinschaftliche Weiterentwicklung:</strong> Die Plattform wird gemeinsam von Kommunen, Unternehmen
          und der Open-Source-Community weiterentwickelt und profitiert von deren Wissen und Erfahrung. Jedes digitale
          Werkzeug und jede Verbesserung, die eine Kommune beiträgt, kommt der gesamten Gemeinschaft zugute.
        </li>

        <li>
          <strong>Datensouveränität und Sicherheit:</strong> Mit Adler OS behalten deutsche Kommunen und Bürger die
          Hoheit über ihre Daten. Die Plattform entspricht höchsten Sicherheitsstandards und erfüllt alle Anforderungen
          an den Datenschutz in Deutschland und Europa.
        </li>
      </ul>
      <p>
        <strong>Warum Open Source?</strong> Die Herausforderungen der digitalen Transformation erfordern offene und
        flexible Systeme mit einheitlichen Standards. Die Zukunftsfähigkeit der Verwaltung muss unabhängig von einzelnen
        Anbietern sein. Open Source bedeutet für Adler OS, dass Innovationen für alle zugänglich und von vielen
        talentierten Entwicklern gemeinsam gestaltet werden können. Ein Fundament, auf dem *jeder* aufbauen kann.
      </p>
      <p>
        <strong>Aufruf zur Mitgestaltung:</strong> Adler OS lädt Entwickler, Kommunen, Unternehmen und Bürger ein, Teil
        des Adlernests zu werden um Deutschland endlich wieder modern und effizient zu machen. Gemeinsam wollen wir die
        digitale Transformation in Deutschland gestalten und eine Verwaltung aufbauen, die im 21. Jahrhundert ankommt.
        Helfen Sie mit, eine sichere, zukunftsfähige und nachhaltige digitale Verwaltungsplattform für Deutschland zu
        schaffen!
      </p>
      <p>
        <github-button
          href="https://github.com/adler-os/adler-os"
          data-color-scheme="no-preference: light; light: light; dark: dark;"
          data-size="large"
          data-show-count="true"
          aria-label="Star adler-os/adler-os on GitHub"
          >Star</github-button
        >
      </p>
    </article>
  </div>
</template>

<script>
import GithubButton from "vue-github-button";

export default {
  components: {
    GithubButton,
  },
};
</script>
