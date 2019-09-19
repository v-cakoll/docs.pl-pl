---
title: Tworzenie gry do aplikacji z listą z programowaniem Infer.NET i probabilistyczne
description: Dowiedz się, w jaki sposób używać programowania probabilistyczne z Infer.NET do tworzenia aplikacji listy rozgrywki gry na podstawie uproszczonej wersji programu TrueSkill.
ms.date: 05/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: edb747355f2d41d0400c6a989eea37423bbda2b4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117987"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Tworzenie gry do aplikacji z listą z programowaniem Infer.NET i probabilistyczne

Ten przewodnik zawiera wskazówki dotyczące programowania probabilistyczne przy użyciu Infer.NET. Programowanie probabilistyczne jest podejściem do uczenia maszynowego, w którym modele niestandardowe są wyrażane jako programy komputerowe. Umożliwia ona włączenie znajomości domeny w modelach i sprawia, że system uczenia maszynowego jest bardziej interpretowany. Obsługuje ona również wnioskowanie online — proces uczenia się w miarę nadejścia nowych danych. Infer.NET jest używany w różnych produktach firmy Microsoft na platformie Azure, Xbox i Bing.

## <a name="what-is-probabilistic-programming"></a>Co to jest programowanie probabilistyczne?

Programowanie probabilistyczne umożliwia tworzenie modeli statystycznych procesów rzeczywistych.

## <a name="prerequisites"></a>Wymagania wstępne

- Konfiguracja lokalnego środowiska deweloperskiego

  Ten przewodnik zawiera informacje o komputerze, którego można użyć do programowania. Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie MacOS, Windows lub Linux.

## <a name="create-your-app"></a>Tworzenie aplikacji

1. Otwórz nowy wiersz polecenia i uruchom następujące polecenia:

```dotnetcli
dotnet new console -o myApp
cd myApp
```

Polecenie tworzy aplikację typu`console`. `new` `dotnet` Parametr tworzy katalog o nazwie `myApp` , w którym jest przechowywana aplikacja, i wypełnia je wymaganymi plikami. `-o` `cd myApp` Polecenie przełączy Cię do nowo utworzonego katalogu aplikacji.

## <a name="install-infernet-package"></a>Zainstaluj pakiet Infer.NET

Aby korzystać z Infer.NET, należy zainstalować `Microsoft.ML.Probabilistic.Compiler` pakiet. W wierszu polecenia Uruchom następujące polecenie:

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Projektowanie modelu

Przykładowy przykład używa tabeli tenis lub Foosball, które są odtwarzane w biurze. Masz uczestników i wynik każdego dopasowania.  Chcesz wywnioskować umiejętności gracza z tych danych. Załóżmy, że każdy gracz ma zwykle rozłożoną, niezrównaną umiejętność, a ich wydajność jest w tej samej wersji. Dane ograniczają wydajność zwycięzcy do większej niż wydajność Loser. Jest to uproszczona wersja popularnego modelu [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) , który również obsługuje zespoły, rysuje i inne rozszerzenia. [Zaawansowana wersja](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) tego modelu jest używana do Matchmaking w najlepszej sprzedaży tytułów gry i narzędzia wojny.

Należy wystawić umiejętności z tytułu odroczonego odtwarzacza wraz z ich wariancją — miarą niepewności wokół umiejętności.

*Przykładowe dane wyników gry*

Rozgrywk |Wygrywając | Loser
---------|----------|---------
 1 | Gracz 0 | Gracz 1
 2 | Gracz 0 | Player 3
 3 | Gracz 0 | Gracz 4
 4 | Gracz 1 | Gracz 2
 5 | Player 3 | Gracz 1
 6 | Gracz 4 | Gracz 2

Dokładniejsze spojrzenie na przykładowe dane można zauważyć, że gracze 3 i 4 mają jedną z nich. Zobaczmy, jak wygląda Klasyfikacja przy użyciu programowania probabilistyczne. Zwróć również uwagę na to, że gracz ma wartość zero, ponieważ nawet listy dopasowania pakietu Office są równe zero w oparciu o deweloperów w Stanach Zjednoczonych.

## <a name="write-some-code"></a>Napisz kod

Po zaprojektowaniu modelu należy zaprezentować go jako program probabilistyczne przy użyciu interfejsu API modelowania Infer.NET. Otwórz `Program.cs` w ulubionym edytorze tekstów i Zastąp całą jego zawartość następującym kodem:

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

W wierszu polecenia Uruchom następujące polecenie:

```dotnetcli
dotnet run
```

## <a name="results"></a>Wyniki

Wyniki powinny wyglądać podobnie do następujących:

```
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

W wynikach Zwróć uwagę, że gracz 3 ranguje nieco więcej niż gracz 4 zgodnie z naszym modelem. Wynika to z faktu, że Victory odtwarzacza 3 w odtwarzaczu 1 jest bardziej znaczące niż Victory gracz 4 w odtwarzaczu 2 — należy zauważyć, że gracz 1 bije gracz 2. Gracz 0 to ogólna SEO!

## <a name="keep-learning"></a>Utrzymuj uczenie

Projektowanie modeli statystycznych jest własną umiejętnością. Zespół ds. Cambridge Research firmy Microsoft zapisał [bezpłatną książkę online](http://mbmlbook.com/), która zapewnia łagodne wprowadzenie do artykułu. Rozdział 3 tej książki dotyczy modelu TrueSkill w bardziej szczegółowy sposób. Jeśli masz model, możesz przekształcić go w kod przy użyciu [obszernej dokumentacji](https://dotnet.github.io/infer/) w witrynie sieci Web Infer.NET.

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z repozytorium usługi GitHub Infer.NET, aby kontynuować uczenie i znaleźć więcej przykładów.
> [!div class="nextstepaction"]
> [repozytorium GitHub/wnioskowanie](https://github.com/dotnet/infer)
