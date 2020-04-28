========== Server ==========
hidupkan server mongodb = sudo service mongodb start
matikan server mongodb  = sudo service mongodb stop
Menyalakan ulang server mongodb = sudo service mongodb restart
Melihat status server mongodb = sudo service mongodb status
note : Gunakan tombol q untuk keluar dari status
============================

========== Memulai ==========
aktifkan dan masuk = mongo
=============================

========== Memulai ==========
membuat database = use namadatabase
melihat database yang aktif = db
lihat db and storage = show dbs
=============================

========== membuat collection/table ==========
db.namatable.insert({"name" : "sammi", "age" : 20})
lihat collection yang telah dibuat = show collections
hapus database = db.dropDatabase()
hapus collection/table = db.namacollection.drop
==============================================

==============================================
buat database = use contohDb
buat coolection = db.createCollection('collectionPertama')
lihat = show collections

cara kedua membuat collection : db.namaTable.insert({"name" : "sammi", "age" : 20})
==============================================

============ insert data =====================
buat db     = use namaDb
tambah data = db.namaCollection.insert({"username" : "sammidevmisalnya", "password" : "sammidev"})
tampilkan json = db.namaCollection.find()
lebih rapi     = db.namadata.find().pretty()

buat data banyak, misalnya : 

{
	"username" : "sammidev",
	"password" : "hello"
},
{
	"username" : "sammidev",
	"password" : "hello"
},
{
	"username" : "sammidev",
	"password" : "hello"
},
{
	"username" : "sammidev",
	"password" : "hello"
},
{
	"username" : "sammidev",
	"password" : "hello"
}


cara masukan = db.namadata.insert([tekan shift+enter untuk membuat bari baru, kemudian paste yg banyak tadi, shif + enter lagi untuk membuat kurung tutup array dan biasa])

==================================================================================================


========== UPDATE DATA ==========
db.namaCollections.update
(
	{
		"firstname" : "nelson"
	},
	{
		"firstname" : "Sam",
		"lastname"  : "dev",
		"gender" 	: "male"
	}
)


CARA LAIN : 

db.namaColl.update({name : "sam"}, {$set:{name : "samUpdate", kelas : "xii", gender : "male"}})



multi update : 
db.namaCollection.update({name : "sam"}, {$set : {name : "sammidev",  gender : "male"}}, {multi:true})

======= fungsi save()
db.namacoll.save({copy data json paste kesini}) // untuk menggunakan ini harus pake _id dan kasih tanda koma setelah penutup kurung id, kemudian isi data2 lain untuk di update misal name,class,and others

jika misal id yg dimasukkan tidak ada, maka akan dibuat sebuah document baru,mirip fungsi ifPresent() pada collection di bahasa pemrograman

==============================================

======= Remove Data ========
db.studentdata.remove({firstname : "Sam"})

remove umur 15 tapi hanya satu orang:
db.namaCollect.remove({umur : 15}, 1) 
============================

====== Hapus semua data dalam collection ======
db.namaCollections.remove({})
===============================================

======== Drop =================================
Menghapus koleksi : db.<koleksi>.drop();
Menghapus database: db.dropDatabase();
===============================================

===== FindData / operator=====
db.namaCollections.find({name : "sam",lastname : "dev"});

OR : 

db.namaCollection({$or:[{name : "sam"}, {lastname : "dev"}]});

IN : 

db.namaCollections({umur : {$in: [16,17,18]}}).pretty()

$it

kurang dari value tertentu
misa, umur < 16

db.namaCollection.find({umur : {$it : 16}}).pretty()

$gt

umur > 16
db.namaColl.find({umur : {$gt : 16}}).pretty()

$ne
umur != 16
db.namColl.find({umur : {$ne : 16}}).pretty()
============================================

============================================
=========== projection =======
find beberapa field saja
misal id dan nama saja : 
db.siswa.find({},{nama:true})


nama saja : 1 = true, 0 = false
db.siswa.find({}, {name:1, _id:0})



=========== Limit ==========================
limitasi berapa banyak doc yg akan ditampilkan
misal 5 doc: 
db.siswa.find({},{nama : 1, _id:0}).limit(5)


===== skip ======
skip bebrapa doc
lewati 5 buah : 
db.siswa.find().skip(5)

==== sort ======
mengurutkan dokumen berdasarkan nama  lihat : argument terakhir, ascending
db.siswa.find({}.{nama : 1, _id:0}).sort({nama : 1})

descending
db.siswa.find({}.{nama : 1, _id:0}).sort({nama : -1})