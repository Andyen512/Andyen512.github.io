<!-- <h4 style="margin:0 10px 0;">Conference Reviewers</h4>

<ul style="margin:0 0 5px;">
  <li><a href="http://cvpr2023.thecvf.com/"><autocolor>IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR) 2021-2023</autocolor></a></li>
  <li><a href="http://iccv2021.thecvf.com/"><autocolor>IEEE/CVF International Conference on Computer Vision (ICCV) 2021</autocolor></a></li>
  <li><a href="https://eccv2022.ecva.net/"><autocolor>European Conference on Computer Vision (ECCV) 2022</autocolor></a></li>
</ul>

<h4 style="margin:0 10px 0;">Journal Reviewers</h4>

<ul style="margin:0 0 20px;">
  <li><a href="https://www.computer.org/csdl/journal/tp"><autocolor>IEEE Transactions on Pattern Analysis and Machine Intelligence (TPAMI)</autocolor></a></li>
  <li><a href="https://www.springer.com/journal/11263"><autocolor>International Journal of Computer Vision (IJCV)</autocolor></a></li>
</ul> -->

<!-- ### Journal Reviewer
- [IEEE Transactions on Pattern Analysis and Machine Intelligence (TPAMI)](https://www.computer.org/csdl/journal/tp)
- [International Journal of Computer Vision (IJCV)](https://www.springer.com/journal/11263) -->

## Services
#### Conference Reviewer
- [AAAI](https://aaai.org/conference/aaai/aaai-26/), [IJCAI](https://www.ijcai.org/), [PRCV](https://www.prcv.cn/)

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
