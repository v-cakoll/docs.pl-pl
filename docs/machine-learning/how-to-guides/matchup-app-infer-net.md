---
title: Tworzenie gier dopasowania listy aplikacji przy użyciu Infer.NET i Probabilistyczne programowania
description: Dowiedz się, jak za pomocą programowania Probabilistyczne Infer.NET utworzyć aplikację listy gier matchup oparty na uproszczonej wersji TrueSkill.
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 06538ec9de26f5aeabe474fbcae69f0a313c8d32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650301"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="7acbd-103">Tworzenie gier dopasowania listy aplikacji przy użyciu Infer.NET i Probabilistyczne programowania</span><span class="sxs-lookup"><span data-stu-id="7acbd-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

> [!NOTE]
> <span data-ttu-id="7acbd-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="7acbd-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="7acbd-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="7acbd-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="7acbd-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="7acbd-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="7acbd-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="7acbd-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="7acbd-108">Ten przewodnik zawiera informacje na temat prawdopodobieństwa programowania przy użyciu Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="7acbd-108">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="7acbd-109">Probabilistyczne programowania jest podejście machine learning, gdzie niestandardowe modele są wyrażane jako programów komputerowych.</span><span class="sxs-lookup"><span data-stu-id="7acbd-109">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="7acbd-110">Umożliwia zdobędziesz znajomość domeny w ramach modeli oraz sprawia, że system jest bardziej interpretowanej uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="7acbd-110">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="7acbd-111">Obsługuje ona również wnioskowania online — proces uczenia nadejściu nowych danych.</span><span class="sxs-lookup"><span data-stu-id="7acbd-111">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="7acbd-112">Infer.NET jest używana w różnych produktów w firmie Microsoft na platformie Azure, usługi Xbox i Bing.</span><span class="sxs-lookup"><span data-stu-id="7acbd-112">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="7acbd-113">Co to jest programowanie Probabilistyczne?</span><span class="sxs-lookup"><span data-stu-id="7acbd-113">What is probabilistic programming?</span></span>

<span data-ttu-id="7acbd-114">Probabilistyczne programowania służy do tworzenia modeli statystyczne rzeczywistych procesów.</span><span class="sxs-lookup"><span data-stu-id="7acbd-114">Probabilistic programming allows you to create statistical models of real-world processes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7acbd-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7acbd-115">Prerequisites</span></span>

- <span data-ttu-id="7acbd-116">Konfigurowanie środowiska deweloperskiego lokalne</span><span class="sxs-lookup"><span data-stu-id="7acbd-116">Local development environment setup</span></span>

  <span data-ttu-id="7acbd-117">Ten poradnik oczekuje, że będziesz mieć maszyny, których można użyć do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7acbd-117">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="7acbd-118">.NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) samouczek zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux.</span><span class="sxs-lookup"><span data-stu-id="7acbd-118">The .NET [Get Started in 10 minutes](https://www.microsoft.com/net/core) tutorial has instructions for setting up your local development environment on Mac, PC, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="7acbd-119">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7acbd-119">Create your app</span></span>

1. <span data-ttu-id="7acbd-120">Otwórz nowy wiersz polecenia i uruchom następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="7acbd-120">Open a new command prompt and run the following commands:</span></span>

```console
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="7acbd-121">`dotnet` Polecenie tworzy `new` aplikacji typu `console`.</span><span class="sxs-lookup"><span data-stu-id="7acbd-121">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="7acbd-122">`-o` Parametr tworzy katalog o nazwie `myApp` gdzie aplikacji są przechowywane i wypełnia je wymaganych plików.</span><span class="sxs-lookup"><span data-stu-id="7acbd-122">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="7acbd-123">`cd myApp` Polecenie zapisuje do katalogu nowo utworzoną aplikację.</span><span class="sxs-lookup"><span data-stu-id="7acbd-123">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="7acbd-124">Zainstaluj pakiet Infer.NET</span><span class="sxs-lookup"><span data-stu-id="7acbd-124">Install Infer.NET package</span></span>

<span data-ttu-id="7acbd-125">Aby użyć Infer.NET, musisz zainstalować `Microsoft.ML.Probabilistic.Compiler` pakietu.</span><span class="sxs-lookup"><span data-stu-id="7acbd-125">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="7acbd-126">W wierszu polecenia Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="7acbd-126">In your command prompt, run the following command:</span></span>

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="7acbd-127">Projektowanie modelu</span><span class="sxs-lookup"><span data-stu-id="7acbd-127">Design your model</span></span>

<span data-ttu-id="7acbd-128">W przykładzie przykładzie użyto tenisa tabeli lub dopasowania foosball odtwarzany w biurze.</span><span class="sxs-lookup"><span data-stu-id="7acbd-128">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="7acbd-129">Masz uczestników i wynik każdego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="7acbd-129">You have the participants and outcome of each match.</span></span>  <span data-ttu-id="7acbd-130">Chcesz wywnioskować gracza umiejętności z tych danych.</span><span class="sxs-lookup"><span data-stu-id="7acbd-130">You want to infer the player's skills from this data.</span></span> <span data-ttu-id="7acbd-131">Załóżmy, że każdy z graczy ma zwykle rozproszonych umiejętności ukryte, a ich wydajności danego dopasowanie jest hałas wersją tej umiejętności.</span><span class="sxs-lookup"><span data-stu-id="7acbd-131">Assume that each player has a normally distributed latent skill and their given match performance is a noisy version of this skill.</span></span> <span data-ttu-id="7acbd-132">Dane ogranicza wydajność zwycięzca powinien być większy niż pominiętych wskutek wydajności.</span><span class="sxs-lookup"><span data-stu-id="7acbd-132">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="7acbd-133">Jest to Uproszczona wersja popularnej [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) modelu, który również obsługuje zespołów, rysuje oraz inne rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="7acbd-133">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="7acbd-134">[Zaawansowanych wersji](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) ten model jest używana do matchmaking w najlepiej sprzedające tytuły gry Halo i Gears War.</span><span class="sxs-lookup"><span data-stu-id="7acbd-134">An [advanced version](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="7acbd-135">Należy listy zadań do umiejętności wywnioskowane player wraz z ich wariancji — miary niepewności wokół umiejętności.</span><span class="sxs-lookup"><span data-stu-id="7acbd-135">You need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="7acbd-136">*Wynik gier przykładowych danych*</span><span class="sxs-lookup"><span data-stu-id="7acbd-136">*Game result sample data*</span></span>

<span data-ttu-id="7acbd-137">Gra</span><span class="sxs-lookup"><span data-stu-id="7acbd-137">Game</span></span> |<span data-ttu-id="7acbd-138">Zwycięzcy</span><span class="sxs-lookup"><span data-stu-id="7acbd-138">Winner</span></span> | <span data-ttu-id="7acbd-139">Pominiętych wskutek</span><span class="sxs-lookup"><span data-stu-id="7acbd-139">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="7acbd-140">1</span><span class="sxs-lookup"><span data-stu-id="7acbd-140">1</span></span> | <span data-ttu-id="7acbd-141">Odtwarzacz 0</span><span class="sxs-lookup"><span data-stu-id="7acbd-141">Player 0</span></span> | <span data-ttu-id="7acbd-142">Odtwarzacz 1</span><span class="sxs-lookup"><span data-stu-id="7acbd-142">Player 1</span></span>
 <span data-ttu-id="7acbd-143">2</span><span class="sxs-lookup"><span data-stu-id="7acbd-143">2</span></span> | <span data-ttu-id="7acbd-144">Odtwarzacz 0</span><span class="sxs-lookup"><span data-stu-id="7acbd-144">Player 0</span></span> | <span data-ttu-id="7acbd-145">Odtwarzacz 3</span><span class="sxs-lookup"><span data-stu-id="7acbd-145">Player 3</span></span>
 <span data-ttu-id="7acbd-146">3</span><span class="sxs-lookup"><span data-stu-id="7acbd-146">3</span></span> | <span data-ttu-id="7acbd-147">Odtwarzacz 0</span><span class="sxs-lookup"><span data-stu-id="7acbd-147">Player 0</span></span> | <span data-ttu-id="7acbd-148">Player 4</span><span class="sxs-lookup"><span data-stu-id="7acbd-148">Player 4</span></span>
 <span data-ttu-id="7acbd-149">4</span><span class="sxs-lookup"><span data-stu-id="7acbd-149">4</span></span> | <span data-ttu-id="7acbd-150">Odtwarzacz 1</span><span class="sxs-lookup"><span data-stu-id="7acbd-150">Player 1</span></span> | <span data-ttu-id="7acbd-151">Odtwarzacz 2</span><span class="sxs-lookup"><span data-stu-id="7acbd-151">Player 2</span></span>
 <span data-ttu-id="7acbd-152">5</span><span class="sxs-lookup"><span data-stu-id="7acbd-152">5</span></span> | <span data-ttu-id="7acbd-153">Odtwarzacz 3</span><span class="sxs-lookup"><span data-stu-id="7acbd-153">Player 3</span></span> | <span data-ttu-id="7acbd-154">Odtwarzacz 1</span><span class="sxs-lookup"><span data-stu-id="7acbd-154">Player 1</span></span>
 <span data-ttu-id="7acbd-155">6</span><span class="sxs-lookup"><span data-stu-id="7acbd-155">6</span></span> | <span data-ttu-id="7acbd-156">Player 4</span><span class="sxs-lookup"><span data-stu-id="7acbd-156">Player 4</span></span> | <span data-ttu-id="7acbd-157">Odtwarzacz 2</span><span class="sxs-lookup"><span data-stu-id="7acbd-157">Player 2</span></span>

<span data-ttu-id="7acbd-158">Za pomocą bliższe spojrzenie na przykładowych danych zauważysz, że graczy, 3 i 4 mają jeden win i utraty jednej.</span><span class="sxs-lookup"><span data-stu-id="7acbd-158">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="7acbd-159">Zobaczmy, rankingi wygląd za pomocą programowania Probabilistyczne.</span><span class="sxs-lookup"><span data-stu-id="7acbd-159">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="7acbd-160">Zwróć uwagę, również ma odtwarzacz zero, ponieważ nawet office dopasowanie wykazów są zera nam deweloperów.</span><span class="sxs-lookup"><span data-stu-id="7acbd-160">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="7acbd-161">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="7acbd-161">Write some code</span></span>

<span data-ttu-id="7acbd-162">Posiadanie zaprojektowany modelu, warto Wyraź ją jako Probabilistyczne programu przy użyciu Infer.NET interfejsów API do modelowania.</span><span class="sxs-lookup"><span data-stu-id="7acbd-162">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="7acbd-163">Otwórz `Program.cs` w swoim ulubionym edytorze tekstów i Zastąp całą jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7acbd-163">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="7acbd-164">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7acbd-164">Run your app</span></span>

<span data-ttu-id="7acbd-165">W wierszu polecenia Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="7acbd-165">In your command prompt, run the following command:</span></span>

```console
dotnet run
```

## <a name="results"></a><span data-ttu-id="7acbd-166">Wyniki</span><span class="sxs-lookup"><span data-stu-id="7acbd-166">Results</span></span>

<span data-ttu-id="7acbd-167">Wyniki powinny wyglądać podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="7acbd-167">Your results should be similar to the following:</span></span>

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

<span data-ttu-id="7acbd-168">W wynikach Zwróć uwagę, że tego odtwarzacza 3 szereguje nieznacznie wyższe niż 4 graczy, zgodnie z naszym modelu.</span><span class="sxs-lookup"><span data-stu-id="7acbd-168">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="7acbd-169">To dlatego zwycięstwa odtwarzacza 3 za pośrednictwem gracz 1 jest większe znaczenie niż zwycięstwa odtwarzacza 4 za pośrednictwem player 2 — Uwaga tego odtwarzacza 1 uderzeń player 2.</span><span class="sxs-lookup"><span data-stu-id="7acbd-169">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="7acbd-170">Odtwarzacz 0 jest ogólny wyszukiwarek.</span><span class="sxs-lookup"><span data-stu-id="7acbd-170">Player 0 is the overall champ!</span></span>

## <a name="keep-learning"></a><span data-ttu-id="7acbd-171">Zachowaj nauki</span><span class="sxs-lookup"><span data-stu-id="7acbd-171">Keep learning</span></span>

<span data-ttu-id="7acbd-172">Projektowanie statystyczne modeli jest umiejętności samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="7acbd-172">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="7acbd-173">Zapisane przez zespół Microsoft Research Cambridge [bezpłatnej książki online](http://mbmlbook.com/), co daje delikatnie wprowadzenie w artykule.</span><span class="sxs-lookup"><span data-stu-id="7acbd-173">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="7acbd-174">Rozdział 3 tę książkę omówiono bardziej szczegółowo model TrueSkill.</span><span class="sxs-lookup"><span data-stu-id="7acbd-174">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="7acbd-175">Po utworzeniu modelu należy pamiętać, można przekształcić go do kodu za pomocą [obszerną dokumentację](https://dotnet.github.io/infer/) w witrynie sieci Web Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="7acbd-175">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7acbd-176">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7acbd-176">Next steps</span></span>

<span data-ttu-id="7acbd-177">Zapoznaj się z repozytorium Infer.NET GitHub, aby kontynuować zapoznawanie się z i znaleźć więcej przykładów.</span><span class="sxs-lookup"><span data-stu-id="7acbd-177">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7acbd-178">polecenia DotNet/wywnioskować repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="7acbd-178">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
