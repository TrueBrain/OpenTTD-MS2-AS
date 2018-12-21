# Terminology

- *game server*: Computer system that hosts a multi-player OpenTTD game.
- *master server*: Computer system that provides information about existing
  (available) game servers to users.

# Master server

The purpose of a master server is to make game servers findable for players.
It does that by

a) accepting messages from game servers to inform the master server of the
   existence of the game server,
b) exchange information with known game servers for their current setup and
   situation, and
c) accept queries from users, asking for available servers.

In addition, it may be useful to also accept connections from other master
servers, making it possible to build meta master servers, a master server that
know about other master servers.


# Interactions with game servers

There are two forms of interactions with game servers from the master server.
The first interaction is a 'hello, I am alive' message from the game server, the
second interaction is a check whether the game server is still up.

Since the service provided by the game server may change in time, at least the
second interaction should provide some information about the situation of the
game server.

Useful information could be

- Community information
  - Name of the community running the server
  - Website of the community
  - Registration requirements
  - Rules of the community
  - Admin contact
  - Languages

  - Master server of the community
  - Authentication server of the community

- Game server information
  - Name of the game server
  - IP address for game play
  - IP address for game server

- Current Game information
  - Used OpenTTD program name (patchpack, nightly, stable, etc)
  - Used OpenTTD program version
  - Game type (transport, aesthetic, competitive, etc)
  - Game series (competition game #12, 2018 Q4)
  - Keywords
  - Start year
  - End condition (end year, amount of money, ...)
  - Progress of the game (how much is done, current scores, etc)
  - Current year
  - Current number of free/open companies
  - Current number of active companies
  - Current number of spectators
  - Allowed players
  - Game map description
    - Climate
    - Map size
    - Descriptive text
    - Used NewGRFs

- Next game information

  Would be mostly like the current game information, except the 'current'
  values can be omitted.


While most information is likely useful in some cases, most is also not always
needed or desired. For actual transport of the information, perhaps the
simplest form is a YAML or JSON format, with UTF-8 text.


# Interaction with users

The user can query for existing (alive) game servers. Some possible criteria for
selecting a server

- Used OpenTTD program name (patchpack, nightly, stable, etc)
- Used OpenTTD program versions (probably some form of wildcard or range)
- Game types
- Communities
- Map sizes
- Keywords (likely with and/or)
- Climates

The master returns a list of game servers that match the selection. The user
can then query the game server for more information.


# Assumptions

- One authentication server is sufficient for a community.

# Questions that need an answer

If you have some information or ideas, please update the document, and update
the question as well.

- Does it need fallback IP addresses for authentication and game servers?

- How much trust should exist between the master server and a game server,
  that is, should it identify itself?

  Theoretically, it could prevent 'stealing' a game server by changing the IP
  address.

- Check what information the current master server exchanges, and resolve any
  missing information.

- A user querying the game server for more detailed information may be a bad
  idea.
