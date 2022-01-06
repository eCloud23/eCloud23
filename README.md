/*Topik : Pemesanan Makanan
Kelompok 1 : 
Andy Sudriyanto (201724003)
Jonatan Hutahean (201724013)
Reyhan Dwi Saputra (201724029)*/

#include<iostream>
#include<stdlib.h>
#include<string.h>
#include<conio.h>
#include <stdio.h>
#include <windows.h>
#include <iomanip>

using namespace std;
void gotoxy(int x, int y){
	COORD coord;
	coord.X=x;
	coord.Y = y;
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),coord);
}

int main () {
	
	//KAMUS DATA
	char pilihan,pilihan1,password[15],nama[20],lagi,status[20];
	string jenis[10];
	int a,nomeja,menu,porsi[10],kode,harga[10];
	float totalharga,total,uang,kembalian;
		
	//MENU UTAMA
	menuutama:
	system("cls");
	printf("=========================================================\n");
	printf("		  RUMAH MAKAN APAYAH\n");
	printf("     Jl. LUAR ANGKASA RAYA NO.27 Galaxy, Ciwaruga\n");
	printf("=========================================================\n");
	printf("\n---------------------------------------------------------\n");
	printf("		    MENU PILIHAN\n");	
	printf("---------------------------------------------------------\n");
	printf("\n\t1.Pegawai\n");
	printf("\n\t2.Pembeli\n");
	printf("\n\t3.Status Pemesanan\n");
	printf("\n---------------------------------------------------------\n");
	printf("=========================================================\n");
	printf("\t\nMasukan Pilihan Anda :");
	scanf("%d",&pilihan);
	system("cls");
	
	//USER
	if(pilihan==1){
		printf("\n=========================================================\n");
		printf("			Pegawai\n");
		printf("=========================================================\n");
		printf("\n\tPassword  :");
		scanf("%s",&password);
		if(strcmp(password,"678")==0) {
			printf("\n---------------------------------------------------------\n");
			printf("\n\tBerhasil Masuk & Selamat Bekerja\n");
			printf("\n---------------------------------------------------------\n");
			printf("=========================================================\n");
			fflush(stdin);
			while(!kbhit());
			pilihan=1;
			system ("cls");
			
			//FITUR PEGAWAI
			menupilihan:
			system("cls");
			printf("\n---------------------------------------------------------\n");
			printf("		    MENU PILIHAN\n");	
			printf("---------------------------------------------------------\n");
			printf("\n\t1.Menginput Pembelian\n");
			printf("\n\t2.Menginput Status Pemesanan\n");
			printf("\nMasukan Pilihan Anda :");
			scanf("%d",&pilihan1);
			system("cls");
			
			switch (pilihan1){
				menupegawai :
				system("cls");
				case 1 : {
						printf("=========================================================\n");
						printf("		MENU MAKANAN DAN MINUMAN\n");
						printf("=========================================================\n");
						printf("---------------------------------------------------------\n");
						printf("\tDaftar Menu                     Harga\n");
						printf("\t1. Soto Ayam + Nasi     	Rp 25.000\n");
						printf("\t2. Soto Betawi + Nasi		Rp 30.000\n");
						printf("\t3. Ayam Goreng + Nasi		Rp 17.000\n");
						printf("\t4. Nasi Putih	        	Rp 5.000\n");
						printf("\t5. Jus Jeruk            	Rp 10.000\n");
						printf("\t6. Es Teh Manis         	Rp 10.000\n");		
						printf("---------------------------------------------------------\n");
						cout<<"\nNomor Meja : ";cin>>nomeja;
						cout<<"\nNama Pemesan : ";cin>>nama;
						cout<<"\nBanyak Pesanan : ";cin>>menu;
    					
						
						//PROSES PENGINPUTAN
						for(a=1;a<=menu;++a) {
							cout<<"\nPesanan Ke-"<<a<<endl;
							cout<<"Masukkan Nomor Makanan/Minuman : ";cin>>kode;
                			cout<<"Jumlah Pesan                   : ";cin>>porsi[a];
                			
			                if (kode==1){
			                	cout<<"Menu Yang Dipilih  	       : Soto Ayam + Nasi\n";
			            		jenis[a]="Soto Ayan + Nasi";
			                	harga[a]=25000;}
			 
			                else if (kode==2){
			                	cout<<"Menu Yang Dipilih  	       : Soto Betawi + Nasi\n";
			                    jenis[a]="Soto Betawi + Nasi";
			                    harga[a]=30000;}
			 
			                else if (kode==3){
			                	cout<<"Menu Yang Dipilih  	       : Ayam Goreng + Nasi\n";
			                    jenis[a]="Ayam Goreng + Nasi";
			                    harga[a]=17000;}
			 
			                else if (kode==4){
			                	cout<<"Menu Yang Dipilih  	       : Nasi Putih\n";
			                    jenis[a]="Nasi putih";
			                    harga[a]=5000;}
			 
			                else if (kode==5){
			                	cout<<"Menu Yang Dipilih  	       : Jus Jeruk\n";
			                    jenis[a]="Jus Jeruk";
			                    harga[a]=10000;}
			 
			                else if (kode==6){
			                	cout<<"Menu Yang Dipilih  	       : Es Teh Manis\n";
			                    jenis[a]="Es Teh Manis";
			                    harga[a]=10000;}
			 
			                else {cout<<"Salah!!,Input Kode Lagi!!"<<endl;
			                     goto menupegawai;}
						}
						
						//PROSES PEMBAYARAN
						system("cls");
            			printf("\t\t\tRUMAH MAKAN APAYAH\n");
            			printf("\t\tJL. LUAR ANGKASA NO.27 Galaxy, Ciwaruga\n");
            			printf("=======================================================================\n");
            			cout<<"Nomor Meja :"<<nomeja<<endl;
            			cout<<"Nama Pemesan : "<<nama<<endl;
            			printf("=======================================================================\n");
            			printf("No.       Nama          Harga        Jumlah      Subtotal             \n");
            			printf("          Makanan       Makanan      Pesan                            \n");
            			printf("=======================================================================\n");
						
						totalharga=0;
            			for(a=1;a<=menu;++a) {
                			gotoxy(1,a+10);  cout<<a;
                			gotoxy(5,a+10);  cout<<jenis[a];
                			gotoxy(25,a+10); cout<<harga[a];
                			gotoxy(39,a+10); cout<<porsi[a];
                			total=porsi[a]*harga[a];
                			gotoxy(51,a+10); cout<<total;
                			cout<<endl;
                			totalharga=totalharga+total;
               			 }
           				printf("\n=======================================================================\n");
            			cout<<"                                Total Bayar     :Rp. "<<totalharga<<endl;
            			cout<<"                                Uang Bayar      :Rp. ";cin>>uang;
            			kembalian=uang-totalharga;
            			cout<<"                                Uang Kembali    :Rp. "<<kembalian<<endl;
            			printf("=======================================================================\n ");
            			printf("\tTerimakasih atas kunjungan anda di RUMAH MAKAN APAYAH	                \n");
            			printf("======================================================================= \n");	
						cout<<"Apakah Ingin Memesan Lagi? [Y/T]:\n"; cin>>lagi;
        				if(lagi=='T'||lagi=='t')
            			goto menupilihan;
            			else (lagi=='Y'||lagi=='y');
            			goto menupegawai;		
					break;
				}
				case 2: {
					printf("===============================================================\n");
					printf("		       STATUS PEMESANAN\n");
					printf("===============================================================\n");
					printf("---------------------------------------------------------------\n");
					printf("\tNomer Meja         Nama Pemesan       Status");
					
					printf("\n\n---------------------------------------------------------------\n");
					cout<<"\nJika ingin kembali ketik [Y]:"; cin>>lagi;
        			if(lagi=='Y'||lagi=='y')
            		goto menuutama; 
					break;
				}
			}
	   	}
		else {
			printf("\n---------------------------------------------------------\n");
			printf("\n\tPassword salah !");
			printf("\n\n---------------------------------------------------------\n");
			fflush(stdin);
			while(!kbhit());
			pilihan=0;
		}
		
	}
	menupembeli:
	system("cls");
	if(pilihan==2){
		printf("=========================================================\n");
		printf("		MENU MAKANAN DAN MINUMAN\n");
		printf("=========================================================\n");
		printf("---------------------------------------------------------\n");
		printf("\tDaftar Menu                     Harga\n");
		printf("\t1. Soto Ayam + Nasi     	Rp 25.000\n");
		printf("\t2. Soto Betawi + Nasi		Rp 30.000\n");
		printf("\t3. Ayam Goreng + Nasi		Rp 17.000\n");
		printf("\t4. Nasi Putih	        	Rp 5.000\n");
		printf("\t5. Jus Jeruk            	Rp 10.000\n");
		printf("\t6. Es Teh Manis         	Rp 10.000\n");			
		printf("---------------------------------------------------------\n");	
		
		cout<<"Apakah Ingin Memesan Lagi? [Y/T]:"; cin>>lagi;
        	if(lagi=='T'||lagi=='t')
            goto menuutama;
            else (lagi=='Y'||lagi=='y');
            goto menupembeli;
	}
	
	if(pilihan==3) {
		printf("===============================================================\n");
		printf("		       STATUS PEMESANAN\n");
		printf("===============================================================\n");
		printf("---------------------------------------------------------------\n");
		printf("\tNomer Meja        Nama Pemesan        Status");
		
		printf("\n\n---------------------------------------------------------------\n");
		cout<<"\nJika ingin kembali ketik [Y]:"; cin>>lagi;
        	if(lagi=='Y'||lagi=='y')
            goto menuutama; 
	}
	
	
	
	
}
