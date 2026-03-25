<?php
	session_start();
	require("db.php");
    $location = $_POST['selectLocation'];
    $location = mysqli_real_escape_string($con,$location);
    $username = $_SESSION['username'];
    
     if(!empty($_POST['product'])){
            //$_POST['product'] = mysqli_real_escape_string($con,$_POST['product']);
			$checkbox = implode(', ', $_POST['product']);
// Loop to store and display values of individual checked checkbox.
        //foreach($_POST['product[]'] as $selected){
               
        $query = "INSERT into `preorder` (username, location, product)
  VALUES ('$username', '$location', '$checkbox')";
          $result = mysqli_query($con,$query);
       // }
         
          if($result){
          echo "Thank you for your order. Please go to <a href='payment.php'> pay for your order. </a>";
          }
     } else {
		 echo "Please select at least at one drink.Please go back to <a href='preorder.php'> pre-order.</a>";
	 }
    
          

  ?>
