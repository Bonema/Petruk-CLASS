#include <iostream>
//#include <conio.h>
#include <iomanip>
#include <windows.h>
using namespace std;

class room
{
    public:
      int data;
      room* next;
};

room* head;
room* tail;
room* curr;
room* entry;
room* del;

void isi()
{
      head = NULL;
      tail = NULL;
}

void input(int dt)
{
      entry = (room* )malloc(sizeof(room));
      entry->data = dt;
      entry->next = NULL;
      if(head==NULL)
      {
            head = entry;
            tail = head;
      }
      else
      {
            tail->next = entry;
            tail = entry;
      }
}

void hapus()
{
      int simpan;
      if(head==NULL)
      {
            cout<<"\nlinked list kosong, penghapusan tidak bisa dilakukan"<<endl;
      }
      else
      {
            simpan  = head ->data;
            del = head;
            head = head->next;
            delete del;

            cout<<"\ndata yang dihapus adalah "<<simpan<<endl;
      }

}

void cetak()
{
      curr = head;
      if(head == NULL)
            cout<<"\ntidak ada data dalam linked list"<<endl;
      else
      {
            cout<<"\nData yang ada dalam linked list adalah"<<endl;
            cout<<setw(6);
            while(curr!=NULL)
            {
                  cout<<curr->data<<"->";
                  curr = curr->next;
            }
cout<<"NULL";
            cout<<endl;
      }
}

void menu()
{
      char pilih, ulang;
      int data;

      do
      {
      system("cls");
      cout<<"================================"<<endl;
      cout<<"Menu : "<<endl;
      cout<<"1. Input "<<endl;
      cout<<"2. Hapus "<<endl;
      cout<<"3. Cetak "<<endl;
      cout<<"4. Exit"<<endl;
      cout<<"Masukkan pilihan Anda : ";
      cin>>pilih;

      switch(pilih)
      {
      case '1' :
            cout<<"\nMasukkan data : ";
            cin>>data;
            input(data);
            break;
      case '2' :
            hapus();
            break;
      case '3' :
            cetak();
            break;
      case '4' :
            exit(0);
            break;
      default :
            cout<<"\nPilih ulang"<<endl;
      }
      cout<<"\nKembali ke menu?(y/n)";
      cin>>ulang;
      }while(ulang=='y' || ulang=='Y');
}


int main()
{

      isi();
      menu();

      return EXIT_SUCCESS;
}
