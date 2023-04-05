<!DOCTYPE HTML>
<html>
<head>
<style>
.error{color:#FF0000;}
</style>
</head>
<body>
<?php
//define variables and set to empty values.
$nameErr=$emailErr=$genderErr=$websiteErr="";
$name=$email=$gender=$comment=$website="";
if($_SERVER["REQUEST_METHOD"]=="POST"){
if(empty($_post["name"])){
$nameErr="name is required";
}else{
$name=test_input($_post["name"]);
}
if(empty($_post["email"])){
$emailErr="email is required";
$email=test_input($_post["email"]);}
if(empty($_post["website"])){
$website="";
}else{
$website=test_input($_post["website"]);
}
if(empty($_post["comment"])){
$comment="";
}else{
$comment=test_input($_post["comment"]);
}
if(empty($_post["gender"])){
$genderErr="gender is required";
}else{
$gender=test_input($_post["gender"]);
}
}
function test_input($data){
$data=trim($data);
$data=stripslashes($data);
$data=htmlspecialchars($data);
return $data;
}
?>
<h2>PHP FORM VALIDATION EXAMPLE</h2>
<p><span class="error">*required field</span></p>
<form method="post" action="<?php echo htmlspecialchars($_server["PHP_SELF"]);?>">
Name:<input type="text" name="name">
<span class="error">*<?php echo $nameErr;?></span><br><br>
Email:<input type="text" name="email"><span class="error">*<?php
echo $emailErr;?></span><br><br>
Website:<input type="text" name="website">
<span class="error"*<?php echo $websiteErr;?></span><br><br>
Comment:<textarea name="comment" rows="5" cols="40"></textarea><br><br>
Gender:<input type="radio" name="gender" value="female">Female
<input type="radio" name="gender" value="male">Male
<input type="radio" name="gender" value="other">other
<span class="error">*<?php echo $genderErr;?></span><br><br>
<input type="submit" name="submit" value="submit">
</form>
<?php
echo "<h2>Your Input:</h2>";
echo $name;
echo "<br>";
echo $email;
echo "<br>";
echo $website;
echo "<br>";
echo $comment;
echo "<br>";
echo $gender ;
?>
</body>
</html>
