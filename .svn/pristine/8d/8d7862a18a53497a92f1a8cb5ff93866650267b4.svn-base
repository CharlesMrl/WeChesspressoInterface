var init = function() {

//--- start example JS ---
var myfen = document.getElementById('myfen').innerHTML;
var playerColor = document.getElementById('playerColor').innerHTML;

if (playerColor == 'b')
var playerColorRegEx= /^w/;
else playerColorRegEx = /^b/;

var board, game = new Chess(myfen);


var removeGreySquares = function() {
  $('#board .square-55d63').css('background', '');
};

var greySquare = function(square) {
  var squareEl = $('#board .square-' + square);
  
  var background = '#a9a9a9';
  if (squareEl.hasClass('black-3c85d') === true) {
    background = '#696969';
  }

  squareEl.css('background', background);
};

var onDragStart = function(source, piece) {
  // do not pick up pieces if the game is over
  // or if it's not that side's turn
  /*if (game.game_over() === true ||
      (game.turn() === playerColor && piece.search(/^b/) !== -1) ||
      (game.turn() === playerColor && piece.search(/^w/) !== -1)) {
    return false;
  }*/
    if (game.in_checkmate() === true || game.in_draw() === true ||
    piece.search(playerColorRegEx) !== -1) {
    return false;
  }
};

var onDrop = function(source, target) {
  removeGreySquares();

  // see if the move is legal
  var move = game.move({
    from: source,
    to: target,
    promotion: 'q' // NOTE: always promote to a queen for example simplicity
  });
  
  // illegal move
  if (move === null) return 'snapback';
  
        $.ajax({
        type: "POST",
        url: "./postDatas.php",
        data: { myFen: game.fen(), from : move.from, to: move.to},
        }
                
              )

        .done(function( msg ) {
          //alert( "Data Saved: " + msg );
        });


      };

var onMouseoverSquare = function(square, piece) {
  // get list of possible moves for this square
  var moves = game.moves({
    square: square,
    verbose: true
  });

  // exit if there are no moves available for this square
  if (moves.length === 0) return;

  // highlight the square they moused over
  greySquare(square);

  // highlight the possible squares for this piece
  for (var i = 0; i < moves.length; i++) {
    greySquare(moves[i].to);
  }
};

var onMouseoutSquare = function(square, piece) {
  removeGreySquares();
};

var onSnapEnd = function() {
  board.position(game.fen());
};


//alert(myfen);
var cfg = {
  draggable: true,
  position: myfen,
  onDragStart: onDragStart,
  onDrop: onDrop,
  onMouseoutSquare: onMouseoutSquare,
  onMouseoverSquare: onMouseoverSquare,
  onSnapEnd: onSnapEnd
};

board =  new ChessBoard('board', cfg);

//--- end example JS ---
$('#getPositionBtn').on('click', function() {

  console.log("Current position as a FEN string:");
  console.log(board.fen());
  console.log(game.fen());
  
  console.log("Player color :");
  console.log(playerColor);
  console.log("Player color regex:");
  console.log(playerColorRegEx);
  
});

function sendFen()
{
    return game.fen();
}
}; // end init()

$(document).ready(init);