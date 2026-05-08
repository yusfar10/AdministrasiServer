MIgration Standalone Folder to Instance AWS Ec2

Upload standalone.zip via SFTP (Filezilla)
Konek Open SSH -> ssh -i nama_file.pem ubuntu@[IP_ADDRESS] / PuTTY
Patching OS -> sudo apt update && sudo apt upgrade
Install tools unzip -> sudo apt install unzip -y
cd /var/www/html
![alt text](image.png)
extract standalone.zip -> unzip standalone.zip
cek hasil Extract -> ls -R / dari filezilla
Install Interpreter untuk Apps base node JS sesuai dokumentasi resmi https://nodejs.org/en/download
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash
. "$HOME/.nvm/nvm.sh"
nvm install 24
Verify the Node.js version:
node -v
![alt text](image-1.png)
![alt text](image-2.png)
Export - Import DB - Start DBMS (Laragon, xampp, dll) - Export db_compro - hapus ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci - Login usercompro - use dbcompro_NIM; - Copy Paste Query ctrl+A file sql export -> Klik Kanan di terminal AWS -show tables;
![alt text](image-3.png)
kita sesuaikan file .env
cd standalone
sudo nano .env
sesuiakn isi .env : DB_HOST=[IP_ADDRESS] DB_USER=usercompro_NIM DB_PASS=[PASSWORD] DB_NAME=dbcompro_NIM
ctrl+x -> y -> Enter
pm2 start server.js
tambah / buka port 3000 di AWS Security Groups
![alt text](image-4.png)
Akses http://[IP_ADDRESS]:3000
akses BE http://[IP_ADDRESS]:3000/admin edit berita ke 2 tambahkan nama - nim