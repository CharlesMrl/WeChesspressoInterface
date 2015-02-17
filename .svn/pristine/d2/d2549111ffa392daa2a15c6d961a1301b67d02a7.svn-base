<?php
session_start();

?>



<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html>
    <head>
        <meta charset="UTF-8">
        <title>weChess</title>
        <link rel="stylesheet" type="text/css" href="css/chessboard-0.3.0.css" />
        <link rel="stylesheet" type="text/css" href="css/chessboard-0.3.0.min.css" />
        <script src="http://chessboardjs.com/js/json3.min.js"></script>
        <script src="http://chessboardjs.com/js/jquery-1.10.1.min.js"></script>
        <script src="http://chessboardjs.com/js/chessboard.js"></script>
    </head>
    <body>
        
        
            
        <?php 
        
        
        $playerId = $_POST["playerNb"];
        $opponentId = $_POST["opponentNb"];
        $_SESSION['playerId'] = $playerId;
        $_SESSION['opponentId'] = $opponentId;
        echo "Player : " . $playerId . " against opponent : ".$opponentId .".";
        
        $servername = "localhost";
        $username = "root";
        $password = "root";
        $dbname = "chessdb";

        // Create connection
        $conn = new mysqli($servername, $username, $password, $dbname);

        // Check connection
        if ($conn->connect_error) {
            die("Connection failed: " . $conn->connect_error);
        } 
        echo "Connected successfully";
        
       
       // $conn->select_db($dbname);
       $sql = "SELECT * from games where uidw = '" . $playerId . "' or uidb = '".$playerId."' ;";
       $result = $conn->query($sql);
       
       if ($result->num_rows > 0) {
            $row = $result->fetch_assoc();
        }
        // output data of each row
       
        
        $conn->close();
        
        $tab = split(" ", $row['fen']);
        $myfen=$tab[0];
        //echo $myfen;
        
        if ($row['uidw'] == $playerId) 
            {
                $playerColor = 'w';
            } 
            else 
                {
                    $playerColor = 'b';
                }
        $_SESSION['gameId'] = $row['id'];
?>
        
        
        <p id='myfen' ><?php echo $row['fen'] ?></p>
        <p id='playerColor'><?php echo $playerColor ?></p>
        <script src="http://chessboardjs.com/js/chess.js"></script>
        <div id="board" style="width: 400px"></div>
        <script src="./js/script.js"></script>
        
        <div id="board" style="width: 400px"></div>
        <input type="button" id="getPositionBtn" value="Show position in console" />
     
     
        

    </body>
</html>
