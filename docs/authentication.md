# Authentication server

One of the more difficult problems is authentication of users. There are three
parties involved here:

- The user that wants access to the game server.
- The game server (or bananas server) that needs to establish the identity of
  the user.
- The authentication system providing credentials in some way.


There are several ways to establish this goal. A few are listed below. More
alternatives likely exist.

1. The simplest way is probably to have the user contact the game server with
   the user information, the game server forwards the request to the
   authentication server, and the latter provides a yes/no answer.

   The obvious flaw here is that the game server has access to all user
   information without needing it. Encrypting the information wouldn't help.

2. Another option is to have the user authenticate him/herself with the
   authentication server with the goal of accessing a particular game server.
   The authentication server returns some information that can be passed on to
   the game server by the user. This information should be sufficient for the
   game server to decide acceptance.

3. A third option is a variation on the previous option. The user
   authenticates with the authentication server, and gets information to pass
   on to the game server. The game server then asks for confirmation at the
   authentication server using the sent information from the user.

A discussion what would be best is seems useful, also how to implement the
chosen approach should be decided.
