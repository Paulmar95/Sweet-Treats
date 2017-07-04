---MAIN---
<html>
<head><title>Marinescu Paul - Gabriel</title></head>
<body>
<h1> Formular date:</h1>
<form name="f" action="adaugare.php" method="post" style="border:2px solid black;border-radius:8px;width:70%;margin-left:15%;margin-right:15%;box-shadow:2px 2px 2px 2px;padding:1%;"></br>
	nume :<input type="text" name="t1" size="30" /></br>
	prenume :<input type="text" name="t2" size="30" /></br>
	varsta :<input type="text" name="t3" size="2" /></br>
	telefon :<input type="text" name="t4" size="10" /></br>
	adresa :<input type="text" name="t5" size="30" /></br>
	email :<input type="text" name="t6" size="30" />
	</br>
	<input type="submit" value="test">
</form>
</body>
</html>
 
 ---adaugare.php---
 
 <?php

$a=strtoupper($_POST["t1"]);
$b=strtoupper($_POST["t2"]);
$c=$_POST["t3"];
$d=$_POST["t4"];
$e=strtoupper($_POST["t5"]);
$f=$_POST["t6"];
//preia date si aplica conversia

mysql_connect("localhost","root","") or die ("Nu merge");
mysql_select_db("zi_2015") or die ('Eroare la baza de date!');
//creez insert

$x="insert into Paul set 
nume='".$a."',prenume='".$b."',varsta='".$c."',tel='".$d."',adresa='".$e."',email='".$f."';";

$y=mysql_query($x);
if($x)
{	
	echo "<br /> Datele s-au introdus corect!";
}
else
{
	echo "Eroare la adaugare!";
}
//Afisare
$q="select * from Paul;";
$rez=mysql_query($q);
echo "<table border='1' align='center'>";
echo "<tr><td>Nume</td><td>Prenume</td><td>Varsta</td><td>Telefon</td><td>Adresa</td></tr>";
$sem=0;
while($row=mysql_fetch_array($rez)){
if($sem==0)
{echo "<tr bgcolor='#992233'>";
echo "<td>" . $row['nume'] . "</td>";
echo "<td>" . $row['prenume'] . "</td>";
echo "<td>" . $row['varsta'] . "</td>";
echo "<td>" . $row['tel'] . "</td>";
echo "<td>" . $row['adresa'] . "</td>";
echo "</tr>";
$sem=1;
}
else
{echo "<tr bgcolor='9568473'>";
echo "<td>" . $row['nume'] . "</td>";
echo "<td>" . $row['prenume'] . "</td>";
echo "<td>" . $row['varsta'] . "</td>";
echo "<td>" . $row['tel'] . "</td>";
echo "<td>" . $row['adresa'] . "</td>";
echo "</tr>";
$sem=0;
}
}
echo "</table>";
//sfarsit afisare



echo "<a href='introducere.html'>Back</a>";
echo "<br /><b>Continuati?</b>
		<form action='rasp.php' method='post'>
		<input type='submit' value='Alegeti?' /> <br />
		<input type='radio' name='r' value='da' /> da
		<input type='radio' name='r' value='nu' /> nu
		</form>";
?>

--- rasp.php ---

<?php
mysql_connect("localhost","root","") or die ("Nu merge");
mysql_select_db("zi_2015") or die ('Eroare la baza de date!');
//Afisare
$q="select * from Paul;";
$rez=mysql_query($q);
echo "<table border='1' align='center'>";
echo "<tr><td>Nume</td><td>Prenume</td><td>Varsta</td><td>Telefon</td><td>Adresa</td></tr>";
$sem=0;
while($row=mysql_fetch_array($rez)){
if($sem==0)
{echo "<tr bgcolor='#992233'>";
echo "<td>" . $row['nume'] . "</td>";
echo "<td>" . $row['prenume'] . "</td>";
echo "<td>" . $row['varsta'] . "</td>";
echo "<td>" . $row['tel'] . "</td>";
echo "<td>" . $row['adresa'] . "</td>";
echo "</tr>";
$sem=1;
}
else
{echo "<tr bgcolor='9568473'>";
echo "<td>" . $row['nume'] . "</td>";
echo "<td>" . $row['prenume'] . "</td>";
echo "<td>" . $row['varsta'] . "</td>";
echo "<td>" . $row['tel'] . "</td>";
echo "<td>" . $row['adresa'] . "</td>";
echo "</tr>";
$sem=0;
}
}
echo "</table>";
//sfarsit afisare
echo "<a href='introducere.html'>Back</a>";

?>
<?php
$rasp=$_POST["r"];
if($rasp=="da")
	include "introducere.html";
else
	echo "</br>revenire la meniul principal";

	?>
