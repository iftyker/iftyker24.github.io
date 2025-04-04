// pages/index.tsx
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import Link from "next/link";

const games = [
  { id: "1", name: "Tic Tac Toe" },
  { id: "2", name: "Rock Paper Scissors" },
  { id: "3", name: "Clicker Game" },
  // Add more here...
];

export default function Home() {
  const [search, setSearch] = useState("");
  const filteredGames = games.filter((game) =>
    game.name.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div className="min-h-screen bg-gray-100 p-6">
      <h1 className="text-3xl font-bold mb-4 text-center">🎮 1000 Games Hub</h1>
      <div className="max-w-md mx-auto mb-6">
        <Input
          placeholder="Search games..."
          value={search}
          onChange={(e) => setSearch(e.target.value)}
        />
      </div>
      <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4">
        {filteredGames.map((game) => (
          <Link key={game.id} href={`/games/${game.id}`}>
            <Card className="cursor-pointer hover:shadow-lg transition">
              <CardContent className="p-4 text-center font-medium">
                {game.name}
              </CardContent>
            </Card>
          </Link>
        ))}
      </div>
    </div>
  );
}

// pages/games/1.tsx (Tic Tac Toe)
export default function TicTacToe() {
  return (
    <div className="min-h-screen p-6 bg-white">
      <h2 className="text-2xl font-semibold mb-4">Tic Tac Toe</h2>
      <p>Game code goes here...</p>
    </div>
  );
}
