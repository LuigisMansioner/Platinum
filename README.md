# Platinum
My Bot Will Be Your Judge!

### Required Files/Directories
The bot requires four files and one directory not in the repository to run. These files are:
- `pass.txt`, which contains the password for the bots account
- `threadData.json`, a JSON file containing the IDs of the threads the bot can run in, along with the most recently parsed post in each of them. In the format of a dictionary, with each element having a key of the thread's ID (as a string), and a value containing various information about the thread.
- `data.json`, a JSON file containing various statistics. The default is the following: `{"parse_cycles": 0, "commands_parsed": 0, "commands_found": 0, "valid_commands": 0}`
- `botInfo.json`, a JSON file containing various data and strings for the bot.
- `logs`, a directory used to store log files. Default is empty.
- `files`, a directory used to store files generated by the bot. Default contains a single empty file named `_.txt`.

### `threadData.json`
This file is formatted using the following:
```
{
    "thread_id": {
    	"recentPost": postID,
        "types": [
        	"type1",
            "type2"
        ],
        "name": "The name of the thread",
        "date": {
            "year": year_of_first_post,
            "month": month_of_first_post,
            "day": day_of_first_post,
            "hour": hour_of_first_post,
            "minute": minute_of_first_post,
            "second": second_of_first_post
        }
    }
}
```
##### `"recentPost"`
(Integer) The postID of the most recent post as of the most recent parse-cycle. Default should be `0`.
##### `"types"`
(List of strings) The categories that the thread is in. Specific categories have additional properties. The default categories are:
```
postID    | The thread is part of the postID family.
postID_0  | Exclusive to postID 0.
2^n       | The thread is part of the 2^n series of postId threads.
3^n       | The thread is part of the 3^n series of postId threads.
4^n       | The thread is part of the 4^n series of postId threads.
7^n       | The thread is part of the 7^n series of postId threads.
2^^n      | The thread is part of the 2^^n series of postId threads.
fib       | The thread is part of the Fibonnaci series of postId threads.
pi        | The thread is part of the Pi series of postId threads.
hub       | The thread is considered the bots "hub" thread.
gpostID   | The thread is part of the global postID series of postId threads.
races     | The thread is part of the races series of postId threads.
allTitles | The thread is part of the All Titles series of postId threads.
tbg       | The thread is in the TBGs section of the forum.
rpg       | The thread is in the RPGs section of the forum.
mfg_main  | The thread is in the Main Topics section of the forum.
mfg_file  | The thread is in the Game Files section of the forum.
```
##### `"name"`
(String) The name of the thread.
##### `"date"`
(Dictonary of Integers) The date and time of the first post in the thread.
##### `"goal"`
(Integer) Exclusive to threads with the types `postID` or `gpostID`. The goal post ID.
##### `"estimates"`
(List of Strings) Exclusive to threads with the type `postID`. The estimates previously given for the thread. Default should be `[]`.
##### `"race_thread"`
(Integer) Exclusive to threads with the type `races`. The thread ID of the thread being raced against.

### `botInfo.json`
This file is formatted using the following:
```
{"name": "External Name", "id": "internal_id", "prefix": "command_prefix", "tagline": "Tagline", "offline": "Offline messgae", "online": "Online message", "onError": "Error message", "username": "Account Username", "uid": "account_id"}
```
(All items are strings.)
##### `"name"`
The name of the bot. This doesn't need to be the same as the account name.
##### `"id"`
The internal id of the bot. This is used for making commands exclusive to a single fork, or for making commands unable to be used by a single fork.
##### `"prefix"`
The prefix that the bot uses to find commands. This should be unique to your fork; a good prefix idea might be to use one or two letters from the name of your bot, followed by and exclamation mark (`!`).
##### `"tagline"`
The bot's tagline, displayed in its signature.
##### `"offline"`
The message in the bot's signature that's displayed when it's offline. A good message to start with, and the one Nihonium uses, is `"Currently offline."`.
##### `"online"`
The message in the bot's signature that's displayed when it's online. If the bot is abruptly shut down, such as when power to the machine it's running on is cut, this message will be displayed even though the bot is offline, so it's recommended that this message mentions the fact that the bot might be offline. A good message to start with, and the one Nihonium uses, is `"Currently online. ([i]may not be guaranteed[/i])"`.
##### `"onError"`
The message used when the bot encounters an error while parsing a command. A good message to start with, and the one Nihonium uses, is `"While parsing that command, an error occured: "`.
##### `"username"`
The username of the bot's account.
##### `"uid"`
The user id of the bot's account. This is required to change the signature.
