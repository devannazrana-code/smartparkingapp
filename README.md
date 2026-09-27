<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Smart Parking — Struk Parkir Digital</title>
<style>
  :root{
    /* ==== PALET MAROON ==== */
    --maroon-900:#3b0a12;
    --maroon-800:#5a0f1c;
    --maroon-700:#7a1327;
    --maroon-600:#8f1a30;
    --maroon-500:#a82340;
    --maroon-400:#c13a58;
    --maroon-300:#e07a92;
    --cream-100:#fdf6ec;
    --cream-200:#f8ead5;
    --cream-300:#efd9b8;
    --paper:#fffaf0;
    --ink:#3a1a1a;
    --ink-soft:#6b4a4a;
    --gold:#c9a227;
    --gold-soft:#e6c860;
    --green:#4f7d4f;
    --shadow:0 18px 40px rgba(59,10,18,.35);
    --shadow-soft:0 10px 25px rgba(59,10,18,.18);
  }
  *{box-sizing:border-box;margin:0;padding:0}
  body{
    font-family:'Segoe UI',system-ui,-apple-system,sans-serif;
    background:
      radial-gradient(circle at 12% 8%,#7a132733 0%,transparent 40%),
      radial-gradient(circle at 88% 92%,#c13a5822 0%,transparent 45%),
      linear-gradient(160deg,#fdf6ec 0%,#f8ead5 60%,#efd9b8 100%);
    color:var(--ink);
    min-height:100vh;
    padding:32px 16px;
    line-height:1.6;
  }
  .container{max-width:920px;margin:0 auto}

  /* ================= HEADER ================= */
  .hero{
    background:linear-gradient(135deg,var(--maroon-900),var(--maroon-600) 60%,var(--maroon-400));
    border-radius:26px;
    padding:34px 32px;
    box-shadow:var(--shadow);
    position:relative;
    overflow:hidden;
    margin-bottom:26px;
    color:var(--cream-100);
  }
  .hero::before{
    content:"";
    position:absolute;inset:0;
    background:
      radial-gradient(circle at 82% 15%,rgba(255,255,255,.22),transparent 45%),
      radial-gradient(circle at 8% 95%,rgba(0,0,0,.25),transparent 45%);
  }
  .hero .icon{
    position:absolute;right:26px;top:50%;transform:translateY(-50%);
    font-size:6rem;opacity:.15;z-index:0;
  }
  .hero h1{
    font-size:clamp(1.4rem,3.4vw,2.1rem);
    position:relative;z-index:1;letter-spacing:.4px;
    font-family:'Georgia',serif;font-weight:800;
  }
  .hero p{position:relative;z-index:1;opacity:.92;margin-top:6px;font-size:.94rem}
  .badges{display:flex;gap:8px;flex-wrap:wrap;margin-top:16px;position:relative;z-index:1}
  .badge{
    background:rgba(255,250,240,.16);
    border:1px solid rgba(255,250,240,.35);
    padding:5px 13px;border-radius:999px;font-size:.75rem;font-weight:700;
    backdrop-filter:blur(6px);letter-spacing:.3px;
  }

  /* ================= CARD ================= */
  .card{
    background:var(--paper);
    border:1px solid var(--cream-300);
    border-radius:20px;
    padding:26px;
    box-shadow:var(--shadow-soft);
    margin-bottom:22px;
    animation:fade .5s ease;
  }
  @keyframes fade{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:translateY(0)}}
  .card h2{
    font-size:1.08rem;margin-bottom:16px;display:flex;align-items:center;gap:10px;
    color:var(--maroon-700);letter-spacing:.3px;font-family:'Georgia',serif;
  }
  .card h2 .num{
    background:linear-gradient(135deg,var(--maroon-700),var(--maroon-500));
    color:var(--cream-100);width:30px;height:30px;display:grid;place-items:center;
    border-radius:50%;font-weight:900;font-size:.9rem;box-shadow:0 4px 12px rgba(122,19,39,.35);
  }

  /* ================= TARIF CARD ================= */
  .tarif-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}
  @media(max-width:640px){.tarif-grid{grid-template-columns:1fr}}
  .tarif-item{
    background:linear-gradient(160deg,#fffaf0,#f8ead5);
    border:1px solid var(--cream-300);border-radius:16px;
    padding:18px 14px;text-align:center;position:relative;
    transition:transform .25s,border-color .25s,box-shadow .25s;
    overflow:hidden;
  }
  .tarif-item::after{
    content:"";position:absolute;left:0;right:0;bottom:0;height:4px;
    background:linear-gradient(90deg,var(--maroon-500),var(--gold));
    transform:scaleX(0);transition:transform .3s;
  }
  .tarif-item:hover{transform:translateY(-5px);border-color:var(--maroon-400);box-shadow:var(--shadow-soft)}
  .tarif-item:hover::after{transform:scaleX(1)}
  .tarif-item .emoji{font-size:1.7rem}
  .tarif-item .val{font-size:1.2rem;font-weight:900;color:var(--maroon-700);margin-top:4px}
  .tarif-item .lbl{font-size:.74rem;color:var(--ink-soft);margin-top:2px;letter-spacing:.3px;font-weight:600}

  /* ================= FORM ================= */
  .grid2{display:grid;grid-template-columns:1fr 1fr;gap:18px}
  @media(max-width:640px){.grid2{grid-template-columns:1fr}}
  label{
    display:block;font-size:.78rem;color:var(--maroon-700);margin-bottom:7px;
    font-weight:800;letter-spacing:.5px;text-transform:uppercase;
  }
  .input-wrap{position:relative}
  .input-wrap .unit{
    position:absolute;right:14px;top:50%;transform:translateY(-50%);
    color:var(--ink-soft);font-size:.8rem;font-weight:800;pointer-events:none;
  }
  input[type="number"]{
    width:100%;padding:14px 46px 14px 16px;border-radius:14px;
    border:2px solid var(--cream-300);
    background:#fffaf0;color:var(--ink);font-size:1.05rem;font-weight:700;
    outline:none;transition:border .2s,box-shadow .2s,background .2s;
  }
  input[type="number"]:focus{
    border-color:var(--maroon-500);
    box-shadow:0 0 0 4px rgba(168,35,64,.15);
    background:#fff;
  }

  /* ================= BUTTONS ================= */
  .btn-row{display:flex;gap:12px;flex-wrap:wrap;margin-top:22px}
  .btn{
    display:inline-flex;align-items:center;justify-content:center;gap:9px;
    padding:14px 26px;border-radius:14px;border:none;cursor:pointer;
    font-weight:800;font-size:.95rem;letter-spacing:.4px;
    transition:transform .15s,filter .2s,box-shadow .2s;
    font-family:inherit;
  }
  .btn:hover{transform:translateY(-2px);filter:brightness(1.08)}
  .btn:active{transform:translateY(0)}
  .btn-primary{
    background:linear-gradient(135deg,var(--maroon-700),var(--maroon-500));
    color:var(--cream-100);
    box-shadow:0 10px 24px rgba(122,19,39,.35);
  }
  .btn-primary:hover{box-shadow:0 14px 30px rgba(122,19,39,.45)}
  .btn-ghost{
    background:transparent;border:2px solid var(--maroon-300);
    color:var(--maroon-700);
  }
  .btn-ghost:hover{border-color:var(--maroon-700);background:rgba(168,35,64,.06)}
  .btn-danger{
    background:linear-gradient(135deg,var(--maroon-900),var(--maroon-700));
    color:var(--cream-100);
    box-shadow:0 10px 24px rgba(59,10,18,.35);
  }

  /* ================= STRUK ================= */
  .struk-wrap{
    margin-top:28px;
    display:flex;justify-content:center;
    animation:fadeUp .55s ease;
  }
  @keyframes fadeUp{from{opacity:0;transform:translateY(18px)}to{opacity:1;transform:translateY(0)}}

  .struk{
    width:100%;max-width:420px;
    background:#fffdf7;
    color:var(--ink);
    padding:26px 26px 22px;
    position:relative;
    filter:drop-shadow(0 14px 30px rgba(59,10,18,.28));
    font-family:'Courier New',monospace;
    /* efek sobekan atas & bawah */
    clip-path:polygon(
      0% 3%, 3% 0%, 6% 3%, 9% 0%, 12% 3%, 15% 0%, 18% 3%, 21% 0%,
      24% 3%, 27% 0%, 30% 3%, 33% 0%, 36% 3%, 39% 0%, 42% 3%, 45% 0%,
      48% 3%, 51% 0%, 54% 3%, 57% 0%, 60% 3%, 63% 0%, 66% 3%, 69% 0%,
      72% 3%, 75% 0%, 78% 3%, 81% 0%, 84% 3%, 87% 0%, 90% 3%, 93% 0%,
      96% 3%, 99% 0%, 100% 3%,
      100% 97%, 97% 100%, 94% 97%, 91% 100%, 88% 97%, 85% 100%, 82% 97%,
      79% 100%, 76% 97%, 73% 100%, 70% 97%, 67% 100%, 64% 97%, 61% 100%,
      58% 97%, 55% 100%, 52% 97%, 49% 100%, 46% 97%, 43% 100%, 40% 97%,
      37% 100%, 34% 97%, 31% 100%, 28% 97%, 25% 100%, 22% 97%, 19% 100%,
      16% 97%, 13% 100%, 10% 97%, 7% 100%, 4% 97%, 0% 97%
    );
  }
  .struk::before{
    content:"";
    position:absolute;inset:0;
    background:
      repeating-linear-gradient(0deg,rgba(122,19,39,.035) 0 2px,transparent 2px 4px);
    pointer-events:none;
  }

  .struk-header{text-align:center;padding-bottom:14px;border-bottom:2px dashed var(--maroon-300)}
  .struk-header .logo{
    width:54px;height:54px;border-radius:50%;margin:0 auto 8px;
    background:linear-gradient(135deg,var(--maroon-700),var(--maroon-500));
    display:grid;place-items:center;color:var(--cream-100);font-size:1.6rem;
    box-shadow:0 6px 14px rgba(122,19,39,.4);
  }
  .struk-header .brand{
    font-family:'Georgia',serif;font-weight:900;font-size:1.05rem;
    color:var(--maroon-800);letter-spacing:1px;
  }
  .struk-header .sub{font-size:.7rem;color:var(--ink-soft);letter-spacing:1.5px;margin-top:2px}
  .struk-header .no{
    margin-top:8px;font-size:.72rem;color:var(--maroon-600);
    background:var(--cream-200);display:inline-block;padding:3px 10px;border-radius:6px;
    font-weight:700;letter-spacing:1px;
  }

  .struk-body{padding:14px 0;font-size:.86rem}
  .struk-line{
    display:flex;justify-content:space-between;padding:6px 0;
    border-bottom:1px dotted var(--cream-300);
  }
  .struk-line:last-child{border-bottom:none}
  .struk-line .k{color:var(--ink-soft)}
  .struk-line .v{font-weight:700;color:var(--ink)}
  .struk-line .v.dis{color:var(--maroon-600)}

  .struk-divider{
    text-align:center;color:var(--maroon-300);
    font-size:.75rem;letter-spacing:3px;margin:10px 0;
    overflow:hidden;white-space:nowrap;
  }

  .struk-total{
    margin-top:10px;padding:16px 14px;border-radius:12px;
    background:linear-gradient(135deg,var(--maroon-800),var(--maroon-600));
    color:var(--cream-100);text-align:center;
    box-shadow:0 8px 20px rgba(90,15,28,.35);
  }
  .struk-total .lbl{font-size:.7rem;letter-spacing:3px;opacity:.85;font-weight:700}
  .struk-total .amt{
    font-size:1.7rem;font-weight:900;letter-spacing:1px;margin-top:4px;
    font-family:'Georgia',serif;
  }

  .struk-foot{
    text-align:center;padding-top:14px;border-top:2px dashed var(--maroon-300);
    font-size:.72rem;color:var(--ink-soft);line-height:1.7;
  }
  .struk-foot .thanks{
    font-family:'Georgia',serif;font-weight:800;color:var(--maroon-700);
    font-size:.86rem;letter-spacing:1px;margin-bottom:4px;
  }
  .struk-foot .barcode{
    margin-top:10px;height:38px;
    background:repeating-linear-gradient(90deg,
      var(--ink) 0 2px, transparent 2px 4px,
      var(--ink) 4px 5px, transparent 5px 9px,
      var(--ink) 9px 12px, transparent 12px 14px);
    border-radius:2px;opacity:.85;
  }

  /* ================= ERROR ================= */
  .error{
    margin-top:20px;padding:16px 20px;border-radius:14px;
    background:#fbe6e6;border:2px solid var(--maroon-400);
    color:var(--maroon-800);font-weight:700;font-size:.9rem;
    display:flex;align-items:center;gap:10px;
    animation:shake .4s ease;
  }
  @keyframes shake{0%,100%{transform:translateX(0)}25%{transform:translateX(-6px)}75%{transform:translateX(6px)}}

  /* ================= RIWAYAT ================= */
  .riwayat-list{display:flex;flex-direction:column;gap:12px;margin-top:8px}
  .riwayat-item{
    background:linear-gradient(160deg,#fffaf0,#f8ead5);
    border-left:5px solid var(--maroon-600);
    border-radius:12px;padding:14px 16px;
    display:flex;justify-content:space-between;align-items:center;gap:14px;
    flex-wrap:wrap;
    transition:transform .2s,box-shadow .2s;
  }
  .riwayat-item:hover{transform:translateX(4px);box-shadow:var(--shadow-soft)}
  .riwayat-item .info{font-size:.84rem;color:var(--ink-soft)}
  .riwayat-item .info b{color:var(--maroon-700);font-size:.95rem}
  .riwayat-item .info .dur{
    display:inline-block;background:var(--cream-200);color:var(--maroon-700);
    padding:2px 10px;border-radius:999px;font-size:.72rem;font-weight:800;margin-left:6px;
  }
  .riwayat-item .harga{
    font-size:1.1rem;font-weight:900;color:var(--maroon-700);
    font-family:'Georgia',serif;
  }
  .riwayat-item .harga small{display:block;font-size:.68rem;color:var(--ink-soft);font-weight:600;text-align:right}
  .empty{
    color:var(--ink-soft);font-size:.88rem;padding:20px;text-align:center;
    background:var(--cream-200);border-radius:12px;border:1px dashed var(--maroon-300);
  }

  footer{
    text-align:center;color:var(--ink-soft);font-size:.78rem;
    margin-top:28px;letter-spacing:.3px;
  }
</style>
</head>
<body>
<div class="container">

  <!-- ============ HERO ============ -->
  <header class="hero">
    <span class="icon">🅿️</span>
    <h1>Smart Parking</h1>
    <p>Hitung tarif parkir mobil Anda & dapatkan struk digital secara otomatis.</p>
    <div class="badges">
      <span class="badge">⏱️ 1 Jam Pertama · Rp 5.000</span>
      <span class="badge">➕ Jam Berikutnya · Rp 3.000</span>
      <span class="badge">🎁 Diskon Rp 2.000 jika &gt; 5 jam</span>
    </div>
  </header>

  <!-- ============ TARIF ============ -->
  <section class="card">
    <h2><span class="num">💰</span> Daftar Tarif</h2>
    <div class="tarif-grid">
      <div class="tarif-item">
        <div class="emoji">⏱️</div>
        <div class="val">Rp 5.000</div>
        <div class="lbl">1 Jam Pertama</div>
      </div>
      <div class="tarif-item">
        <div class="emoji">➕</div>
        <div class="val">Rp 3.000</div>
        <div class="lbl">Per Jam Berikutnya</div>
      </div>
      <div class="tarif-item">
        <div class="emoji">🎁</div>
        <div class="val">− Rp 2.000</div>
        <div class="lbl">Diskon &gt; 5 Jam</div>
      </div>
    </div>
  </section>

  <!-- ============ INPUT ============ -->
  <section class="card">
    <h2><span class="num">🧮</span> Masukkan Waktu Parkir</h2>
    <div class="grid2">
      <div>
        <label>🚗 Jam Masuk</label>
        <div class="input-wrap">
          <input type="number" id="jamMasuk" min="0" max="23" value="8" placeholder="0 - 23">
          <span class="unit">:00</span>
        </div>
      </div>
      <div>
        <label>🏁 Jam Keluar</label>
        <div class="input-wrap">
          <input type="number" id="jamKeluar" min="0" max="23" value="15" placeholder="0 - 23">
          <span class="unit">:00</span>
        </div>
      </div>
    </div>

    <div class="btn-row">
      <button class="btn btn-primary" onclick="hitungTarif()">🧾 Cetak Struk Parkir</button>
      <button class="btn btn-ghost" onclick="resetForm()">🔄 Reset</button>
      <button class="btn btn-danger" onclick="hapusRiwayat()">🗑️ Hapus Riwayat</button>
    </div>

    <div id="hasil"></div>
  </section>

  <!-- ============ RIWAYAT ============ -->
  <section class="card">
    <h2><span class="num">📋</span> Riwayat Parkir</h2>
    <div id="riwayatWrap">
      <div class="empty">Belum ada transaksi. Silakan cetak struk terlebih dahulu 🚗</div>
    </div>
  </section>

  <footer>LKPD Informatika Kelas XII · Smart Parking Simulator · Nuansa Maroon</footer>
</div>

<script>
/* =========================================================
   SMART PARKING — LOGIKA TARIF
   ========================================================= */
const TARIF_JAM_PERTAMA = 5000;
const TARIF_JAM_BERIKUTNYA = 3000;
const BATAS_DISKON = 5;
const NILAI_DISKON = 2000;

let riwayat = [];
let noStruk = 0;

function rupiah(angka){
  return 'Rp ' + angka.toLocaleString('id-ID');
}

/* ---------- VALIDASI ---------- */
function ambilInput(){
  const masuk  = document.getElementById('jamMasuk').value.trim();
  const keluar = document.getElementById('jamKeluar').value.trim();

  if(masuk === '' || keluar === ''){
    return {error:'Jam masuk dan jam keluar wajib diisi ya 🙏'};
  }
  const jm = Number(masuk);
  const jk = Number(keluar);

  if(!Number.isInteger(jm) || !Number.isInteger(jk)){
    return {error:'Jam harus berupa angka bulat.'};
  }
  if(jm < 0 || jm > 23 || jk < 0 || jk > 23){
    return {error:'Jam harus di antara 0 sampai 23.'};
  }
  if(jk <= jm){
    return {error:'Jam keluar harus lebih besar dari jam masuk.'};
  }
  return {jamMasuk: jm, jamKeluar: jk, durasi: jk - jm};
}

/* ---------- HITUNG + CETAK STRUK ---------- */
function hitungTarif(){
  const hasil = document.getElementById('hasil');
  const input = ambilInput();

  if(input.error){
    hasil.innerHTML = `<div class="error">⚠️ ${input.error}</div>`;
    return;
  }

  const {jamMasuk, jamKeluar, durasi} = input;

  let biayaDasar, rincian;
  if(durasi <= 1){
    biayaDasar = TARIF_JAM_PERTAMA;
    rincian = `1 jam pertama`;
  } else {
    biayaDasar = TARIF_JAM_PERTAMA + (durasi - 1) * TARIF_JAM_BERIKUTNYA;
    rincian = `1 jam pertama + ${durasi - 1} jam berikutnya`;
  }

  let diskon = 0;
  if(durasi > BATAS_DISKON){
    diskon = NILAI_DISKON;
  }
  const biayaAkhir = biayaDasar - diskon;

  noStruk++;
  const kodeStruk = 'SP-' + String(noStruk).padStart(4,'0');
  const waktuCetak = new Date().toLocaleString('id-ID',{
    day:'2-digit',month:'short',year:'numeric',
    hour:'2-digit',minute:'2-digit'
  });

  // Simpan riwayat
  riwayat.unshift({
    kode: kodeStruk,
    masuk: String(jamMasuk).padStart(2,'0') + ':00',
    keluar: String(jamKeluar).padStart(2,'0') + ':00',
    durasi: durasi,
    dasar: biayaDasar,
    diskon: diskon,
    akhir: biayaAkhir,
    waktu: waktuCetak
  });
  renderRiwayat();

  // Tampilkan struk
  hasil.innerHTML = `
    <div class="struk-wrap">
      <div class="struk">
        <div class="struk-header">
          <div class="logo">🅿️</div>
          <div class="brand">SMART PARKING</div>
          <div class="sub">PUSAT PERBELANJAAN</div>
          <div class="no">${kodeStruk}</div>
        </div>

        <div class="struk-body">
          <div class="struk-line"><span class="k">Tanggal</span><span class="v">${waktuCetak}</span></div>
          <div class="struk-line"><span class="k">Jam Masuk</span><span class="v">${String(jamMasuk).padStart(2,'0')}:00</span></div>
          <div class="struk-line"><span class="k">Jam Keluar</span><span class="v">${String(jamKeluar).padStart(2,'0')}:00</span></div>
          <div class="struk-line"><span class="k">Durasi Parkir</span><span class="v">${durasi} jam</span></div>

          <div class="struk-divider">• • • • • • • • • • • • • • • • • •</div>

          <div class="struk-line"><span class="k">Rincian</span><span class="v">${rincian}</span></div>
          <div class="struk-line"><span class="k">Biaya Dasar</span><span class="v">${rupiah(biayaDasar)}</span></div>
          <div class="struk-line">
            <span class="k">Diskon (&gt;5 jam)</span>
            <span class="v ${diskon > 0 ? 'dis' : ''}">
              ${diskon > 0 ? '− ' + rupiah(diskon) : 'Tidak berlaku'}
            </span>
          </div>

          <div class="struk-total">
            <div class="lbl">TOTAL BAYAR</div>
            <div class="amt">${rupiah(biayaAkhir)}</div>
          </div>
        </div>

        <div class="struk-foot">
          <div class="thanks">TERIMA KASIH 🙏</div>
          <div>Simpan struk ini sebagai bukti pembayaran</div>
          <div>Parkir aman · Kendaraan nyaman</div>
          <div class="barcode"></div>
        </div>
      </div>
    </div>
  `;
}

/* ---------- RESET ---------- */
function resetForm(){
  document.getElementById('jamMasuk').value = 8;
  document.getElementById('jamKeluar').value = 15;
  document.getElementById('hasil').innerHTML = '';
}

/* ---------- RIWAYAT ---------- */
function renderRiwayat(){
  const wrap = document.getElementById('riwayatWrap');

  if(riwayat.length === 0){
    wrap.innerHTML = `<div class="empty">Belum ada transaksi. Silakan cetak struk terlebih dahulu 🚗</div>`;
    return;
  }

  wrap.innerHTML = `<div class="riwayat-list">${
    riwayat.map(r => `
      <div class="riwayat-item">
        <div class="info">
          <b>${r.kode}</b> · ${r.waktu}<br>
          Masuk ${r.masuk} → Keluar ${r.keluar}
          <span class="dur">${r.durasi} jam</span>
          ${r.diskon > 0 ? `<span class="dur" style="background:#f3d9a4;color:#7a5a10">🎁 Diskon ${rupiah(r.diskon)}</span>` : ''}
        </div>
        <div class="harga">
          ${rupiah(r.akhir)}
          <small>${r.diskon > 0 ? 'sebelum: ' + rupiah(r.dasar) : 'tanpa diskon'}</small>
        </div>
      </div>
    `).join('')
  }</div>`;
}

function hapusRiwayat(){
  if(riwayat.length === 0){
    alert('Riwayat masih kosong.');
    return;
  }
  if(confirm('Yakin ingin menghapus semua riwayat parkir?')){
    riwayat = [];
    noStruk = 0;
    renderRiwayat();
  }
}

/* ---------- ENTER UNTUK HITUNG ---------- */
document.addEventListener('DOMContentLoaded', () => {
  ['jamMasuk','jamKeluar'].forEach(id => {
    document.getElementById(id).addEventListener('keydown', e => {
      if(e.key === 'Enter') hitungTarif();
    });
  });
});
</script>
</body>
</html>
