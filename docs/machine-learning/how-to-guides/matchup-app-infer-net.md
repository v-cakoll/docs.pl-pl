---
title: Tworzenie gry do aplikacji z listą z programowaniem Infer.NET i probabilistyczne
description: Dowiedz się, w jaki sposób używać programowania probabilistyczne z Infer.NET do tworzenia aplikacji listy rozgrywki gry na podstawie uproszczonej wersji programu TrueSkill.
ms.date: 05/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: f6f91aecfe7fdeffb7e8913309046c7942ecbab7
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957211"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="190d5-103">Tworzenie gry do aplikacji z listą z programowaniem Infer.NET i probabilistyczne</span><span class="sxs-lookup"><span data-stu-id="190d5-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="190d5-104">Ten przewodnik zawiera wskazówki dotyczące programowania probabilistyczne przy użyciu Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="190d5-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="190d5-105">Programowanie probabilistyczne jest podejściem do uczenia maszynowego, w którym modele niestandardowe są wyrażane jako programy komputerowe.</span><span class="sxs-lookup"><span data-stu-id="190d5-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="190d5-106">Umożliwia ona włączenie znajomości domeny w modelach i sprawia, że system uczenia maszynowego jest bardziej interpretowany.</span><span class="sxs-lookup"><span data-stu-id="190d5-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="190d5-107">Obsługuje ona również wnioskowanie online — proces uczenia się w miarę nadejścia nowych danych.</span><span class="sxs-lookup"><span data-stu-id="190d5-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="190d5-108">Infer.NET jest używany w różnych produktach firmy Microsoft na platformie Azure, Xbox i Bing.</span><span class="sxs-lookup"><span data-stu-id="190d5-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="190d5-109">Co to jest programowanie probabilistyczne?</span><span class="sxs-lookup"><span data-stu-id="190d5-109">What is probabilistic programming?</span></span>

<span data-ttu-id="190d5-110">Programowanie probabilistyczne umożliwia tworzenie modeli statystycznych procesów rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="190d5-110">Probabilistic programming allows you to create statistical models of real-world processes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="190d5-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="190d5-111">Prerequisites</span></span>

- <span data-ttu-id="190d5-112">Konfiguracja lokalnego środowiska deweloperskiego</span><span class="sxs-lookup"><span data-stu-id="190d5-112">Local development environment setup</span></span>

  <span data-ttu-id="190d5-113">Ten przewodnik zawiera informacje o komputerze, którego można użyć do programowania.</span><span class="sxs-lookup"><span data-stu-id="190d5-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="190d5-114">Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie MacOS, Windows lub Linux.</span><span class="sxs-lookup"><span data-stu-id="190d5-114">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on macOS, Windows, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="190d5-115">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="190d5-115">Create your app</span></span>

1. <span data-ttu-id="190d5-116">Otwórz nowy wiersz polecenia i uruchom następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="190d5-116">Open a new command prompt and run the following commands:</span></span>

```dotnetcli
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="190d5-117">Polecenie `dotnet` tworzy aplikację `new` typu `console`.</span><span class="sxs-lookup"><span data-stu-id="190d5-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="190d5-118">Parametr `-o` tworzy katalog o nazwie `myApp`, w którym jest przechowywana aplikacja i wypełnia je wymaganymi plikami.</span><span class="sxs-lookup"><span data-stu-id="190d5-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="190d5-119">Polecenie `cd myApp` przełączy Cię do nowo utworzonego katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="190d5-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="190d5-120">Zainstaluj pakiet Infer.NET</span><span class="sxs-lookup"><span data-stu-id="190d5-120">Install Infer.NET package</span></span>

<span data-ttu-id="190d5-121">Aby korzystać z Infer.NET, należy zainstalować pakiet `Microsoft.ML.Probabilistic.Compiler`.</span><span class="sxs-lookup"><span data-stu-id="190d5-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="190d5-122">W wierszu polecenia Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="190d5-122">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="190d5-123">Projektowanie modelu</span><span class="sxs-lookup"><span data-stu-id="190d5-123">Design your model</span></span>

<span data-ttu-id="190d5-124">Przykładowy przykład używa tabeli tenis lub Foosball, które są odtwarzane w biurze.</span><span class="sxs-lookup"><span data-stu-id="190d5-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="190d5-125">Masz uczestników i wynik każdego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="190d5-125">You have the participants and outcome of each match.</span></span>  <span data-ttu-id="190d5-126">Chcesz wywnioskować umiejętności gracza z tych danych.</span><span class="sxs-lookup"><span data-stu-id="190d5-126">You want to infer the player's skills from this data.</span></span> <span data-ttu-id="190d5-127">Załóżmy, że każdy gracz ma zwykle rozłożoną, niezrównaną umiejętność, a ich wydajność jest w tej samej wersji.</span><span class="sxs-lookup"><span data-stu-id="190d5-127">Assume that each player has a normally distributed latent skill and their given match performance is a noisy version of this skill.</span></span> <span data-ttu-id="190d5-128">Dane ograniczają wydajność zwycięzcy do większej niż wydajność Loser.</span><span class="sxs-lookup"><span data-stu-id="190d5-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="190d5-129">Jest to uproszczona wersja popularnego modelu [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) , który również obsługuje zespoły, rysuje i inne rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="190d5-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="190d5-130">[Zaawansowana wersja](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) tego modelu jest używana do Matchmaking w najlepszej sprzedaży tytułów gry i narzędzia wojny.</span><span class="sxs-lookup"><span data-stu-id="190d5-130">An [advanced version](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="190d5-131">Należy wystawić umiejętności z tytułu odroczonego odtwarzacza wraz z ich wariancją — miarą niepewności wokół umiejętności.</span><span class="sxs-lookup"><span data-stu-id="190d5-131">You need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="190d5-132">*Przykładowe dane wyników gry*</span><span class="sxs-lookup"><span data-stu-id="190d5-132">*Game result sample data*</span></span>

<span data-ttu-id="190d5-133">Rozgrywk</span><span class="sxs-lookup"><span data-stu-id="190d5-133">Game</span></span> |<span data-ttu-id="190d5-134">Wygrywając</span><span class="sxs-lookup"><span data-stu-id="190d5-134">Winner</span></span> | <span data-ttu-id="190d5-135">Loser</span><span class="sxs-lookup"><span data-stu-id="190d5-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="190d5-136">1</span><span class="sxs-lookup"><span data-stu-id="190d5-136">1</span></span> | <span data-ttu-id="190d5-137">Gracz 0</span><span class="sxs-lookup"><span data-stu-id="190d5-137">Player 0</span></span> | <span data-ttu-id="190d5-138">Gracz 1</span><span class="sxs-lookup"><span data-stu-id="190d5-138">Player 1</span></span>
 <span data-ttu-id="190d5-139">2</span><span class="sxs-lookup"><span data-stu-id="190d5-139">2</span></span> | <span data-ttu-id="190d5-140">Gracz 0</span><span class="sxs-lookup"><span data-stu-id="190d5-140">Player 0</span></span> | <span data-ttu-id="190d5-141">Player 3</span><span class="sxs-lookup"><span data-stu-id="190d5-141">Player 3</span></span>
 <span data-ttu-id="190d5-142">3</span><span class="sxs-lookup"><span data-stu-id="190d5-142">3</span></span> | <span data-ttu-id="190d5-143">Gracz 0</span><span class="sxs-lookup"><span data-stu-id="190d5-143">Player 0</span></span> | <span data-ttu-id="190d5-144">Gracz 4</span><span class="sxs-lookup"><span data-stu-id="190d5-144">Player 4</span></span>
 <span data-ttu-id="190d5-145">4</span><span class="sxs-lookup"><span data-stu-id="190d5-145">4</span></span> | <span data-ttu-id="190d5-146">Gracz 1</span><span class="sxs-lookup"><span data-stu-id="190d5-146">Player 1</span></span> | <span data-ttu-id="190d5-147">Gracz 2</span><span class="sxs-lookup"><span data-stu-id="190d5-147">Player 2</span></span>
 <span data-ttu-id="190d5-148">5</span><span class="sxs-lookup"><span data-stu-id="190d5-148">5</span></span> | <span data-ttu-id="190d5-149">Player 3</span><span class="sxs-lookup"><span data-stu-id="190d5-149">Player 3</span></span> | <span data-ttu-id="190d5-150">Gracz 1</span><span class="sxs-lookup"><span data-stu-id="190d5-150">Player 1</span></span>
 <span data-ttu-id="190d5-151">6</span><span class="sxs-lookup"><span data-stu-id="190d5-151">6</span></span> | <span data-ttu-id="190d5-152">Gracz 4</span><span class="sxs-lookup"><span data-stu-id="190d5-152">Player 4</span></span> | <span data-ttu-id="190d5-153">Gracz 2</span><span class="sxs-lookup"><span data-stu-id="190d5-153">Player 2</span></span>

<span data-ttu-id="190d5-154">Dokładniejsze spojrzenie na przykładowe dane można zauważyć, że gracze 3 i 4 mają jedną z nich.</span><span class="sxs-lookup"><span data-stu-id="190d5-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="190d5-155">Zobaczmy, jak wygląda Klasyfikacja przy użyciu programowania probabilistyczne.</span><span class="sxs-lookup"><span data-stu-id="190d5-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="190d5-156">Zwróć również uwagę na to, że gracz ma wartość zero, ponieważ nawet listy dopasowania pakietu Office są równe zero w oparciu o deweloperów w Stanach Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="190d5-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="190d5-157">Napisz kod</span><span class="sxs-lookup"><span data-stu-id="190d5-157">Write some code</span></span>

<span data-ttu-id="190d5-158">Po zaprojektowaniu modelu należy zaprezentować go jako program probabilistyczne przy użyciu interfejsu API modelowania Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="190d5-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="190d5-159">Otwórz `Program.cs` w ulubionym edytorze tekstów i Zastąp całą jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="190d5-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="190d5-160">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="190d5-160">Run your app</span></span>

<span data-ttu-id="190d5-161">W wierszu polecenia Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="190d5-161">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet run
```

## <a name="results"></a><span data-ttu-id="190d5-162">Wyniki</span><span class="sxs-lookup"><span data-stu-id="190d5-162">Results</span></span>

<span data-ttu-id="190d5-163">Wyniki powinny wyglądać podobnie do następujących:</span><span class="sxs-lookup"><span data-stu-id="190d5-163">Your results should be similar to the following:</span></span>

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

<span data-ttu-id="190d5-164">W wynikach Zwróć uwagę, że gracz 3 ranguje nieco więcej niż gracz 4 zgodnie z naszym modelem.</span><span class="sxs-lookup"><span data-stu-id="190d5-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="190d5-165">Wynika to z faktu, że Victory odtwarzacza 3 w odtwarzaczu 1 jest bardziej znaczące niż Victory gracz 4 w odtwarzaczu 2 — należy zauważyć, że gracz 1 bije gracz 2.</span><span class="sxs-lookup"><span data-stu-id="190d5-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="190d5-166">Gracz 0 to ogólna SEO!</span><span class="sxs-lookup"><span data-stu-id="190d5-166">Player 0 is the overall champ!</span></span>

## <a name="keep-learning"></a><span data-ttu-id="190d5-167">Utrzymuj uczenie</span><span class="sxs-lookup"><span data-stu-id="190d5-167">Keep learning</span></span>

<span data-ttu-id="190d5-168">Projektowanie modeli statystycznych jest własną umiejętnością.</span><span class="sxs-lookup"><span data-stu-id="190d5-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="190d5-169">Zespół ds. Cambridge Research firmy Microsoft zapisał [bezpłatną książkę online](http://mbmlbook.com/), która zapewnia łagodne wprowadzenie do artykułu.</span><span class="sxs-lookup"><span data-stu-id="190d5-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="190d5-170">Rozdział 3 tej książki dotyczy modelu TrueSkill w bardziej szczegółowy sposób.</span><span class="sxs-lookup"><span data-stu-id="190d5-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="190d5-171">Jeśli masz model, możesz przekształcić go w kod przy użyciu [obszernej dokumentacji](https://dotnet.github.io/infer/) w witrynie sieci Web Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="190d5-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="190d5-172">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="190d5-172">Next steps</span></span>

<span data-ttu-id="190d5-173">Zapoznaj się z repozytorium usługi GitHub Infer.NET, aby kontynuować uczenie i znaleźć więcej przykładów.</span><span class="sxs-lookup"><span data-stu-id="190d5-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="190d5-174">repozytorium GitHub/wnioskowanie</span><span class="sxs-lookup"><span data-stu-id="190d5-174">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
