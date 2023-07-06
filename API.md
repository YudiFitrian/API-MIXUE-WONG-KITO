API 
<?php
require("koneksi.php");

if($_SERVER["REQUEST_METHOD"] == "POST"){
    $nama = $_POST["nama"];
    $lokasi = $_POST["lokasi"];
    $deskripsi = $_POST["deskripsi"];
    $urlmap = $_POST["urlmap"];
    
    $perintah = "INSERT INTO tbl_mixuewongkito (nama, lokasi, deskripsi, urlmap) VALUES ('$nama', '$lokasi', '$deskripsi', '$urlmap')";
    $eksekusi = mysqli_query($konek, $perintah);
    $cek = mysqli_affected_rows($konek);
    
    if($cek>0){
        $response["kode"] = 1;
        $response["pesan"] = "Tambah Data Sukses!";
    }
    else{
        $response["kode"] = 0;
        $response["pesan"] = "Tambah Data Gagal!";
    }
}
else{
    $response["kode"] = 0;
    $response["pesan"] = "Tidak ada Post Data";
}

echo json_encode($response);
mysqli_close($konek);


<?php
require("koneksi.php");

if($_SERVER["REQUEST_METHOD"] == "POST"){
    $id = $_POST["id"];
    
    $perintah = "DELETE FROM tbl_mixuewongkito WHERE id='$id'";
    $eksekusi = mysqli_query($konek, $perintah);
    $cek = mysqli_affected_rows($konek);
    
    if($cek>0){
        $response["kode"] = 1;
        $response["pesan"] = "Hapus Data Sukses!";
    }
    else{
        $response["kode"] = 0;
        $response["pesan"] = "Hapus Data Gagal!";
    }
}
else{
    $response["kode"] = 0;
    $response["pesan"] = "Tidak ada Post Data";
}

echo json_encode($response);
mysqli_close($konek);

<?php
    $db_host = "localhost";
    $db_name = "id20921000_dbmixuewongkito";
    $db_user = "id20921000_usermixuewongkito";
    $db_pass = "Mixuewongkito01*";
    
    $konek = mysqli_connect($db_host, $db_user, $db_pass, $db_name) or die("Database Tidak Terhubung");


<?php
    require("koneksi.php");
    
    $perintah = "SELECT * FROM tbl_mixuewongkito";
    $eksekusi = mysqli_query($konek, $perintah);
    
    $cek = mysqli_affected_rows($konek);
    
    if($cek>0){
        $response["kode"] = 1;
        $response["pesan"] = "Data Tersedia";
        $response["data"] = array();
        
        while($ambil = mysqli_fetch_object($eksekusi)){
            $temp["id"] = $ambil->id;
            $temp["nama"] = $ambil->nama;
            $temp["lokasi"] = $ambil->lokasi;
            $temp["deskripsi"] = $ambil ->deskripsi;
            $temp["urlmap"] = $ambil ->urlmap;
            
            array_push($response["data"], $temp);
        }
    }
    else{
        $response["kode"] = 0;
        $response["pesan"] = "Data Tidak Tersedia";
    }
    
    echo json_encode($response);
    mysqli_close($konek);

<?php
require("koneksi.php");

if($_SERVER["REQUEST_METHOD"] == "POST"){
    $id = $_POST["id"];
    $nama = $_POST["nama"];
    $lokasi = $_POST["lokasi"];
    $deskripsi = $_POST["deskripsi"];
    $urlmap = $_POST["urlmap"];
    
    $perintah = "UPDATE tbl_mixuewongkito SET nama='$nama', lokasi='$lokasi', deskripsi='$deskripsi', urlmap='urlmap' WHERE id='$id'";
    $eksekusi = mysqli_query($konek, $perintah);
    $cek = mysqli_affected_rows($konek);
    
    if($cek>0){
        $response["kode"] = 1;
        $response["pesan"] = "Ubah Data Sukses!";
    }
    else{
        $response["kode"] = 0;
        $response["pesan"] = "Ubah Data Gagal!";
    }
}
else{
    $response["kode"] = 0;
    $response["pesan"] = "Tidak ada Post Data";
}

echo json_encode($response);
mysqli_close($konek);