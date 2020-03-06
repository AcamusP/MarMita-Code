const Discord = require('discord.js');
const message = require('discord.js');

const bot = new Discord.Client();

const token = 'Njg0MDU3MTI4NDYxMjcxMDUw.Xl0kDA.J8BxKxha7iSRmeYwY9mLj1aSSZg';

const PREFIX = ".";

bot.on('ready', () => {
    console.log('This bot is online !');
   
   
    bot.user.setPresence({activity: {name: `${bot.users.cache.size} Members`, type: 'LISTENING'}});
 

});

bot.on('message', message =>{
let args = message.content.substring(PREFIX.length).split(" ");

switch(args[0]){
case "poll":
    message.delete();
    if (!message.member.hasPermission('ADMINISTRATOR')) return message.reply("You can't make a poll because you don't have the premission")
    const Embed = new Discord.MessageEmbed()
    .setColor(15158332)
    .setTitle("Inititate Poll")
    .setDescription(".poll to intitiate a simple yes or no poll");

    if(!args[1]){
        message.delete();
        message.channel.send(Embed);
        break;
    
    }
    
      message.delete();
    
        let msgArgs = args.slice(1).join(" ");

    message.channel.send(msgArgs).then(messageReaction =>{
        messageReaction.react("??");
        messageReaction.react("??");
    });

        break;

        case 'clean':
            message.delete();
            if (!message.member.hasPermission('ADMINISTRATOR')) return message.reply("You can't delete messages because you don't have the premission")
            if (!args[1]) return message.reply("Please provide a number!!!").then(message => message.delete(200));
            
            else message.delete();
            message.channel.bulkDelete(args[1]).then (message.delete());
            message.delete();
            
            break;
           
            case 'help':
                message.delete();
                return message.reply(`If you have any problem you can DM the ??Discord Manager?? and they will be happy to help you!!!`)

                break;


                case 'inviterew':
                    message.delete();
                    if (!message.member.hasPermission('ADMINISTRATOR')) return message.reply("You can't delete messages because you don't have the premission")
                    return message.channel.send("If u want some free gta v money and RP you can get your reward through the ??invite-rewards?? @everyone").then(messageReaction =>{
                        messageReaction.react("*");
                        messageReaction.react("*");
                        messageReaction.react("*");
                        messageReaction.react("*");
                    });
                    



                    

    }


    
        
    }

    




);

bot.login(token);
