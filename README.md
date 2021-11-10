# Tugas Kelas - Week 9 (18 Oktober 2021)
Oct 18,  2021


      #include <stdio.h>

      typedef struct Person{
          char *namaDepan;
          char *namaBelakang;
          unsigned int umur;
          char jeniskelamin;
          char *makananDisuka;
          struct Person *father;
          struct Person *mother;
      } Person;

      typedef enum makananFavorit{
          SateKambing=1,
          SateAyam,
          GulaiKambing,
          SupIkan,
          AyamGoreng
      } Makanan;

      int main(){
          char *namaMakanan[] = {"" "Sate Kambing", "Sate Ayam", "Gulai Kambing", "Sup Ikan", "Ayam Goreng"};
          Makanan makananDisuka = 4;

          Person human, father, mother;
          Person dataperson[3] = {
              {"Tatang", "Suryana", 17, 'L', namaMakanan[makananDisuka], &father, &mother},{"Dadang", "Malinkundang", 43, 'L'},{"Suryani", "Saridewi", 34, 'P'}
          };


          human = dataperson[0];
          father = dataperson[1];
          mother = dataperson[2];

          printf("Nama : %s %s \nUmur %d tahun\n", human.namaDepan, human.namaBelakang, human.umur);
          printf("Jenis Kelamin : %c\n", human.jeniskelamin);
          printf("Makanan Kesukaan : %s\n", human.makananDisuka);
          printf("Nama Ayah : %s %s\n", human.father->namaDepan, human.father->namaBelakang);
          printf("Nama Ibu : %s %s\n", human.mother->namaDepan, human.mother->namaBelakang);
          printf("Bit dari usia ayah: \n");
          displayBits(human.father->umur);
          printf("Bit dari usia ibu: \n");
          displayBits(human.mother->umur);
          printf("Usia ayah AND usia ibu: \n");
          displayBits(human.father->umur & human.mother->umur);
          printf("Usia ayah OR usia ibu: \n");
          displayBits(human.father->umur | human.mother->umur);
          printf("Usia ayah XOR usia ibu: \n");
          displayBits(human.father->umur ^ human.mother->umur);
      }

      void displayBits(unsigned int value)
      {
          unsigned int displayMask = 1 << 31;
          printf("%10u = ", value);
          for (unsigned int c = 1; c <= 32; ++c)
          {
              putchar(value & displayMask ? '1' : '0');
              value <<= 1;
              if (c % 8 == 0)
              {
                  putchar(' ');
              }
          }
          putchar('\n');
      }
