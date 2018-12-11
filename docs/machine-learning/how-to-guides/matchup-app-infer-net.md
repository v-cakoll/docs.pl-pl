---
title: Tworzenie gier dopasowania listy aplikacji za pomocą programowania probalistic i Infer.NET
description: Dowiedz się, jak za pomocą programowania probalistic Infer.NET utworzyć aplikację listy gier matchup oparty na uproszczonej wersji TrueSkill.
ms.date: 10/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ceeb0f43e03c7ce93f105498f44bf243eec86bbf
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152474"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Tworzenie gier dopasowania listy aplikacji przy użyciu Infer.NET i Probabilistyczne programowania

Ten przewodnik zawiera informacje na temat prawdopodobieństwa programowania przy użyciu Infer.NET. Probabilistyczne programowania jest podejście machine learning, gdzie niestandardowe modele są wyrażane jako programów komputerowych. Umożliwia zdobędziesz znajomość domeny w ramach modeli oraz sprawia, że system jest bardziej interpretowanej uczenia maszynowego. Obsługuje ona również wnioskowania online — proces uczenia nadejściu nowych danych. Infer.NET jest używana w różnych produktów w firmie Microsoft na platformie Azure, usługi Xbox i Bing.

## <a name="what-is-probabilistic-programming"></a>Co to jest programowanie Probabilistyczne?

Programowanie Probabilistyczne umożliwia nam tworzenie statystyczne modeli procesów w rzeczywistych warunkach. 

## <a name="prerequisites"></a>Wymagania wstępne

- Konfigurowanie środowiska deweloperskiego lokalne

  Ten poradnik oczekuje, że będziesz mieć maszyny, których można użyć do tworzenia aplikacji. .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) samouczek zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux.

## <a name="create-your-app"></a>Tworzenie aplikacji

1. Otwórz nowy wiersz polecenia i uruchom następujące polecenia:

```console
dotnet new console -o myApp
cd myApp
```

`dotnet` Polecenie tworzy `new` aplikacji typu `console`. `-o` Parametr tworzy katalog o nazwie `myApp` gdzie aplikacji są przechowywane i wypełnia je wymaganych plików. `cd myApp` Polecenie zapisuje do katalogu nowo utworzoną aplikację.

## <a name="install-infernet-package"></a>Zainstaluj pakiet Infer.NET

Aby użyć Infer.NET, musisz zainstalować `Microsoft.ML.Probabilistic.Compiler` pakietu. W wierszu polecenia Uruchom następujące polecenie:

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Projektowanie modelu

W przykładzie przykładzie użyto tenisa tabeli lub dopasowania foosball odtwarzany w biurze. Mamy z uczestnikami i wynik każdego dopasowania.  Chcemy wywnioskować gracza umiejętności z tych danych. Będziesz przyjęto założenie, że każdy z graczy ma zwykle rozproszonych umiejętności ukrytego, a ich wydajności w danym dopasowanie jest hałas wersją tej umiejętności. Dane ogranicza wydajność zwycięzca powinien być większy niż pominiętych wskutek wydajności. Jest to Uproszczona wersja popularnej [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) modelu, który również obsługuje zespołów, rysuje oraz inne rozszerzenia. [Zaawansowanych wersji](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) ten model jest używana do matchmaking w najlepiej sprzedające tytuły gry Halo i Gears War.

Potrzebujemy listy zadań do umiejętności wywnioskowane player wraz z ich wariancji — miary niepewności wokół umiejętności.

*Wynik gier przykładowych danych*

Gra |Zwycięzcy | Pominiętych wskutek
---------|----------|---------
 1 | Odtwarzacz 0 | Odtwarzacz 1
 2 | Odtwarzacz 0 | Odtwarzacz 3
 3 | Odtwarzacz 0 | Player 4
 4 | Odtwarzacz 1 | Odtwarzacz 2
 5 | Odtwarzacz 3 | Odtwarzacz 1
 6 | Player 4 | Odtwarzacz 2

Za pomocą bliższe spojrzenie na przykładowych danych zauważysz, że graczy, 3 i 4 mają jeden win i utraty jednej. Zobaczmy, rankingi wygląd za pomocą programowania Probabilistyczne. Zwróć uwagę, również ma odtwarzacz zero, ponieważ nawet office dopasowanie wykazów są zera nam deweloperów.

## <a name="write-some-code"></a>Pisanie kodu

Posiadanie zaprojektowany modelu, warto Wyraź ją jako Probabilistyczne programu przy użyciu Infer.NET interfejsów API do modelowania. Otwórz `Program.cs` w swoim ulubionym edytorze tekstów i Zastąp całą jego zawartość następującym kodem:

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

```console
dotnet run
```

## <a name="results"></a>Wyniki

Wyniki powinny wyglądać podobnie do następującego:

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

W wynikach Zwróć uwagę, że tego odtwarzacza 3 szereguje nieznacznie wyższe niż 4 graczy, zgodnie z naszym modelu. To dlatego zwycięstwa odtwarzacza 3 za pośrednictwem gracz 1 jest większe znaczenie niż zwycięstwa odtwarzacza 4 za pośrednictwem player 2 — Uwaga tego odtwarzacza 1 uderzeń player 2. Odtwarzacz 0 jest ogólny wyszukiwarek.  

## <a name="keep-learning"></a>Zachowaj nauki

Projektowanie statystyczne modeli jest umiejętności samodzielnie. Zapisane przez zespół Microsoft Research Cambridge [bezpłatnej książki online](http://mbmlbook.com/), co daje delikatnie wprowadzenie w artykule. Rozdział 3 tę książkę omówiono bardziej szczegółowo model TrueSkill. Po utworzeniu modelu należy pamiętać, można przekształcić go do kodu za pomocą [obszerną dokumentację](https://dotnet.github.io/infer/) w witrynie sieci Web Infer.NET.

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z repozytorium Infer.NET GitHub, aby kontynuować zapoznawanie się z i znaleźć więcej przykładów.
> [!div class="nextstepaction"]
> [polecenia DotNet/wywnioskować repozytorium GitHub](https://github.com/dotnet/infer)
