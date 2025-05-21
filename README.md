#include <iostream>
#include <cstdlib>
#include <ctime>
#include <string>
#include <fstream>
#include <limits>
#include <vector>

using namespace std;

const char alphaNum[] = "0123456789!@#$%^&*_abcdefghijklmnopqrstuvwxyzn";
const int panjang_string = sizeof(alphaNum) - 1;

struct MyToDo {
    int id;
    string judul;
    string keterangan;
};

int main() {
    srand(time(0)); // inisialisasi generator bilangan acak

    vector<MyToDo> daftarTugas;

    int pilihan;
    do {
        cout << "Menu:" << endl;
        cout << "1. Tambah Tugas" << endl;
        cout << "2. Lihat Tugas" << endl;
        cout << "3. Ubah Tugas" << endl;
        cout << "4. Hapus Tugas" << endl;
        cout << "5. Keluar" << endl;
        cout << "Masukkan pilihan: ";
        cin >> pilihan;

        switch (pilihan) {
            case 1: {
                MyToDo tugas;
                cout << "Masukkan judul tugas: ";
                cin.ignore();
                getline(cin, tugas.judul);
                cout << "Masukkan keterangan tugas: ";
                getline(cin, tugas.keterangan);
                daftarTugas.push_back(tugas);
                break;
            }
            case 2: {
                for (int i = 0; i < daftarTugas.size(); i++) {
                    cout << "Tugas " << i + 1 << ":" << endl;
                    cout << "Judul: " << daftarTugas[i].judul << endl;
                    cout << "Keterangan: " << daftarTugas[i].keterangan << endl;
                }
                break;
            }
            case 3: {
                int index;
                cout << "Masukkan nomor tugas yang ingin diubah: ";
                cin >> index;
                cin.ignore();
                if (index > 0 && index <= daftarTugas.size()) {
                    cout << "Masukkan judul tugas baru: ";
                    getline(cin, daftarTugas[index - 1].judul);
                    cout << "Masukkan keterangan tugas baru: ";
                    getline(cin, daftarTugas[index - 1].keterangan);
                } else {
                    cout << "Nomor tugas tidak valid!" << endl;
                }
                break;
            }
            case 4: {
                int index;
                cout << "Masukkan nomor tugas yang ingin dihapus: ";
                cin >> index;
                cin.ignore();
                if (index > 0 && index <= daftarTugas.size()) {
                    daftarTugas.erase(daftarTugas.begin() + index - 1);
                } else {
                    cout << "Nomor tugas tidak valid!" << endl;
                }
                break;
            }
            case 5: {
                cout << "Keluar dari program..." << endl;
                break;
            }
            default: {
                cout << "Pilihan tidak valid!" << endl;
                break;
            }
        }
    } while (pilihan != 5);

    return 0;
}
