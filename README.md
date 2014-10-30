<?php
ob_start();
include('config.php');
$id = $_POST['no'];
$KodeBarang=$_POST['KodeBarang'];
$JenisBarang=$_POST['JenisBarang'];
$JumlahAset=$_POST['JumlahAset'];
$MerkType=$_POST['MerkType'];
$RuangLokasi=$_POST['RuangLokasi'];
$Bahan=$_POST['Bahan'];
$CaraPerolehan=$_POST['CaraPerolehan'];
$TahunPerolehan=$_POST['TahunPerolehan'];
$Satuan=$_POST['Satuan'];
$KeadaanBarang=$_POST['KeadaanBarang'];
$HargaBarang=$_POST['HargaBarang'];
if($JumlahAset==0){ 
	$TotalHarga=$HargaBarang;
	}
	else{
$TotalHarga==$JumlahAset*$HargaBarang;
}
$Keterangan = $_POST['Keterangan'];

$query = mysql_query("update inventaris set KodeBarang='$KodeBarang', 
JenisBarang='$JenisBarang', JumlahAset='$JumlahAset', MerkType='$MerkType', RuangLokasi='$RuangLokasi', Bahan='$Bahan',
CaraPerolehan='$CaraPerolehan',TahunPerolehan='$TahunPerolehan',Satuan='$Satuan',KeadaanBarang='$KeadaanBarang',HargaBarang='$HargaBarang',
TotalHarga='$TotalHarga',Keterangan ='$Keterangan';
where no='$id'") or die(mysql_error());

if ($query) {
	header('location:view.php?message=success');
}
ob_end_flush();
?>
