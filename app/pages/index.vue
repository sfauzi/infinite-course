<script setup lang="ts">
const isMenuOpen = ref(false);
const activeAccordion = ref<number | null>(null);

const navLinks = [
  { label: "Home", href: "#home" },
  { label: "Program", href: "#program" },
  { label: "Tentor", href: "#tentor" },
  { label: "Testimoni", href: "#testimoni" },
  { label: "FAQ", href: "#faq" },
  { label: "Kontak", href: "#kontak" },
];

const programs = [
  {
    icon: "heroicons:academic-cap",
    title: "Bimbel SD",
    desc:
      "Fondasi akademik yang kuat untuk siswa sekolah dasar dengan pendekatan fun learning.",
    subjects: ["Matematika", "IPA", "Bahasa Indonesia", "IPS"],
    system: "Tatap Muka & Online",
    schedule: "Senin – Sabtu",
    color: "from-amber-400 to-amber-500",
  },
  {
    icon: "heroicons:book-open",
    title: "Bimbel SMP",
    desc:
      "Persiapan ujian dan pemantapan materi untuk siswa SMP dengan modul terstruktur.",
    subjects: ["Matematika", "IPA Terpadu", "Bahasa Inggris", "IPS"],
    system: "Tatap Muka & Hybrid",
    schedule: "Senin – Sabtu",
    color: "from-amber-500 to-orange-500",
  },
  {
    icon: "heroicons:light-bulb",
    title: "Bimbel SMA",
    desc: "Pendalaman materi UN & persiapan masuk perguruan tinggi terbaik Indonesia.",
    subjects: ["Matematika", "Fisika", "Kimia", "Biologi", "Ekonomi"],
    system: "Tatap Muka & Online",
    schedule: "Senin – Sabtu",
    color: "from-amber-400 to-yellow-500",
  },
  {
    icon: "heroicons:trophy",
    title: "Persiapan SNBT",
    desc:
      "Program intensif khusus lolos SNBT dengan tryout nasional dan pembahasan mendalam.",
    subjects: ["TPS", "Literasi", "Penalaran Matematika", "Sains & Teknologi"],
    system: "Intensif & Full Online",
    schedule: "Setiap Hari",
    color: "from-orange-400 to-amber-500",
  },
  {
    icon: "heroicons:shield-check",
    title: "SKD CPNS",
    desc: "Bimbingan khusus SKD CPNS dengan simulasi CAT dan strategi mengerjakan soal.",
    subjects: ["TWK", "TIU", "TKP"],
    system: "Online & Offline",
    schedule: "Fleksibel",
    color: "from-amber-600 to-orange-500",
  },
];

const whyUs = [
  {
    icon: "heroicons:user-group",
    title: "Tentor Profesional",
    desc: "Lulusan universitas terbaik dengan pengalaman mengajar terstruktur.",
  },
  {
    icon: "heroicons:document-text",
    title: "Modul Lengkap",
    desc: "Materi belajar eksklusif yang terus diperbarui sesuai kurikulum terkini.",
  },
  {
    icon: "heroicons:computer-desktop",
    title: "Kelas Interaktif",
    desc: "Metode diskusi aktif dan media belajar digital yang menarik.",
  },
  {
    icon: "heroicons:chart-bar",
    title: "Tryout Berkala",
    desc: "Evaluasi rutin dengan bank soal ribuan pertanyaan tervalidasi.",
  },
  {
    icon: "heroicons:chart-pie",
    title: "Monitoring Perkembangan",
    desc: "Laporan belajar berkala untuk orang tua dan siswa.",
  },
  {
    icon: "heroicons:chat-bubble-left-right",
    title: "Konsultasi Belajar",
    desc: "Sesi konsultasi personal tanpa batas bersama tentor terpilih.",
  },
];

const stats = [
  { value: "10.000+", label: "Siswa Aktif", icon: "heroicons:users" },
  { value: "25.000+", label: "Alumni", icon: "heroicons:academic-cap" },
  { value: "150+", label: "Tentor Aktif", icon: "heroicons:user-circle" },
  { value: "95%", label: "Lolos PTN", icon: "heroicons:trophy" },
  { value: "12", label: "Cabang Belajar", icon: "heroicons:map-pin" },
];

const methods = [
  {
    step: "01",
    icon: "heroicons:user-group",
    title: "Small Class",
    desc: "Kelas kecil maksimal 10 siswa untuk perhatian optimal dari tentor.",
  },
  {
    step: "02",
    icon: "heroicons:computer-desktop",
    title: "Hybrid Learning",
    desc: "Kombinasi tatap muka dan online untuk fleksibilitas belajar maksimal.",
  },
  {
    step: "03",
    icon: "heroicons:adjustments-horizontal",
    title: "Personalized Learning",
    desc: "Kurikulum disesuaikan dengan kebutuhan dan kemampuan tiap siswa.",
  },
  {
    step: "04",
    icon: "heroicons:clipboard-document-check",
    title: "Evaluasi Mingguan",
    desc: "Tes mingguan untuk mengukur perkembangan dan pemahaman materi.",
  },
  {
    step: "05",
    icon: "heroicons:heart",
    title: "Pendampingan Intensif",
    desc: "Tentor siap mendampingi di luar jam belajar untuk sesi tanya jawab.",
  },
];

const universities = [
  { name: "Universitas Indonesia", short: "UI", color: "bg-yellow-400" },
  { name: "Universitas Gadjah Mada", short: "UGM", color: "bg-blue-600" },
  { name: "Institut Teknologi Bandung", short: "ITB", color: "bg-green-600" },
  { name: "Universitas Diponegoro", short: "UNDIP", color: "bg-red-600" },
  { name: "Universitas Airlangga", short: "UNAIR", color: "bg-blue-800" },
  { name: "Institut Teknologi Sepuluh Nopember", short: "ITS", color: "bg-gray-700" },
];

const testimonials = [
  {
    name: "Rahma Aulia",
    school: "SMAN 3 Purwokerto",
    review:
      "Berkat bimbel di sini saya berhasil lolos SNBT di Universitas Indonesia jurusan Kedokteran. Metode belajarnya efektif banget!",
    rating: 5,
    program: "SNBT",
    avatar: "https://i.pravatar.cc/100?img=47",
  },
  {
    name: "Dimas Prasetyo",
    school: "SMA Muhammadiyah 1",
    review:
      "Tentor-tentornya sabar dan berpengalaman. Nilai Matematika dan Fisika saya naik drastis dalam 3 bulan.",
    rating: 5,
    program: "SMA",
    avatar: "https://i.pravatar.cc/100?img=12",
  },
  {
    name: "Sari Wulandari",
    school: "Ibu Siswa SD",
    review:
      "Anak saya jadi lebih semangat belajar dan nilainya meningkat pesat. Terima kasih Learning Today!",
    rating: 5,
    program: "SD",
    avatar: "https://i.pravatar.cc/100?img=32",
  },
  {
    name: "Budi Santoso",
    school: "Peserta CPNS 2024",
    review:
      "Lolos SKD CPNS di percobaan pertama! Modul dan simulasi CAT-nya sangat membantu persiapan saya.",
    rating: 5,
    program: "SKD CPNS",
    avatar: "https://i.pravatar.cc/100?img=8",
  },
];

const mentors = [
  {
    name: "Dr. Arif Hidayat",
    subject: "Matematika & Fisika",
    university: "Lulusan ITB",
    experience: "8 Tahun Pengalaman",
    avatar: "https://i.pravatar.cc/150?img=3",
  },
  {
    name: "Dra. Siti Nurhaliza",
    subject: "Biologi & Kimia",
    university: "Lulusan UGM",
    experience: "10 Tahun Pengalaman",
    avatar: "https://i.pravatar.cc/150?img=45",
  },
  {
    name: "M. Fajar Ramadhan, S.Pd",
    subject: "TPS & SNBT",
    university: "Lulusan UI",
    experience: "6 Tahun Pengalaman",
    avatar: "https://i.pravatar.cc/150?img=15",
  },
  {
    name: "Dewi Kartika, S.Si",
    subject: "Bahasa Inggris & IPS",
    university: "Lulusan UNDIP",
    experience: "5 Tahun Pengalaman",
    avatar: "https://i.pravatar.cc/150?img=49",
  },
];

const faqs = [
  {
    q: "Bagaimana sistem belajar di Learning Today?",
    a:
      "Kami menggunakan sistem hybrid (online dan offline) dengan kelas kecil maksimal 10 siswa. Setiap siswa mendapatkan perhatian personal dari tentor berpengalaman.",
  },
  {
    q: "Berapa biaya pendaftaran program bimbel?",
    a:
      "Biaya bervariasi tergantung program yang dipilih. Silakan hubungi admin kami untuk informasi biaya lengkap dan paket promo yang tersedia.",
  },
  {
    q: "Apakah ada program trial atau konsultasi gratis?",
    a:
      "Ya! Kami menyediakan sesi konsultasi gratis untuk membantu menentukan program belajar yang paling sesuai dengan kebutuhan siswa.",
  },
  {
    q: "Bagaimana cara mendaftar di Learning Today?",
    a:
      "Pendaftaran bisa dilakukan secara online melalui WhatsApp atau datang langsung ke kantor kami. Proses sangat mudah dan cepat, hanya 15 menit!",
  },
  {
    q: "Apakah tersedia program intensif menjelang ujian?",
    a:
      "Kami menyediakan program intensif khusus menjelang SNBT, UN, dan CPNS dengan jadwal belajar lebih padat dan tryout simulasi rutin.",
  },
  {
    q: "Apakah ada monitoring perkembangan belajar anak?",
    a:
      "Orang tua akan menerima laporan perkembangan belajar secara berkala setiap bulan, termasuk nilai tryout, kehadiran, dan rekomendasi belajar dari tentor.",
  },
];

const toggleAccordion = (index: number) => {
  activeAccordion.value = activeAccordion.value === index ? null : index;
};

const whatsappUrl =
  "https://wa.me/6281234567890?text=Halo%2C%20saya%20ingin%20daftar%20bimbel%20Learning%20Today";
</script>

<template>
  <div class="min-h-screen font-sans bg-white text-gray-900">
    <!-- ===== STICKY NAVBAR ===== -->
    <header
      class="fixed top-0 left-0 right-0 z-50 bg-white/80 backdrop-blur-xl border-b border-amber-100 shadow-sm"
    >
      <nav class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-16">
          <!-- Logo -->
          <a href="#home" class="flex items-center gap-2 group">
            <div
              class="w-8 h-8 rounded-lg bg-gradient-to-br from-amber-400 to-amber-600 flex items-center justify-center shadow"
            >
              <Icon name="heroicons:academic-cap" class="w-5 h-5 text-white" />
            </div>
            <div class="leading-tight">
              <p class="text-xs font-bold text-amber-600 tracking-wide uppercase">
                Learning Today
              </p>
              <p class="text-[10px] text-gray-400 font-medium tracking-widest">
                LEADING TOMORROW
              </p>
            </div>
          </a>

          <!-- Desktop Menu -->
          <ul class="hidden lg:flex items-center gap-1">
            <li v-for="link in navLinks" :key="link.label">
              <a
                :href="link.href"
                class="px-3 py-2 text-sm font-medium text-gray-600 rounded-lg hover:text-amber-600 hover:bg-amber-50 transition-all duration-200"
              >
                {{ link.label }}
              </a>
            </li>
          </ul>

          <!-- CTA Button -->
          <div class="hidden lg:flex items-center gap-3">
            <a
              :href="whatsappUrl"
              target="_blank"
              class="flex items-center gap-2 px-5 py-2 bg-gradient-to-r from-amber-400 to-amber-500 text-white text-sm font-semibold rounded-full shadow-md hover:shadow-amber-200 hover:shadow-lg transition-all duration-300 hover:-translate-y-0.5"
            >
              <Icon name="heroicons:phone" class="w-4 h-4" />
              Daftar Sekarang
            </a>
          </div>

          <!-- Mobile Menu Button -->
          <button
            @click="isMenuOpen = !isMenuOpen"
            class="lg:hidden p-2 rounded-lg text-gray-600 hover:bg-amber-50"
          >
            <Icon
              :name="isMenuOpen ? 'heroicons:x-mark' : 'heroicons:bars-3'"
              class="w-5 h-5"
            />
          </button>
        </div>

        <!-- Mobile Menu -->
        <div v-if="isMenuOpen" class="lg:hidden pb-4 pt-2 border-t border-amber-50">
          <ul class="space-y-1">
            <li v-for="link in navLinks" :key="link.label">
              <a
                :href="link.href"
                @click="isMenuOpen = false"
                class="block px-3 py-2 text-sm font-medium text-gray-600 rounded-lg hover:text-amber-600 hover:bg-amber-50"
              >
                {{ link.label }}
              </a>
            </li>
          </ul>
          <a
            :href="whatsappUrl"
            target="_blank"
            class="mt-3 flex items-center justify-center gap-2 px-5 py-2.5 bg-gradient-to-r from-amber-400 to-amber-500 text-white text-sm font-semibold rounded-xl"
          >
            Daftar Sekarang
          </a>
        </div>
      </nav>
    </header>

    <!-- ===== HERO SECTION ===== -->
    <section
      id="home"
      class="relative min-h-screen flex items-center overflow-hidden pt-16"
    >
      <!-- Background -->
      <div
        class="absolute inset-0 bg-gradient-to-br from-amber-50 via-white to-orange-50"
      ></div>
      <div
        class="absolute top-0 right-0 w-[600px] h-[600px] bg-amber-100/50 rounded-full -translate-y-1/2 translate-x-1/4 blur-3xl"
      ></div>
      <div
        class="absolute bottom-0 left-0 w-[400px] h-[400px] bg-orange-100/40 rounded-full translate-y-1/2 -translate-x-1/4 blur-2xl"
      ></div>
      <!-- Grid pattern -->
      <div
        class="absolute inset-0 opacity-[0.03]"
        style="
          background-image: linear-gradient(#f59e0b 1px, transparent 1px),
            linear-gradient(90deg, #f59e0b 1px, transparent 1px);
          background-size: 40px 40px;
        "
      ></div>

      <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20 lg:py-28">
        <div class="grid lg:grid-cols-2 gap-12 items-center">
          <!-- Left Content -->
          <div>
            <!-- Badge -->
            <div
              class="inline-flex items-center gap-2 px-4 py-1.5 bg-amber-100 text-amber-700 rounded-full text-xs font-semibold mb-6 border border-amber-200"
            >
              <span class="w-1.5 h-1.5 rounded-full bg-amber-500 animate-pulse"></span>
              Bimbel Terpercaya #1 di Purwokerto
            </div>

            <h1
              class="text-4xl sm:text-5xl lg:text-6xl font-black text-gray-900 leading-tight mb-6"
            >
              Learning Today,<br />
              <span
                class="text-transparent bg-clip-text bg-gradient-to-r from-amber-500 to-orange-500"
                >Leading Tomorrow</span
              >
            </h1>

            <p class="text-gray-500 text-lg leading-relaxed mb-8 max-w-lg">
              Bimbingan belajar terpercaya untuk SD, SMP, SMA, SNBT, dan SKD dengan tentor
              berpengalaman dan metode belajar modern.
            </p>

            <div class="flex flex-wrap gap-3 mb-10">
              <a
                :href="whatsappUrl"
                target="_blank"
                class="flex items-center gap-2 px-7 py-3.5 bg-gradient-to-r from-amber-400 to-amber-500 text-white font-bold rounded-2xl shadow-lg shadow-amber-200 hover:shadow-xl hover:shadow-amber-300 hover:-translate-y-1 transition-all duration-300"
              >
                <Icon name="heroicons:rocket-launch" class="w-5 h-5" />
                Daftar Sekarang
              </a>
              <a
                :href="whatsappUrl"
                target="_blank"
                class="flex items-center gap-2 px-7 py-3.5 bg-white text-amber-600 font-bold rounded-2xl border-2 border-amber-200 hover:border-amber-400 hover:bg-amber-50 hover:-translate-y-1 transition-all duration-300 shadow-sm"
              >
                <Icon name="heroicons:chat-bubble-left-ellipsis" class="w-5 h-5" />
                Konsultasi Gratis
              </a>
            </div>

            <!-- Floating Badges -->
            <div class="flex flex-wrap gap-3">
              <div
                class="flex items-center gap-2 px-4 py-2 bg-white rounded-xl border border-gray-100 shadow-md"
              >
                <Icon name="heroicons:users" class="w-4 h-4 text-amber-500" />
                <span class="text-sm font-bold text-gray-800">10.000+ Siswa</span>
              </div>
              <div
                class="flex items-center gap-2 px-4 py-2 bg-white rounded-xl border border-gray-100 shadow-md"
              >
                <Icon name="heroicons:trophy" class="w-4 h-4 text-amber-500" />
                <span class="text-sm font-bold text-gray-800">95% Lolos PTN</span>
              </div>
              <div
                class="flex items-center gap-2 px-4 py-2 bg-white rounded-xl border border-gray-100 shadow-md"
              >
                <Icon name="heroicons:star" class="w-4 h-4 text-amber-400" />
                <span class="text-sm font-bold text-gray-800">Rating 4.9</span>
              </div>
            </div>
          </div>

          <!-- Right Illustration -->
          <div class="relative hidden lg:flex items-center justify-center">
            <div class="relative w-full max-w-md aspect-square">
              <!-- Main visual circle -->
              <div
                class="absolute inset-0 bg-gradient-to-br from-amber-100 to-orange-100 rounded-[2.5rem] rotate-3"
              ></div>
              <div
                class="absolute inset-0 bg-white rounded-[2rem] overflow-hidden shadow-2xl"
              >
                <img
                  src="https://images.unsplash.com/photo-1522202176988-66273c2fd55f?w=600&q=80"
                  alt="Siswa belajar modern"
                  class="w-full h-full object-cover"
                />
                <div
                  class="absolute inset-0 bg-gradient-to-t from-amber-900/30 via-transparent to-transparent"
                ></div>
              </div>
              <!-- Floating cards -->
              <div
                class="absolute -top-4 -left-8 bg-white rounded-2xl shadow-xl p-3 border border-amber-50"
              >
                <div class="flex items-center gap-2">
                  <div
                    class="w-8 h-8 rounded-xl bg-amber-100 flex items-center justify-center"
                  >
                    <Icon
                      name="heroicons:chart-bar-square"
                      class="w-4 h-4 text-amber-600"
                    />
                  </div>
                  <div>
                    <p class="text-xs text-gray-400">Progress</p>
                    <p class="text-sm font-bold text-gray-800">+45% nilai</p>
                  </div>
                </div>
              </div>
              <div
                class="absolute -bottom-4 -right-6 bg-white rounded-2xl shadow-xl p-3 border border-amber-50"
              >
                <div class="flex items-center gap-2">
                  <div
                    class="w-8 h-8 rounded-xl bg-green-100 flex items-center justify-center"
                  >
                    <Icon name="heroicons:check-circle" class="w-4 h-4 text-green-600" />
                  </div>
                  <div>
                    <p class="text-xs text-gray-400">Lolos SNBT</p>
                    <p class="text-sm font-bold text-gray-800">Batch 2024</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== PROGRAM SECTION ===== -->
    <section id="program" class="py-20 bg-gray-50">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Header -->
        <div class="text-center mb-14">
          <span
            class="inline-block px-4 py-1.5 bg-amber-100 text-amber-600 text-xs font-bold rounded-full uppercase tracking-widest mb-4"
            >Program Unggulan</span
          >
          <h2 class="text-3xl lg:text-4xl font-black text-gray-900 mb-3">
            Program Bimbingan Belajar
          </h2>
          <p class="text-gray-400 max-w-lg mx-auto">
            Pilih program yang sesuai dengan kebutuhan akademikmu dan raih prestasi
            terbaik.
          </p>
        </div>

        <!-- Cards -->
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div
            v-for="(prog, i) in programs"
            :key="i"
            class="group bg-white rounded-2xl border border-gray-100 shadow-sm hover:shadow-xl hover:-translate-y-1.5 transition-all duration-300 overflow-hidden"
          >
            <!-- Card Header -->
            <div :class="`bg-gradient-to-r ${prog.color} p-5`">
              <div class="flex items-center gap-3">
                <div
                  class="w-10 h-10 rounded-xl bg-white/20 backdrop-blur flex items-center justify-center"
                >
                  <Icon :name="prog.icon" class="w-5 h-5 text-white" />
                </div>
                <h3 class="text-lg font-bold text-white">{{ prog.title }}</h3>
              </div>
            </div>
            <!-- Card Body -->
            <div class="p-5">
              <p class="text-gray-500 text-sm leading-relaxed mb-4">{{ prog.desc }}</p>
              <div class="space-y-2.5 text-sm mb-5">
                <div class="flex items-start gap-2">
                  <Icon
                    name="heroicons:book-open"
                    class="w-4 h-4 text-amber-500 mt-0.5 shrink-0"
                  />
                  <span class="text-gray-600">{{ prog.subjects.join(", ") }}</span>
                </div>
                <div class="flex items-center gap-2">
                  <Icon
                    name="heroicons:computer-desktop"
                    class="w-4 h-4 text-amber-500 shrink-0"
                  />
                  <span class="text-gray-600">{{ prog.system }}</span>
                </div>
                <div class="flex items-center gap-2">
                  <Icon
                    name="heroicons:calendar"
                    class="w-4 h-4 text-amber-500 shrink-0"
                  />
                  <span class="text-gray-600">{{ prog.schedule }}</span>
                </div>
              </div>
              <a
                :href="whatsappUrl"
                target="_blank"
                class="flex items-center justify-center gap-2 w-full py-2.5 border-2 border-amber-400 text-amber-600 font-semibold rounded-xl text-sm hover:bg-amber-400 hover:text-white transition-all duration-200"
              >
                Detail Program
                <Icon name="heroicons:arrow-right" class="w-4 h-4" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== WHY CHOOSE US ===== -->
    <section class="py-20 bg-white">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid lg:grid-cols-2 gap-14 items-center">
          <!-- Image Side -->
          <div class="relative order-2 lg:order-1">
            <div class="relative rounded-3xl overflow-hidden aspect-[4/3] shadow-2xl">
              <img
                src="https://images.unsplash.com/photo-1524178232363-1fb2b075b655?w=700&q=80"
                alt="Kelas interaktif"
                class="w-full h-full object-cover"
              />
              <div
                class="absolute inset-0 bg-gradient-to-tr from-amber-900/20 to-transparent"
              ></div>
            </div>
            <div
              class="absolute -bottom-5 -right-5 bg-amber-400 rounded-2xl p-5 shadow-xl"
            >
              <p class="text-white text-3xl font-black">12+</p>
              <p class="text-amber-100 text-xs font-medium">Tahun Pengalaman</p>
            </div>
          </div>

          <!-- Content Side -->
          <div class="order-1 lg:order-2">
            <span
              class="inline-block px-4 py-1.5 bg-amber-100 text-amber-600 text-xs font-bold rounded-full uppercase tracking-widest mb-4"
              >Mengapa Kami</span
            >
            <h2 class="text-3xl lg:text-4xl font-black text-gray-900 mb-3">
              Keunggulan Learning Today
            </h2>
            <p class="text-gray-400 mb-8">
              Kami berkomitmen memberikan pengalaman belajar terbaik dengan standar
              kualitas tertinggi.
            </p>

            <div class="grid sm:grid-cols-2 gap-4">
              <div
                v-for="(item, i) in whyUs"
                :key="i"
                class="flex gap-3 p-4 rounded-xl hover:bg-amber-50 transition-colors duration-200 group"
              >
                <div
                  class="w-10 h-10 rounded-xl bg-amber-100 flex items-center justify-center shrink-0 group-hover:bg-amber-200 transition-colors"
                >
                  <Icon :name="item.icon" class="w-5 h-5 text-amber-600" />
                </div>
                <div>
                  <h4 class="font-bold text-gray-800 text-sm mb-0.5">{{ item.title }}</h4>
                  <p class="text-gray-400 text-xs leading-relaxed">{{ item.desc }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== STATISTICS ===== -->
    <section
      class="py-20 bg-gradient-to-br from-amber-500 to-orange-500 relative overflow-hidden"
    >
      <div
        class="absolute inset-0 opacity-10"
        style="
          background-image: radial-gradient(circle at 25% 25%, white 2px, transparent 2px),
            radial-gradient(circle at 75% 75%, white 2px, transparent 2px);
          background-size: 60px 60px;
        "
      ></div>
      <div class="relative max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12">
          <h2 class="text-3xl lg:text-4xl font-black text-white mb-2">Pencapaian Kami</h2>
          <p class="text-amber-100">
            Angka nyata yang membuktikan kualitas pendidikan kami.
          </p>
        </div>
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-6">
          <div
            v-for="(stat, i) in stats"
            :key="i"
            class="text-center bg-white/10 backdrop-blur rounded-2xl p-6 border border-white/20 hover:bg-white/20 transition-all duration-300"
          >
            <Icon :name="stat.icon" class="w-7 h-7 text-amber-200 mx-auto mb-3" />
            <p class="text-3xl font-black text-white mb-1">{{ stat.value }}</p>
            <p class="text-amber-100 text-xs font-medium">{{ stat.label }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== LEARNING METHOD ===== -->
    <section class="py-20 bg-gray-50">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-14">
          <span
            class="inline-block px-4 py-1.5 bg-amber-100 text-amber-600 text-xs font-bold rounded-full uppercase tracking-widest mb-4"
            >Metode Belajar</span
          >
          <h2 class="text-3xl lg:text-4xl font-black text-gray-900 mb-3">
            Cara Kami Membelajarkan
          </h2>
          <p class="text-gray-400 max-w-lg mx-auto">
            Sistem belajar modern yang terbukti meningkatkan prestasi siswa secara
            konsisten.
          </p>
        </div>

        <div class="relative">
          <!-- Line connector (desktop) -->
          <div
            class="hidden lg:block absolute top-10 left-0 right-0 h-0.5 bg-gradient-to-r from-transparent via-amber-200 to-transparent"
          ></div>
          <div class="grid md:grid-cols-3 lg:grid-cols-5 gap-6">
            <div
              v-for="(method, i) in methods"
              :key="i"
              class="relative text-center group"
            >
              <!-- Step circle -->
              <div
                class="relative z-10 w-16 h-16 rounded-2xl bg-gradient-to-br from-amber-400 to-amber-500 flex items-center justify-center mx-auto mb-4 shadow-lg shadow-amber-200 group-hover:scale-110 transition-transform duration-300"
              >
                <Icon :name="method.icon" class="w-7 h-7 text-white" />
              </div>
              <span
                class="inline-block text-xs font-black text-amber-400 mb-2 tracking-widest"
                >{{ method.step }}</span
              >
              <h3 class="font-bold text-gray-800 mb-2">{{ method.title }}</h3>
              <p class="text-gray-400 text-sm leading-relaxed">{{ method.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== ALUMNI UNIVERSITIES ===== -->
    <section class="py-20 bg-white">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12">
          <span
            class="inline-block px-4 py-1.5 bg-amber-100 text-amber-600 text-xs font-bold rounded-full uppercase tracking-widest mb-4"
            >Alumni Kami</span
          >
          <h2 class="text-3xl lg:text-4xl font-black text-gray-900 mb-3">
            Kampus Tujuan Alumni
          </h2>
          <p class="text-gray-400">
            Ratusan siswa berhasil masuk kampus impian bersama Learning Today.
          </p>
        </div>

        <div class="grid grid-cols-3 md:grid-cols-6 gap-4 mb-8">
          <div
            v-for="(univ, i) in universities"
            :key="i"
            class="group flex flex-col items-center gap-3 p-5 rounded-2xl border border-gray-100 hover:border-amber-200 hover:shadow-lg hover:-translate-y-1 transition-all duration-300"
          >
            <div
              :class="`w-14 h-14 ${univ.color} rounded-xl flex items-center justify-center shadow-md group-hover:scale-110 transition-transform duration-300`"
            >
              <span class="text-white font-black text-sm">{{ univ.short }}</span>
            </div>
            <p class="text-xs text-center text-gray-500 font-medium leading-tight">
              {{ univ.name }}
            </p>
          </div>
        </div>

        <p class="text-center text-gray-400 text-sm">
          <Icon name="heroicons:map-pin" class="w-4 h-4 inline text-amber-400 mr-1" />
          dan masih banyak perguruan tinggi negeri & swasta terkemuka lainnya.
        </p>
      </div>
    </section>

    <!-- ===== TESTIMONIALS ===== -->
    <section id="testimoni" class="py-20 bg-gray-50">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-14">
          <span
            class="inline-block px-4 py-1.5 bg-amber-100 text-amber-600 text-xs font-bold rounded-full uppercase tracking-widest mb-4"
            >Testimoni</span
          >
          <h2 class="text-3xl lg:text-4xl font-black text-gray-900 mb-3">
            Cerita Sukses Siswa Kami
          </h2>
          <p class="text-gray-400">
            Ribuan siswa telah membuktikan efektivitas program belajar kami.
          </p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
          <div
            v-for="(t, i) in testimonials"
            :key="i"
            class="bg-white rounded-2xl p-6 border border-gray-100 shadow-sm hover:shadow-xl hover:-translate-y-1.5 transition-all duration-300"
          >
            <!-- Rating -->
            <div class="flex gap-0.5 mb-4">
              <Icon
                v-for="s in t.rating"
                :key="s"
                name="heroicons:star-solid"
                class="w-4 h-4 text-amber-400"
              />
            </div>
            <!-- Quote -->
            <p class="text-gray-600 text-sm leading-relaxed mb-5 italic">
              "{{ t.review }}"
            </p>
            <!-- Profile -->
            <div class="flex items-center gap-3">
              <img
                :src="t.avatar"
                :alt="t.name"
                class="w-10 h-10 rounded-full object-cover ring-2 ring-amber-100"
              />
              <div>
                <p class="font-bold text-gray-800 text-sm">{{ t.name }}</p>
                <p class="text-xs text-gray-400">{{ t.school }}</p>
              </div>
              <span
                class="ml-auto text-xs px-2 py-1 bg-amber-50 text-amber-600 rounded-lg font-semibold"
                >{{ t.program }}</span
              >
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== TENTOR SECTION ===== -->
    <section id="tentor" class="py-20 bg-white">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-14">
          <span
            class="inline-block px-4 py-1.5 bg-amber-100 text-amber-600 text-xs font-bold rounded-full uppercase tracking-widest mb-4"
            >Tim Pengajar</span
          >
          <h2 class="text-3xl lg:text-4xl font-black text-gray-900 mb-3">
            Tentor Profesional
          </h2>
          <p class="text-gray-400">
            Belajar bersama tentor terbaik lulusan universitas ternama Indonesia.
          </p>
        </div>

        <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-6">
          <div
            v-for="(mentor, i) in mentors"
            :key="i"
            class="group bg-white rounded-2xl border border-gray-100 overflow-hidden shadow-sm hover:shadow-xl hover:-translate-y-1.5 transition-all duration-300"
          >
            <div
              class="relative h-52 overflow-hidden bg-gradient-to-br from-amber-100 to-orange-100"
            >
              <img
                :src="mentor.avatar"
                :alt="mentor.name"
                class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
              />
              <div
                class="absolute inset-0 bg-gradient-to-t from-black/40 to-transparent"
              ></div>
            </div>
            <div class="p-4">
              <h3 class="font-bold text-gray-800 mb-0.5">{{ mentor.name }}</h3>
              <p class="text-amber-600 text-sm font-semibold mb-2">
                {{ mentor.subject }}
              </p>
              <div class="flex items-center gap-1.5 text-xs text-gray-400 mb-1">
                <Icon name="heroicons:academic-cap" class="w-3.5 h-3.5 text-amber-400" />
                {{ mentor.university }}
              </div>
              <div class="flex items-center gap-1.5 text-xs text-gray-400">
                <Icon name="heroicons:clock" class="w-3.5 h-3.5 text-amber-400" />
                {{ mentor.experience }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== FAQ SECTION ===== -->
    <section id="faq" class="py-20 bg-gray-50">
      <div class="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-14">
          <span
            class="inline-block px-4 py-1.5 bg-amber-100 text-amber-600 text-xs font-bold rounded-full uppercase tracking-widest mb-4"
            >FAQ</span
          >
          <h2 class="text-3xl lg:text-4xl font-black text-gray-900 mb-3">
            Pertanyaan Umum
          </h2>
          <p class="text-gray-400">Jawaban atas pertanyaan yang sering diajukan.</p>
        </div>

        <div class="space-y-3">
          <div
            v-for="(faq, i) in faqs"
            :key="i"
            class="bg-white rounded-2xl border border-gray-100 overflow-hidden shadow-sm"
          >
            <button
              @click="toggleAccordion(i)"
              class="w-full flex items-center justify-between px-6 py-4 text-left hover:bg-amber-50 transition-colors duration-200"
            >
              <span class="font-semibold text-gray-800 pr-4">{{ faq.q }}</span>
              <div
                :class="`w-7 h-7 rounded-lg bg-amber-100 flex items-center justify-center shrink-0 transition-transform duration-300 ${
                  activeAccordion === i ? 'rotate-45 bg-amber-400' : ''
                }`"
              >
                <Icon
                  name="heroicons:plus"
                  :class="`w-4 h-4 ${
                    activeAccordion === i ? 'text-white' : 'text-amber-600'
                  }`"
                />
              </div>
            </button>
            <div v-if="activeAccordion === i" class="px-6 pb-5">
              <p class="text-gray-500 text-sm leading-relaxed">{{ faq.a }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== FINAL CTA ===== -->
    <section
      class="py-24 bg-gradient-to-br from-gray-900 via-gray-800 to-amber-900 relative overflow-hidden"
    >
      <div
        class="absolute inset-0 opacity-20"
        style="
          background-image: radial-gradient(
              ellipse at 20% 50%,
              #f59e0b 0%,
              transparent 60%
            ),
            radial-gradient(ellipse at 80% 50%, #ea580c 0%, transparent 60%);
        "
      ></div>
      <div class="relative max-w-3xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <div
          class="w-16 h-16 rounded-2xl bg-amber-400 flex items-center justify-center mx-auto mb-6 shadow-2xl shadow-amber-400/30"
        >
          <Icon name="heroicons:rocket-launch" class="w-8 h-8 text-white" />
        </div>
        <h2 class="text-3xl lg:text-5xl font-black text-white mb-4 leading-tight">
          Mulai Langkah Menuju<br />
          <span class="text-amber-400">Masa Depan Gemilang</span>
        </h2>
        <p class="text-gray-400 text-lg mb-10 max-w-xl mx-auto">
          Bergabunglah dengan 10.000+ siswa yang telah membuktikan transformasi belajar
          bersama Learning Today.
        </p>
        <div class="flex flex-wrap justify-center gap-4">
          <a
            :href="whatsappUrl"
            target="_blank"
            class="flex items-center gap-2 px-8 py-4 bg-gradient-to-r from-amber-400 to-amber-500 text-white font-bold rounded-2xl shadow-2xl shadow-amber-400/30 hover:shadow-amber-400/50 hover:-translate-y-1 transition-all duration-300 text-lg"
          >
            <Icon name="heroicons:rocket-launch" class="w-5 h-5" />
            Daftar Sekarang
          </a>
          <a
            :href="whatsappUrl"
            target="_blank"
            class="flex items-center gap-2 px-8 py-4 bg-white/10 backdrop-blur text-white font-bold rounded-2xl border border-white/20 hover:bg-white/20 hover:-translate-y-1 transition-all duration-300 text-lg"
          >
            <Icon name="heroicons:phone" class="w-5 h-5" />
            Hubungi Admin
          </a>
        </div>
      </div>
    </section>

    <!-- ===== FOOTER ===== -->
    <footer id="kontak" class="bg-gray-950 text-white pt-16 pb-8">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-10 mb-12">
          <!-- Brand -->
          <div class="lg:col-span-2">
            <div class="flex items-center gap-2 mb-4">
              <div
                class="w-8 h-8 rounded-lg bg-gradient-to-br from-amber-400 to-amber-600 flex items-center justify-center"
              >
                <Icon name="heroicons:academic-cap" class="w-5 h-5 text-white" />
              </div>
              <div>
                <p class="text-sm font-bold text-amber-400 tracking-wide">
                  Learning Today
                </p>
                <p class="text-[10px] text-gray-500 font-medium tracking-widest">
                  LEADING TOMORROW
                </p>
              </div>
            </div>
            <p class="text-gray-400 text-sm leading-relaxed max-w-sm mb-5">
              Bimbingan belajar terpercaya untuk SD, SMP, SMA, SNBT, dan SKD CPNS. Kami
              hadir untuk mewujudkan impian akademikmu.
            </p>
            <div class="flex gap-3">
              <a
                href="#"
                class="w-9 h-9 bg-gray-800 hover:bg-amber-400 rounded-lg flex items-center justify-center transition-colors duration-200"
              >
                <Icon
                  name="heroicons:globe-alt"
                  class="w-4 h-4 text-gray-400 group-hover:text-white"
                />
              </a>
              <a
                href="#"
                class="w-9 h-9 bg-gray-800 hover:bg-amber-400 rounded-lg flex items-center justify-center transition-colors duration-200"
              >
                <Icon
                  name="heroicons:chat-bubble-oval-left"
                  class="w-4 h-4 text-gray-400"
                />
              </a>
              <a
                href="#"
                class="w-9 h-9 bg-gray-800 hover:bg-amber-400 rounded-lg flex items-center justify-center transition-colors duration-200"
              >
                <Icon name="heroicons:video-camera" class="w-4 h-4 text-gray-400" />
              </a>
            </div>
          </div>

          <!-- Links -->
          <div>
            <h4 class="font-bold text-white mb-4 text-sm">Program</h4>
            <ul class="space-y-2">
              <li
                v-for="p in [
                  'Bimbel SD',
                  'Bimbel SMP',
                  'Bimbel SMA',
                  'Persiapan SNBT',
                  'SKD CPNS',
                ]"
                :key="p"
              >
                <a
                  href="#program"
                  class="text-gray-400 hover:text-amber-400 text-sm transition-colors duration-200"
                  >{{ p }}</a
                >
              </li>
            </ul>
          </div>

          <!-- Contact -->
          <div>
            <h4 class="font-bold text-white mb-4 text-sm">Kontak</h4>
            <ul class="space-y-3">
              <li class="flex items-start gap-2.5">
                <Icon
                  name="heroicons:map-pin"
                  class="w-4 h-4 text-amber-400 mt-0.5 shrink-0"
                />
                <span class="text-gray-400 text-sm"
                  >Jl. Pendidikan No. 123, Purwokerto, Jawa Tengah</span
                >
              </li>
              <li class="flex items-center gap-2.5">
                <Icon name="heroicons:phone" class="w-4 h-4 text-amber-400 shrink-0" />
                <a
                  :href="whatsappUrl"
                  target="_blank"
                  class="text-gray-400 hover:text-amber-400 text-sm transition-colors"
                  >+62 812 3456 7890</a
                >
              </li>
              <li class="flex items-center gap-2.5">
                <Icon name="heroicons:envelope" class="w-4 h-4 text-amber-400 shrink-0" />
                <a
                  href="mailto:info@learningtoday.id"
                  class="text-gray-400 hover:text-amber-400 text-sm transition-colors"
                  >info@learningtoday.id</a
                >
              </li>
            </ul>
          </div>
        </div>

        <!-- Bottom bar -->
        <div
          class="border-t border-gray-800 pt-6 flex flex-col sm:flex-row items-center justify-between gap-3"
        >
          <p class="text-gray-500 text-xs">
            &copy; 2026 Learning Today Leading Tomorrow. All rights reserved.
          </p>
          <p class="text-gray-600 text-xs">Designed with care for every learner.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
html {
  scroll-behavior: smooth;
}
</style>
