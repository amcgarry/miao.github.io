'<!doctype html>
<html>
<head>
    <title>My Javascript Color Guessing Game</title>
    <meta name="Javascript Color Guessing Game" content="Guessing Game by Audrey M">

    <script>
        /* GLOBAL VARIABLES */
            var colors = ["aqua", "azure", "coral", "cyan", "olive", "pink",
                        "tan", "teal", "tomato"];                               // Color List 
            var target_index = 0;       
            var target = null; 
            var count = 0;                                                      // Guess counter
            var finished = false;                                               // boolean for determining if the game is finished

        /* MAIN GAME FUNCTION - DO_GAME() */
            function do_game(){
                target_index = Math.floor(Math.random() * colors.length);       // Generate Random Number - store in "target_index"         
                target = colors[target_index];                                  // Pick a color from the color list - store in "target"

                while(!finished){
                    /*ask the player for their guess using prompt()*/
                        guess_input = prompt("I am thinking of a color in this list: " 
                                    + "\n\n" + colors.join("\n") + "\n\n" + 
                                    "Please enter your best guess:" + "\n\n" + "[target color is: " + target + "]");        
                                                                                // Get guess from player - store in "guess_input"
                    /*increase a variable count by 1*/
                        count++;

                        if(check_guess(guess_input)){           //is this a valid guess?
                            finished = true;
                        }
                }
            }



        /* CHECK THE INPUT FUNCTION - CHECK_GUESS() */

            function check_guess(input){
                var temp = "";

                if(input==""){
                    alert("You didn't enter anything Please enter a color.");
                }

                else if(valid_guess(input)){
                    temp = colors.indexOf(input);

                    if(temp>target_index){
                        alert("Your guess is higher than mine, please guess again");
                        return false;
                    }
                    else if(temp<target_index){
                        alert("Your guess is lower than mine, please guess again");
                        return false;
                    }
                    changeBackground(target);
                    alert("You guessed the correct color! It took you " + count + " guesses!");
                    return true;
                    }

                else{
                    alert("I don't recognize your color: Enter a color in the list!");
                    return false;}                            
            }

            
        /* HELPER FUNCTIONS */

            function valid_guess(input){
                var i = 0;

                while(i<colors.length){                 
                    if(colors[i].indexOf(input)!=0)
                        i++; 
                    else
                       return true;
                }
                return false;
            }

            function changeBackground(color) {
                document.body.style.background = color;
            }



    </script>
</head>
    <body onload ="do_game()"></body>

</html>'
