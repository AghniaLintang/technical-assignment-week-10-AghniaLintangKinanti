## Code

	import RPi.GPIO as GPIO
	from mfrc522 import SimpleMFRC522
	from check_db import *
	from payload import *
 
	reader = SimpleMFRC522()

 	def rfid_read():
		id, text = reader.read()
		print(id)
		#print(text)
	 	print(type(id))
		result, status=checkid(id)
	
		if status == True:
			send_ubidots(result["id_card"], result["name"], result["kelas"])
			print("kartu terdaftar")
			results = "berhasil"
			return results;
		else:
			print("kartu tidak terdaftar")
			results = "gagal"
			return results;
		 
## Hasil Dashboard

![WhatsApp Image 2023-09-03 at 11 33 49 AM](https://github.com/AghniaLintang/technical-assignment-week-10-AghniaLintangKinanti/assets/143922162/99e221c0-3bfc-467b-9d5b-cc4ef26bc373)
