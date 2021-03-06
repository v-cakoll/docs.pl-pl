---
title: Infer.NET aplikacja do match-up - programowanie probabilistyczne
description: Dowiedz się, jak używać programowania probabilistycznego z Infer.NET, aby utworzyć aplikację listy dopasowania do gier na podstawie uproszczonej wersji TrueSkill.
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 8e489d61c5e6cca53ba12b13fddd0b73c7f85ef9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092606"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Tworzenie aplikacji listy dopasowania gry z Infer.NET i probabilistycznym programowaniem

Ten poradnik uczy cię o probabilistycznym programowaniu za pomocą Infer.NET. Programowanie probabilistyczne jest podejściem uczenia maszynowego, w którym niestandardowe modele są wyrażane jako programy komputerowe. Pozwala na włączenie wiedzy domeny w modelach i sprawia, że system uczenia maszynowego jest bardziej interpretowany. Wspiera również wnioskowanie online - proces uczenia się w miarę pojawiania się nowych danych. Infer.NET jest używany w różnych produktach firmy Microsoft na platformach Azure, Xbox i Bing.

## <a name="what-is-probabilistic-programming"></a>Co to jest programowanie probabilistyczne?

Programowanie probabilistyczne pozwala na tworzenie statystycznych modeli rzeczywistych procesów.

## <a name="prerequisites"></a>Wymagania wstępne

- Lokalna konfiguracja środowiska programistycznego

  Ten przewodnik po instrukcji oczekuje, że masz maszynę, której możesz użyć do tworzenia. Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemach macOS, Windows lub Linux.

## <a name="create-your-app"></a>Tworzenie aplikacji

1. Otwórz nowy wiersz polecenia i uruchom następujące polecenia:

```dotnetcli
dotnet new console -o myApp
cd myApp
```

Polecenie `dotnet` tworzy `new` aplikację typu `console`. Parametr `-o` tworzy katalog `myApp` o nazwie, gdzie aplikacja jest przechowywana i wypełnia go wymaganymi plikami. Polecenie `cd myApp` umieszcza cię w nowo utworzonym katalogu aplikacji.

## <a name="install-infernet-package"></a>Zainstaluj pakiet Infer.NET

Aby użyć Infer.NET, należy `Microsoft.ML.Probabilistic.Compiler` zainstalować pakiet. W wierszu polecenia uruchom następujące polecenie:

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Zaprojektuj swój model

Przykładowa próbka wykorzystuje mecze tenisa stołowego lub piłkarzyki rozgrywane w biurze. Masz uczestników i wynik każdego meczu.  Chcesz wywnioskować umiejętności gracza z tych danych. Załóżmy, że każdy gracz ma normalnie rozproszone umiejętności utajone, a ich wydajność danego meczu jest hałaśliwą wersją tej umiejętności. Dane ogranicza wyniki zwycięzcy, aby być większa niż wyniki przegranego. Jest to uproszczona wersja popularnego modelu [TrueSkill,](https://www.microsoft.com/research/project/trueskill-ranking-system/) który obsługuje również zespoły, rysuje i inne rozszerzenia. [Zaawansowana wersja](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) tego modelu jest używana do kojarzeń w najlepiej sprzedających się tytułach gier Halo i Gears of War.

Musisz wymienić wywnioskowane umiejętności gracza, wraz z ich wariancją – miarą niepewności wokół umiejętności.

*Przykładowe dane wyników gry*

Gra |Zwycięzca | Przegrany
---------|----------|---------
 1 | Gracz 0 | Gracz 1
 2 | Gracz 0 | Gracz 3
 3 | Gracz 0 | Gracz 4
 4 | Gracz 1 | Gracz 2
 5 | Gracz 3 | Gracz 1
 6 | Gracz 4 | Gracz 2

Przy bliższym przyjrzeniu się przykładowym danym zauważysz, że gracze 3 i 4 mają jedną wygraną i jedną porażkę. Zobaczmy, jak wyglądają rankingi za pomocą programowania probabilistycznego. Zauważ również, że jest gracz zero, ponieważ nawet listy dopasowania biura są zerowe dla nas programistów.

## <a name="write-some-code"></a>Napisz jakiś kod

Po zaprojektowaniu modelu nadszedł czas, aby wyrazić go jako program probabilistyczny przy użyciu Infer.NET modelowania Interfejsu API. Otwórz `Program.cs` w ulubionym edytorze tekstu i zamień całą jego zawartość następującym kodem:

```csharp
namespace myApp

{
    using System;
    using System.Linq;
    using Microsoft.ML.Probabilistic;
    using Microsoft.ML.Probabilistic.Distributions;
    using Microsoft.ML.Probabilistic.Models;

    class Program
    {

        static void Main(string[] args)
        {
            // The winner and loser in each of 6 samples games
            var winnerData = new[] { 0, 0, 0, 1, 3, 4 };
            var loserData = new[] { 1, 3, 4, 2, 1, 2 };

            // Define the statistical model as a probabilistic program
            var game = new Range(winnerData.Length);
            var player = new Range(winnerData.Concat(loserData).Max() + 1);
            var playerSkills = Variable.Array<double>(player);
            playerSkills[player] = Variable.GaussianFromMeanAndVariance(6, 9).ForEach(player);

            var winners = Variable.Array<int>(game);
            var losers = Variable.Array<int>(game);

            using (Variable.ForEach(game))
            {
                // The player performance is a noisy version of their skill
                var winnerPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[winners[game]], 1.0);
                var loserPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[losers[game]], 1.0);

                // The winner performed better in this game
                Variable.ConstrainTrue(winnerPerformance > loserPerformance);
            }

            // Attach the data to the model
            winners.ObservedValue = winnerData;
            losers.ObservedValue = loserData;

            // Run inference
            var inferenceEngine = new InferenceEngine();
            var inferredSkills = inferenceEngine.Infer<Gaussian[]>(playerSkills);

            // The inferred skills are uncertain, which is captured in their variance
            var orderedPlayerSkills = inferredSkills
               .Select((s, i) => new { Player = i, Skill = s })
               .OrderByDescending(ps => ps.Skill.GetMean());

            foreach (var playerSkill in orderedPlayerSkills)
            {
                Console.WriteLine($"Player {playerSkill.Player} skill: {playerSkill.Skill}");
            }
        }
    }
}
```

## <a name="run-your-app"></a>Uruchamianie aplikacji

W wierszu polecenia uruchom następujące polecenie:

```dotnetcli
dotnet run
```

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do następujących:

```console
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

W wynikach zauważ, że gracz 3 plasuje się nieco wyżej niż gracz 4 według naszego modelu. To dlatego, że zwycięstwo gracza 3 nad graczem 1 jest bardziej znaczące niż zwycięstwo gracza 4 nad graczem 2 - należy pamiętać, że gracz 1 bije gracza 2. Gracz 0 jest mistrzem!

## <a name="keep-learning"></a>Utrzymuj naukę

Projektowanie modeli statystycznych jest umiejętnością samą w sobie. Zespół Microsoft Research Cambridge napisał [bezpłatną książkę online,](http://mbmlbook.com/)która daje łagodne wprowadzenie do artykułu. Rozdział 3 tej książki obejmuje model TrueSkill bardziej szczegółowo. Gdy masz na myśli model, możesz przekształcić go w kod, korzystając z [obszernej dokumentacji](https://dotnet.github.io/infer/) na Infer.NET stronie internetowej.

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z repozytorium Infer.NET GitHub, aby kontynuować naukę i znaleźć więcej przykładów.
> [!div class="nextstepaction"]
> [repozytorium github dotnet/infer](https://github.com/dotnet/infer)
