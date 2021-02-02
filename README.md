# Info

[Create tickets using Our Module ogskies_discord_ticket in discord.js without any effort!!](https://www.npmjs.com/package/ogskies_discord_ticket)

# Useful Links

- [Github issue board](https://github.com/OGSkies/OGSkies_Discord_Ticket/issues)

- [Join my discord server](https://discord.gg/tN62YQZ58e)

- [View our website for bot updates and who knows maybe you will be the first one to see the new updates](https://ogskiesbot.weebly.com)

# Contacts
___
**||========> contact me **Block Bytes#7245** on discord <========||**
____


# How to use our module

`npm i ogskies_discord_ticket`

```javaScript
// Importing Modules
const Discord = require('discord.js')
const client = new Discord.Client()
const { OGSkiesTicket } = require('ogskies_discord_ticket')
const ticket = new OGSkiesTicket()

// When bot is ready
client.on('ready', () => {
    console.log(`${client.user.tag} is now online!`)
    console.log("Bot: Hosting " +
      `${client.users.cache.size}` +
      " users, in " +
      `${client.channels.cache.size}` +
      " channels of " +
      `${client.guilds.cache.size}` +
      " guilds."
  );)
  // Example: Bot: Hosting 1053 users, in 265 channels of 10 guilds.
})


client.on('message', async message => {
    let prefix = "+";
    const args = message.content.slice(prefix.length).split(" ");
    const command = args.shift().toLowerCase();
    if ( command == 'ticket' ) {
        ticket.makeTicket(message, args.join(" "))
        /*
         Creates a new ticket
         if no reason is provoided the reason is "No Reason Provoided"
         Reason is optional and not needed to create a channel
         if you want the message author to be dmed that he created a
         ticket pls use >>> ticket.makeTicket(message, args.join(" "), true)
         for default its set for false
        */
    } else if ( command == 'close' ) {
        ticket.closeTicket(message)
    } else if ( command == 'role' ) {
        ticket.setRole(message)
        // Seting a support role
        // Support roles gets pinged whenever a ticket is maded
    } else if ( command == 'remove-role' ) {
        ticket.DelRole(message, client)
        // Remove a support role
    } else if ( command == 'send' ) {
        ticket.msgTicketChannel(message, prefix)
        // send a message to a ticket
    } else if ( command == 'category' ) {
        ticket.Category(message, client, args.join(" "))
        // creates a ticket at the selected Category
    } else if ( command == 'delcategory' ) {
        ticket.DelCategory(message, client)
        // Deleated the selected category from the list of creating 
        // tickets, next time tickets will not be created at that category
    } else if ( command == 'embed-message' ) {
        ticket.editEmbed(message, args.join(" "))
        // Set's a message when user creates a ticket
    } else if ( command == 'remove-embed' ) {
        ticket.DelEmbed(message, client)
        // Removes the embed message that are used in every ticket getting 
        // created
    } else if ( command == `adduser` ) {
        ticket.ticketAddUser(message);
        // Add's a user to a ticket
    } else if ( command === `id` ) {
        ticket.fetchChanID(message, args.join(" "))
        // gets a channel id
    }
})
client.login('TOKEN')
```

**_Make sure to try this code above if you didnt understand a part or dont know how to use a specific command 👍_**
