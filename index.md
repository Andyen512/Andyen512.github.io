---
layout: homepage
---

<!-- <!-- ## About Me -->

I am a second year Ph.D. student at Beijing Normal University.

## Research Interests

- **Computer Vision:** 3D Vision, Human Pose Estimation, Biometrics, Video generation
<!-- - **Human Computer iteraction:** 3D Human Modelling -->
<!-- - **Machine Learning:** meta-learning, incremental learning, transfer learning -->

## News

- **[Feb. 2025]** Our paper about biometrics is accepted to AAAI 2025.
- **[Oct. 2024]** Our paper about biometrics is accepted to ACM MM 2024.
- **[Feb. 2024]** Our paper about 3D Human Pose Estimation is accepted to AAAI 2024.
- **[Sep. 2023]** Our paper about biometrics is accepted to TMM.

{% include_relative _includes/publications.md %}

{% include_relative _includes/services.md %}

## Visitor Map

<div class="visitor-map-wrapper">
  <div id="visitor-map"></div>
  <p id="visitor-map-info">Detecting your approximate location…</p>
</div>

<script>
document.addEventListener('DOMContentLoaded', function () {
  var mapEl = document.getElementById('visitor-map');
  if (!mapEl || typeof L === 'undefined') {
    return;
  }

  var initialCoords = [20, 0];
  var map = L.map('visitor-map', { zoomControl: false }).setView(initialCoords, 2);
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(map);

  var infoEl = document.getElementById('visitor-map-info');
  var updateInfo = function (text) {
    if (infoEl) {
      infoEl.textContent = text;
    }
  };

  var highlightLocation = function (lat, lon, details) {
    map.setView([lat, lon], 5);
    L.marker([lat, lon]).addTo(map).bindPopup(details).openPopup();
    updateInfo(details);
  };

  fetch('https://ipapi.co/json/')
    .then(function (response) { return response.json(); })
    .then(function (data) {
      if (!data || !data.latitude || !data.longitude) {
        throw new Error('No coordinates returned');
      }
      var city = data.city ? data.city + ', ' : '';
      var region = data.region ? data.region + ', ' : '';
      var country = data.country_name || data.country || 'your region';
      var details = 'You appear to be visiting from ' + city + region + country + '.';
      highlightLocation(data.latitude, data.longitude, details);
    })
    .catch(function () {
      updateInfo('Unable to determine your IP location. Showing a global map instead.');
      map.setView(initialCoords, 2);
    });
});
</script>
