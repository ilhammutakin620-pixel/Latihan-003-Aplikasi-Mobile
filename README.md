PARKIR LANGGANAN

Muhammad Ilham muttaqim - 1124160073

- BR-01: Member bulanan mendapatkan parkir gratis
- BR-02: Non-member dikenakan tarif parkir secara progresif berdasarkan durasi parkir.
- BR-03: Tiket parkir yang hilang dikenakan denda sebesar Rp20.000.
- BR-04: Status pengguna harus ditentukan sebagai member atau non-member sebelum perhitungan tarif dilakukan.
- BR-05: Durasi parkir dihitung berdasarkan waktu masuk dan waktu keluar.
```dart
enum StatusMember {
  member,
  nonMember
}

enum StatusTiket {
  ada,
  hilang
}

void main() {
  StatusMember statusMember = StatusMember.nonMember;
  StatusTiket statusTiket = StatusTiket.ada;
  int durasiMenit = 150;

  int durasiJam = hitungDurasiJam(durasiMenit);
  int tarifParkir = hitungTarifParkir(statusMember, durasiJam);
  int denda = hitungDenda(statusTiket);

  int totalBayar = tarifParkir + denda;

  print("=== PARKIR LANGGANAN ===");
  print("Status Member : ${statusMember.name}");
  print("Durasi        : $durasiMenit menit");
  print("Lama Parkir   : $durasiJam jam");
  print("Tarif Parkir  : Rp$tarifParkir");
  print("Denda         : Rp$denda");
  print("Total Bayar   : Rp$totalBayar");
}

int hitungDurasiJam(int durasiMenit) {
  int jam = durasiMenit ~/ 60;

  if (durasiMenit % 60 != 0) {
    jam++;
  }

  if (jam < 1) {
    jam = 1;
  }

  return jam;
}

int hitungTarifParkir(StatusMember statusMember, int durasiJam) {
  if (statusMember == StatusMember.member) {
    return 0;
  }

  int tarif = 5000;

  if (durasiJam > 1) {
    tarif += (durasiJam - 1) * 3000;
  }

  return tarif;
}

int hitungDenda(StatusTiket statusTiket) {
  if (statusTiket == StatusTiket.hilang) {
    return 20000;
  }
```

  return 0;
}
