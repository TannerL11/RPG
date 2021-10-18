# RPG
const readlineSync = require('readline-sync');

const name = readlineSync.question('What is your name traveler? ');

readlineSync.question(`Hello ${name}, You are now in the haunted dungeon! (Press Enter to Continue)`)

const enemies = ['Zombie', 'Spider', 'Skeleton', 'Phantom'];
const treasure = ['Med Kit', '50 XP', 'Sword', 'Bow & Arrow'];
var prize = [];
let playerHealth = 50;
const menu = ['Walk', 'Run away', 'Backpack'];
let collected = treasure[Math.floor(Math.random()*treasure.length)];
function game(){
    const attackPower = Math.floor(Math.random() * (3-2+4) + 4);
    const enemy = enemies[Math.floor(Math.random() * enemies.length)];
    let enemyHealth = 30;
    const enemyPower = Math.floor(Math.random()* (6-4+2)+3);

    const index = readlineSync.keyInSelect(menu, 'What is your next move?');

    if(menu[index] == 'Run away'){
        console.log (`${name} has ran away from the Dungeon!`);
        return playerHealth = 0;
    } 
    else if (menu[index] == 'Backpack'){
        console.log(`${name}'s backpack contains ${collected} \n Health Bar at ${playerHealth} out of 30`);
    }
    else if(menu[index] === 'Walk'){
        let key = Math.random();
        if (key <= .3) {
            console.log('Walking...');
        }
        else if (key >= .3){
            console.log (`You have crossed paths with ${enemy}!`);
            while (enemyHealth > 0 && playerHealth > 0) {
                const player = readlineSync.question(`Will you run (press "r") or will you stand and fight? (press "f") `);
                    switch(player){
                        case 'r':
                            const run = Math.random();
                            if (run < .5){
                                console.log(`${enemy} is faster and hits you for ${enemyPower} damage.`);
                            }
                            else {
                                console.log('You ran away!!');
                                break;
                            }
                        case 'f':
                            enemyHealth -= attackPower;
                            console.log(`You attacked ${enemy} for ${attackPower} damage.`);
                            playerHealth -= enemyPower;
                            console.log(`You were attacked for ${enemyPower} damage.`);
                            if (enemyHealth <= 0){
                                console.log(`You have killed the ${enemy} and found ${collected}.`);
                                let loot = Math.random();
                                if (loot <= .3){
                                    prize.push(collected);
                                }
                                }
                            else if (playerHealth <= 0){
                                console.log(`${enemy} has killed ${name}. GAME OVER`);
                            }
                            }

                    }
            }
        }
    }
 while(playerHealth > 0) {
    playerHealing = function(){
        playerAlive = true;
        playerHealth = 30
    }
    playerHealing();
    game();
} 
