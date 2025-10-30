<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Kalkulator Gabungan: Konsumsi Bensin dan Perkiraan Waktu Tenggelam</title>
<style>
  body {
    font-family: Arial, sans-serif;
    margin: 40px;
    background: #f0f8ff;
    color: #333;
  }
  h1 {
    text-align: center;
    color: #007acc;
  }
  .section {
    margin-bottom: 50px;
    padding: 20px;
    background-color: #ffffff;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
  }
  label {
    display: block;
    margin-top: 20px;
    font-weight: bold;
  }
  select, input, button {
    width: 100%;
    max-width: 300px;
    padding: 8px;
    margin-top: 5px;
    font-size: 1rem;
  }
  button {
    background-color: #007acc;
    color: white;
    border: none;
    cursor: pointer;
    margin-top: 30px;
  }
  button:hover {
    background-color: #005f99;
  }
  .result {
    margin-top: 30px;
    padding: 15px;
    background-color: #d9f0ff;
    border-radius: 6px;
    max-width: 400px;
  }
  .hidden {
    display: none;
  }
</style>
</head>
<body>

<h1>Kalkulator Gabungan: Konsumsi Bensin dan Perkiraan Waktu Tenggelam</h1>

<!-- Bagian Kalkulator Konsumsi Bensin -->
<div class="section">
  <h2>Kalkulator Konsumsi Bensin Kendaraan</h2>
  
  <label for="jenisKendaraan">Jenis Kendaraan:</label>
  <select id="jenisKendaraan">
    <option value="">-- Pilih Jenis Kendaraan --</option>
    <option value="mobil">Mobil</option>
    <option value="motor">Motor</option>
  </select>

  <div id="mobilOptions" class="hidden">
    <label for="jenisMobil">Jenis Mobil:</label>
    <select id="jenisMobil">
      <option value="">-- Pilih Jenis Mobil --</option>
      <option value="hybrid">Hybrid</option>
      <option value="nonhybrid">Non-hybrid</option>
    </select>

    <div id="nonhybridOptions" class="hidden">
      <label for="jenisNonhybrid">Jenis Mobil Non-hybrid:</label>
      <select id="jenisNonhybrid">
        <option value="">-- Pilih Jenis --</option>
        <option value="lcgc">LCGC</option>
        <option value="mpv">MPV</option>
        <option value="suv">SUV</option>
        <option value="sedanmenengah">Sedan Menengah</option>
      </select>
    </div>
  </div>

  <div id="motorOptions" class="hidden">
    <label for="jenisMotor">Jenis Motor:</label>
    <select id="jenisMotor">
      <option value="">-- Pilih Jenis Motor --</option>
      <option value="bebek">Bebek</option>
      <option value="skutik">Skutik</option>
      <option value="sport">Sport</option>
      <option value="moge">Moge</option>
    </select>
  </div>

  <label for="jarakTempuh">Jarak Tempuh (Km):</label>
  <input type="number" id="jarakTempuh" min="0" step="0.01" placeholder="Masukkan jarak">

  <button id="hitungBensinBtn">Hitung Konsumsi Bensin</button>

  <div class="result" id="hasilBensin"></div>
</div>

<!-- Bagian Perkiraan Waktu Tenggelam -->
<div class="section">
  <h2>Perkiraan Waktu Kecamatan Tenggelam (MDPL)</h2>

  <label for="wilayah">Pilih Wilayah:</label>
  <select id="wilayah">
    <option value="">-- Pilih Wilayah --</option>
    <option value="pusat">Surabaya Pusat</option>
    <option value="timur">Surabaya Timur</option>
    <option value="barat">Surabaya Barat</option>
    <option value="selatan">Surabaya Selatan</option>
    <option value="utara">Surabaya Utara</option>
  </select>

  <label for="kecamatan">Pilih Kecamatan:</label>
  <select id="kecamatan" disabled>
    <option value="">-- Pilih Kecamatan --</option>
  </select>

  <button id="hitungTenggelamBtn" disabled>Hitung Waktu Tenggelam</button>

  <div class="result" id="hasilTenggelam"></div>
</div>

<script>
  // Data konsumsi bensin
  const konsumsiMobil = [
    {"jenis": "LCGC", "konsumsi": 0.059},
    {"jenis": "MPV", "konsumsi": 0.080},
    {"jenis": "SUV", "konsumsi": 0.118},
    {"jenis": "Sedan Menengah", "konsumsi": 0.087},
    {"jenis": "Hybrid", "konsumsi": 0.047}
  ];

  const konsumsiMotor = [
    {"jenis": "Bebek", "konsumsi": 0.019},
    {"jenis": "Skutik", "konsumsi": 0.024},
    {"jenis": "Sport", "konsumsi": 0.031},
    {"jenis": "Moge", "konsumsi": 0.054}
  ];

  // Data wilayah untuk tenggelam (MDPL)
  const dataWilayah = {
    pusat: [
      {kecamatan: 'Genteng', mdpl: 6.7},
      {kecamatan: 'Tegalsari', mdpl: 7.7},
      {kecamatan: 'Simokerto', mdpl: 3.7},
      {kecamatan: 'Bubutan', mdpl: 4.7}
    ],
    utara: [
      {kecamatan: 'Kenjeran', mdpl: 4.7},
      {kecamatan: 'Pabean Cantikan', mdpl: 3.7},
      {kecamatan: 'Semampir', mdpl: 5.7},
      {kecamatan: 'Krembangan', mdpl: 3.7}
    ],
    timur: [
      {kecamatan: 'Gubeng', mdpl: 5.7},
      {kecamatan: 'Gunung Anyar', mdpl: 2.7},
      {kecamatan: 'Sukolilo', mdpl: 3.7},
      {kecamatan: 'Tambaksari', mdpl: 5.7},
      {kecamatan: 'Mulyorejo', mdpl: 0.7},
      {kecamatan: 'Rungkut', mdpl: 4.7},
      {kecamatan: 'Tenggilis Mejoyo', mdpl: 6.7}
    ],
    barat: [
      {kecamatan: 'Benowo', mdpl: 10.7},
      {kecamatan: 'Pakal', mdpl: 5.7},
      {kecamatan: 'Asemrowo', mdpl: 4.7},
      {kecamatan: 'Sukomanunggal', mdpl: 5.7},
      {kecamatan: 'Tandes', mdpl: 8.7},
      {kecamatan: 'Sambikerep', mdpl: 17.7},
      {kecamatan: 'Lakarsantri', mdpl: 9.7},
      {kecamatan: 'Bulak', mdpl: 0.7}
    ],
    selatan: [
      {kecamatan: 'Wonokromo', mdpl: 6.7},
      {kecamatan: 'Wonocolo', mdpl: 5.7},
      {kecamatan: 'Wiyung', mdpl: 9.7},
      {kecamatan: 'Karang Pilang', mdpl: 8.7},
      {kecamatan: 'Jambangan', mdpl: 7.7},
      {kecamatan: 'Gayungan', mdpl: 6.7},
      {kecamatan: 'Dukuh Pakis', mdpl: 24.7},
      {kecamatan: 'Sawahan', mdpl: 18.7}
    ]
  };

  // Elemen DOM untuk bensin
  const jenisKendaraan = document.getElementById('jenisKendaraan');
  const mobilOptions = document.getElementById('mobilOptions');
  const motorOptions = document.getElementById('motorOptions');
  const jenisMobil = document.getElementById('jenisMobil');
  const nonhybridOptions = document.getElementById('nonhybridOptions');
  const jenisNonhybrid = document.getElementById('jenisNonhybrid');
  const jenisMotor = document.getElementById('jenisMotor');
  const jarakTempuh = document.getElementById('jarakTempuh');
  const hitungBensinBtn = document.getElementById('hitungBensinBtn');
  const hasilBensin = document.getElementById('hasilBensin');

  // Elemen DOM untuk tenggelam
  const wilayahSelect = document.getElementById('wilayah');
  const kecamatanSelect = document.getElementById('kecamatan');
  const hitungTenggelamBtn = document.getElementById('hitungTenggelamBtn');
  const hasilTenggelam = document.getElementById('hasilTenggelam');

  // Event listeners untuk bensin
  jenisKendaraan.addEventListener('change', () => {
    const jenis = jenisKendaraan.value;
    mobilOptions.classList.add('hidden');
    motorOptions.classList.add('hidden');
    nonhybridOptions.classList.add('hidden');
    jenisMobil.value = '';
    jenisNonhybrid.value = '';
    jenisMotor.value = '';
    hasilBensin.innerHTML = '';
    if (jenis === 'mobil') {
      mobilOptions.classList.remove('hidden');
    } else if (jenis === 'motor') {
      motorOptions.classList.remove('hidden');
    }
  });

  jenisMobil.addEventListener('change', () => {
    const mobil = jenisMobil.value;
    nonhybridOptions.classList.add('hidden');
    jenisNonhybrid.value = '';
    hasilBensin.innerHTML = '';
    if (mobil === 'nonhybrid') {
      nonhybridOptions.classList.remove('hidden');
    }
  });

  hitungBensinBtn.addEventListener('click', () => {
    const jenis = jenisKendaraan.value;
    const jt = parseFloat(jarakTempuh.value);
    if (!jenis || isNaN(jt) || jt < 0) {
      hasilBensin.innerHTML = '<p>Masukkan data yang valid.</p>';
      return;
    }

    let kendaraan;
    if (jenis === 'mobil') {
      const mobil = jenisMobil.value;
      if (mobil === 'hybrid') {
        kendaraan = konsumsiMobil[4];
      } else if (mobil === 'nonhybrid') {
        const nonhybrid = jenisNonhybrid.value;
        if (nonhybrid === 'lcgc') kendaraan = konsumsiMobil[0];
        else if (nonhybrid === 'mpv') kendaraan = konsumsiMobil[1];
        else if (nonhybrid === 'suv') kendaraan = konsumsiMobil[2];
        else if (nonhybrid === 'sedanmenengah') kendaraan = konsumsiMobil[3];
      }
    } else if (jenis === 'motor') {
      const motor = jenisMotor.value;
      if (motor === 'bebek') kendaraan = konsumsiMotor[0];
      else if (motor === 'skutik') kendaraan = konsumsiMotor[1];
      else if (motor === 'sport') kendaraan = konsumsiMotor[2];
      else if (motor === 'moge') kendaraan = konsumsiMotor[3];
    }

    if (!kendaraan) {
      hasilBensin.innerHTML = '<p>Pilih jenis kendaraan yang lengkap.</p>';
      return;
    }

    const bensin = kendaraan.konsumsi * jt;
    const harga = Math.round(bensin * 10000);
    hasilBensin.innerHTML = `
      <p><strong>Penggunaan bensin ${jenis} ${kendaraan.jenis} dengan jarak tempuh ${jt} Km:</strong> ${bensin.toFixed(3)} liter</p>
      <p><strong>Harga bensin:</strong> Rp${harga.toLocaleString()},00</p>
    `;
  });

  // Event listeners untuk tenggelam
  wilayahSelect.addEventListener('change', () => {
    const wilayah = wilayahSelect.value;
    kecamatanSelect.innerHTML = '<option value="">-- Pilih Kecamatan --</option>';
    hasilTenggelam.innerHTML = '';
    hitungTenggelamBtn.disabled = true;

    if (wilayah && dataWilayah[wilayah]) {
      const kecamatanList = dataWilayah[wilayah];
      kecamatanList.forEach((kec, idx) => {
        const option = document.createElement('option');
        option.value = idx;
        option.textContent = kec.kecamatan;
        kecamatanSelect.appendChild(option);
      });
      kecamatanSelect.disabled = false;
    } else {
      kecamatanSelect.disabled = true;
    }
  });

  kecamatanSelect.addEventListener('change', () => {
    hasilTenggelam.innerHTML = '';
    hitungTenggelamBtn.disabled = kecamatanSelect.value === '';
  });

  hitungTenggelamBtn.addEventListener('click', () => {
    const wilayah = wilayahSelect.value;
    const kecamatanIdx = kecamatanSelect.value;

    if (wilayah && kecamatanIdx !== '') {
      const kecamatan = dataWilayah[wilayah][parseInt(kecamatanIdx)];
      const mdpl = kecamatan.mdpl;
      const waktu = mdpl / 0.088;

      hasilTenggelam.innerHTML = `
        <p><strong>Kecamatan:</strong> ${kecamatan.kecamatan}</p>
        <p><strong>Ketinggian (MDPL):</strong> ${mdpl} meter</p>
        <p><strong>Perkiraan waktu akan tenggelam:</strong> ${waktu.toFixed(2)} tahun</p>
      `;
    }
  });
</script>

</body>
</html>
