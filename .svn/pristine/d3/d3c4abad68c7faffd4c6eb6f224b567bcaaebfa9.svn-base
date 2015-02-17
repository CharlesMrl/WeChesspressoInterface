<?php 
    session_start();
    
    $newFen = $_POST["myFen"];
    //echo json_encode($_SESSION['opponentId']);
    


        // Create connection
    $conn = new mysqli('localhost', 'root', 'root', 'chessdb');
    if ($conn->connect_error) {
            die("Connection failed: " . $conn->connect_error);
        }
        
    //update the fen in games
    $updateFenGames = "UPDATE GAMES SET fen = '".$newFen."' where (id = '".$_SESSION['gameId']."');";
    $conn->query($updateFenGames);
    
    //add a move
    $addMove = "INSERT INTO MOVES (pid,uid,fen,type,time,pos1,pos2) VALUES ('".$_SESSION['playerId']."','".$_SESSION['playerId']."','".$newFen."','moveWeb',now(),'".$_POST["from"]."','".$_POST["to"]."');";
    $conn->query($addMove);
    
    
    
    
?>
