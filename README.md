<html>
    <head>
        <title>Cards</title>

        <link rel="stylesheet" href="node_modules/deck-of-cards/example/example.css">
    </head>
    <body>
        <script src="node_modules/deck-of-cards/dist/deck.min.js"></script>

        <div id="container"></div>

        <script>
            var $container = document.getElementById('container');

            var threePlayers = [
                {x: -200, y: -350},
                {x: -100, y: -350},
                {x: 0, y: -350},
                {x: 100, y: -350},
                {x: 500, y: 0},
                {x: 600, y: 0},
                {x: 700, y: 0},
                {x: 800, y: 0},
                {x: -200, y: 350},
                {x: -100, y: 350},
                {x: 0, y: 350},
                {x: 100, y: 350},
                {x: -850, y: 200},
                {x: -750, y: 200},
                {x: -850, y: 75},
                {x: -750, y: 75},
                {x: -850, y: -50},
                {x: -750, y: -50},
                {x: -850, y: -175},
                {x: -750, y: -175},

            ];
            
            var twoPlayers = [
                {x: -200, y: -350},
                {x: -100, y: -350},
                {x: 0, y: -350},
                {x: 100, y: -350},
                {x: -200, y: 350},
                {x: -100, y: 350},
                {x: 0, y: 350},
                {x: 100, y: 350},
                {x: -850, y: 200},
                {x: -750, y: 200},
                {x: -850, y: 75},
                {x: -750, y: 75},
                {x: -850, y: -50},
                {x: -750, y: -50},
                {x: -850, y: -175},
                {x: -750, y: -175},

            ];

            function riggedCard() {
                const values = [1, 7, 8, 9, 10, 11, 12, 13];
                const randomIndex = Math.floor(Math.random() * values.length);
            return values[randomIndex];
            };

            var deck = Deck(true);

            // add to DOM
            deck.mount($container);
            
            var game;

            do {
                game = prompt("Which game? (IrishPoker, rigged, or AcesAndKings)");
            } while (game !== "IrishPoker" && game !== "AcesAndKings" && game !== "rigged");


            var players;
            do {
                players = prompt("How many players? (Enter 2 or 3)");
            } while (players !== "2" && players !== "3");



	    deck.shuffle();
	    deck.shuffle();
	    deck.shuffle();
	    deck.shuffle();
	    deck.shuffle();


            function IrishPoker(players){
            //shuffle 5 times
            
            console.log(window.innerWidth);
            console.log(window.innerHeight);
            
            setTimeout(() => {
                
            //deck.cards[4]['rank'] = 1;
            //deck.cards[4]['suit'] = 0;
            //deck.cards[5]['rank'] = 1;
            //deck.cards[5]['suit'] = 1;
            //deck.cards[6]['rank'] = 1;
            //deck.cards[6]['suit'] = 2;
            //deck.cards[7]['rank'] = 1;
            //deck.cards[7]['suit'] = 3;
            deck.cards.forEach(function (card, i) {

                card.enableFlipping();
                card.enableDragging();

                // move cards to lower right
                card.animateTo({
                    delay: 1000 + i ** 1.5, // wait 1 second + i * 2 ms
                    duration: 500,
                    ease: 'quartOut',

                    x: 800,
                    y: 350,
                });
            });
            }, 3000);

                if (players == 2) {
                    array = twoPlayers;
                } else if (players == 3) {
                    array = threePlayers;
                }

                deck.cards[4]['rank'] = 1;
                deck.cards[5]['rank'] = 1;
                deck.cards[6]['rank'] = 1;
                deck.cards[7]['rank'] = 1;
            setTimeout(() => {
                for (i = 0; i < array.length+1; i++) {
                console.log("i: " + i);
                console.log("x: " + array[i].x + " y: " + array[i].y);
                        deck.cards[i].animateTo({
                        delay: 1000 + i ** 2.5, // wait 1 second + i * 2 ms
                        duration: 500,
                        ease: 'quartOut',
                        x: array[i].x,
                        y: array[i].y
                    });
                }
            }, 5000);

            
    
            }

            function AcesAndKings(players){
                
            //shuffle 5 times
            
            console.log(window.innerWidth);
            console.log(window.innerHeight);
            
            setTimeout(() => {
                
            deck.cards.forEach(function (card, i) {

                card.enableFlipping();
                card.enableDragging();
                
                card['rank'] = (Math.floor(Math.random() * 1000) + 1) % 2 ? 13 : 1;
                card['suit'] = (Math.floor(Math.random() * 1000) + 1) % 4;
                // move cards to lower right
                card.animateTo({
                    delay: 1000 + i ** 1.5, // wait 1 second + i * 2 ms
                    duration: 500,
                    ease: 'quartOut',

                    x: 800,
                    y: 350,
                });
            });
            }, 3000);
            
                if (players == 2) {
                    array = twoPlayers;
                } else if (players == 3) {
                    array = threePlayers;
                }

            setTimeout(() => {
                for (i = 0; i < array.length+1; i++) {
                console.log("i: " + i);
                console.log("x: " + array[i].x + " y: " + array[i].y);
                        deck.cards[i].animateTo({
                        delay: 1000 + i ** 2.5, // wait 1 second + i * 2 ms
                        duration: 500,
                        ease: 'quartOut',
                        x: array[i].x,
                        y: array[i].y
                    });
                }
            }, 5000);
            }


            function rigged(players) {
                //shuffle 5 times
            
            console.log(window.innerWidth);
            console.log(window.innerHeight);
            
            setTimeout(() => {
                
            deck.cards.forEach(function (card, i) {

                card.enableFlipping();
                card.enableDragging();

                card['rank'] = riggedCard()
                // move cards to lower right
                card.animateTo({
                    delay: 1000 + i ** 1.5, // wait 1 second + i * 2 ms
                    duration: 500,
                    ease: 'quartOut',

                    x: 800,
                    y: 350,
                });
            });
            }, 3000);
            
                if (players == 2) {
                    array = twoPlayers;
                } else if (players == 3) {
                    array = threePlayers;
                }

            setTimeout(() => {
                for (i = 0; i < array.length+1; i++) {
                console.log("i: " + i);
                console.log("x: " + array[i].x + " y: " + array[i].y);
                        deck.cards[i].animateTo({
                        delay: 1000 + i ** 2.5, // wait 1 second + i * 2 ms
                        duration: 500,
                        ease: 'quartOut',
                        x: array[i].x,
                        y: array[i].y
                    });
                }
            }, 5000);
            }



            if (game == "IrishPoker") {
                IrishPoker(players);
            } else if (game == "AcesAndKings") {
                AcesAndKings(players);
            } else if (game == "rigged") {
                rigged(players);
            }
        </script>
    </body>
</html>
