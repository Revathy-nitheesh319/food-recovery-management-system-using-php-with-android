# food-recovery-management-system-using-php-with-android
Abstract:
Everyday people used to waste foods. In order to reduce that food wastage problem through web application . In this project we deal with balance food of hotel.Hotel add their details. So they can login and enter their food details in site. Then a simple notification is given to the carrier . After seeing the notification the carrier among that location can login & can gather the details of the hotel.
       Admin have the entire control of the system.Admin can approve or reject the verified hotels.Admin can add the details of food inspector,carriers,and orphanages or old-age homes or poor people.Admin can assign work to food inspector and view complaints from food inspector and reply for that.Admin can add common notifications.
The food inspector can hold an account in this system and do the works assigned by admin.Food inspector verify the registered hotels and do some unexpected checking allotted by admin.Food inspector submit the monthly reports of their works.They give information to admin about the hotel quality and can also send complaint to admin and should suspend the hotel for 3 months.
The hotels can hold an account in this site & whenever there is food wastage he can login and enter the details of food and location.The hotel can approve the request from carrier. The carrier can also hold an account and can retrieve the details. After retrieving the details the carrier can collect food from the hotels and can redistribute to the orphanages or others.
The orphanages/old-age homes can hold an account and they can send request to the carrier for food.They can send complaint to the carrier about the food.
Poor peoples section completely handled by carriers that means they can add poor peoples rough details as per based on location,and type of people. So when the orphanage or old age home don’t respond within a period carriers can pass to the location where poor peoples located. Then carriers update how much food they provided in an area.

Existing System
In existing system if any hotels have extra food  it will be become waste because instantly there is no way to share with anyone if they are having lots of food. Even if they want to give that extra food to any orphanage or poor people they don’t have time or don’t have an idea about that 
So that we have create a website for donate that extra food to poor people like  nearby orphanage or old age homes or poor people.

Proposed System
In proposed system we are reduce that food wastage using that application and also handover the balance food to right people. Through this site we are recovering from food poverty. 
This project is food redistribution is an enormously successful social innovation that tackles food waste and food poverty. the admin collect foods from hotel who entered balance food through their nearby agent then provide to nearest orphanages or old age homes.This project is food redistribution is an enormously successful social innovation that tackles food waste and food poverty. The user’s details are maintained confidential because it maintains a separate account for each user.This project consists of four modules. They are…
1.	Admin
2.	Hotel
3.	Food inspector
4.	Orphanage / Old-age home/Poor People
5.	Carrier
6.	Sponsor

Admin
	Admin can login to the system.
	Admin can register the details of carriers.
	Admin can approve hotel
	View complaints and reply
	Add Orphanage and old-age home
	Add Food inspector
	Add carrier
	Assign work to food inspector
	Add notification
Food inspector
	Verify hotels
	Add monthly reports
	View allotted work from admin
	Send complaint to admin inform hotel quality 
	View notification
	View & update profile
Hotel
	Add balance food
	Approve carrier request
	View & update profile
Orphanage / Old-age home
	Send food request to carrier
	Send complaint to carrier
	View & Update profile
Carrier
	View food request & replay
	View balance food and send request
	View complaint and replay
	View & update profile 

Sponsor
	Sponsors are the people who wants to donate food to these sectors also through carriers.
	They Book any Orphanage on a certain day
	Admin will pass the details through online to orphanage and fix the food sponsorship.
	Carrier will receive the food and reach it in the earlier described orphanage / Old age home.

SYSTEM SPECIFICATION
SOFTWARE SPECIFICATION:-
OPERATING SYSTEM            :  Windows XP Professional
 FRONT END                  :  PHP
BACK END                    : My SQL
 CODING LANGUAGE            :  PHP
HARDWARE SPECIFICATION:-
 SYSTEM                     :   Pentium III 700 MHz
 HARD DISK                  :   40 GB
 FLOPPY DRIVE               :   1.44 MB
 MONITOR                    :   15 VGA colour monitor
 MOUSE                      :   Logitech.
 RAM                        :   128 MB
 KEYBOARD                   :   110 keys enhanced.
 
 
 

 
SOURCE CODE

REGISTRATION

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
<meta content="text/html; charset=utf-8" http-equiv="Content-Type" />
<title>REGISTRATION </title>
</head>
<body style="background-color:fuchsia">
<div>
<center>
<form action="" method="post">
<h1> Registration Form</h1>
<div>
EMAIL:
<input type="text" name="email"/> </div>
<div>
PHONENUMBER:
<input type="text"name="phonenumber"/> </div>
<div>
USERNAME:
<input type="text"name="username"/> </div>
<div>
PASSWORD:
<input type="text" name="password"/></div>
<div>
<input type="submit" name="submit" style="background-color:lime"/></div>
</form>
<p>Click here to <a href='login.php'>Login</a></p>
</center>
</div>
<?php
include "connection.php";
if(isset($_POST['submit']))
{
$email=$_POST['email'];
$phonenumber=$_POST['phonenumber'];
$username=$_POST['username'];
$password=$_POST['password'];
$sql="insert into registration(email,phonenumber,username,password)values('$email','$phonenumber','$username','$password')";
$s=mysql_query($sql);
$sql1="insert into login(username,password,utype)values('$username','$password','user')";
$q=mysql_query($sql1);
if($s>0)
{
echo"<script>alert('thanks for registering');
window.location.href='welcome.php?m=success';<script>";
 
}
else
{
echo"<script>alert('incorrect');  </script>";
}
}
?>
</body>

</html>

LOGIN

<?php
include "connection.php";
if(isset($_POST['save']))
{
$username=$_POST['username'];
$password=$_POST['password'];
$sql="select*from login where username='$username'and password='$password'";
$res=mysql_query($sql)or die(mysql_error());
$count=mysql_rows($res);
if($count>0)
{
$d=mysql_fetch_array($res);
$user=$d[0];
$username=$d[1];
$utype=$d[2];
session_start();
$_SESSION['username']=$username;
$_SESSION['utype']=$utype;
$_SESSION['user']=$user;
if($utype=="user")
{
echo"<script>alert('Login successfully');
window.location.href='welcome.php?m=success';<script>";
}
}
else
{
echo"<script>alert('incorrect');<script>";
}
}
?>
<html>
<head>
</head>
<body style="background-color:navy">
<div>
<center>
<form action="" method="post">
<h1>Login</h1><br><br>
username
<input type="text" name="username"><br><br>
password
<input type=" text" name="password"><br><br>
<input type="submit" value="submit" name="save" style="backgound-color:yellow">
<a href="welcome.php"</a>
 </form></center>
</div>
</body>
</html>
  
  VIEW PAGE
  
  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
<meta content="text/html; charset=utf-8" http-equiv="Content-Type" />
<title> viewpage </title>
</head>
<body>
<center>
<h1> viewpage </h1>
</center>
<center>
<table border="1">
<tr>
<th> id</th>
<th>email</th>
<th>phonenumber</th>
<th>username</th>
<th>password</th>
<th>edit</th>
<th>delete</th>
</tr>
<?php
include "connection.php";
$sql = "select*from registration";
$exe = mysql_query($sql);
while ($row=mysql_fetch_array($exe))
{
?>

<tr>
<td><?php echo $row[0]?></td>
<td><?php echo $row[1]?></td>
<td><?php echo $row[2]?></td>
<td><?php echo $row[3]?></td>
<td><?php echo $row[4]?></td>
<td><a href="editm.php ? id=<?php echo $row[0]?>">edit</a></td>
<td><a href="delete.php?did=<?php echo $row[0]?>">delete</a></td>

</tr>

<?php
}
?>
</table>
</center>
</body>
</html>

CONNECTION

<?php
$server="127.0.0.1:3306";
$username="root";
$password=" ";
$dbname="molutty";
$con=mysql_connect($server,$username,$password);
$db_found=mysql_select_db($dbname,$con);
?>

EDIT

<?php
include "connection.php";
$id=$_GET['id'];
$sql="select*from registration where id='$id'";
$exe=mysql_query($sql);
$row=mysql_fetch_row($exe)
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
<meta content="text/html; charset=utf-8" http-equiv="Content-Type" />
<title>Untitled 1</title>
</head>

<body>
<form method="post" action="">
<input type="hidden" name="hd" value="<?php echo $row[0]?"><br>
<input type="text" name="email" />
<input type="text"name="phonenumber"/>
<input type="text"name="username"/>
<input type="text" name="password"/>
<input type="submit" name="submit" value="save">
</form>
</body>
<?php
include "connection.php";
$id=$_POST['hd'];
if(isset($_POST['submit']))
{
$email=$_POST['email'];
$phonenumber=$_POST['phonenumber'];
$username=$_POST['username'];
$password=$_POST['password'];
$sql="update registration set email='$email',phonenumber='$phonenumber',username='$username',password='$password' where id='$id'";
$exe=mysql_query($sql);
header(location:viewpage.php);
}
?>
</html>

DELETE

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
<meta content="text/html; charset=utf-8" http-equiv="Content-Type" />
<title>Untitled 1</title>
</head>

<body>
<?php 
include 'connection.php';
$id=$_GET['did'];
$s="delete from registration where id='$id'";
$exe=mysql_query($s);
header('location:viewpage.php');
?>
</body>

</html>





 
 
 
 

