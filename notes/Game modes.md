# Game modes
Game modes specify what the games should do on the current tick. It is a good idea, when creating a game, to start by defining its modes, as it can give an outline of how the game is going to play out. One useful way of representing game modes is using a rust `enum`.

```ad-example
collapse: open

~~~rust
enum GameMode {
	Menu,
	Playing,
	End,
}
~~~
```