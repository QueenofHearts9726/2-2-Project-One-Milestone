# 2-2-Project-One-Milestone
//Complete the UML diagram to accurately represent a singleton pattern for the Game Service class.
//Use the singleton pattern to adapt an ordinary class definition, so that only one instance of the GameService class exists in memory at any time.
//Explain the purpose and characteristics of the singleton pattern you are using in the context of this application. Include this brief explanation as comments in your code.
//In the Game Service class, use the iterator pattern to complete the coding for the addGame() and both getGame() methods
//Explain the purpose and characteristics of the iterator pattern you are using in the context of this application. Include this brief explanation as comments in your code. //The comments will be used to communicate your understanding of the pattern you implemented to your instructor.
//Demonstrate industry standard best practices to enhance the readability of your code, including appropriate naming conventions and in-line comments that describe the //functionality.
//Run and compile the code to ensure the application is functional and the requirements have been met

2-2 Project One Milestone FIXME file
package com.gamingroom;

import java.util.ArrayList;
import java.util.List;

// Game class implementation
class Game {
    private long id;
    private String name;

    public Game(long id, String name) {
        this.id = id;
        this.name = name;
    }

    public long getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    @Override
    public String toString() {
        return "Game{" +
                "id=" + id +
                ", name='" + name + '\'' +
                '}';
    }
}

// GameService class implementation
class GameService {
    private List<Game> games = new ArrayList<>();
    private static long nextGameId = 1;

    public Game addGame(String name) {
        Game game = new Game(nextGameId++, name);
        games.add(game);
        return game;
    }

    public Game getGame(int index) {
        if (index < 0 || index >= games.size()) {
            throw new IndexOutOfBoundsException("Invalid index");
        }
        return games.get(index);
    }
    public int getGameCount() {
        return games.size();
    }
}

// Singleton Tester class implementation
class SingletonTester {
    public static void testSingleton() {
        // Implement singleton testing logic here
        // (e.g., ensure only one instance exists)
    }
}

// ProgramDriver class implementation
public class ProgramDriver {
    public static void main(String[] args) {
        GameService gameService = new GameService();

        // Add some games
        gameService.addGame("Game 1");
        gameService.addGame("Game 2");
        gameService.addGame("Game 3");

        // Get the number of games
        int gameCount = gameService.getGameCount();
        System.out.println("Number of games: " + gameCount);

        // Get the first game
        Game firstGame = gameService.getGame(0);
        System.out.println("First game: " + firstGame);

        // Test singleton (if applicable)
        SingletonTester.testSingleton();
    }
}
