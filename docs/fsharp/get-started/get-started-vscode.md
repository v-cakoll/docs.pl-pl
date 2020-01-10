---
title: Rozpoczynanie pracy z językiem F# w programie Visual Studio Code
description: Dowiedz się, F# jak używać programu z Visual Studio Code i pakietem wtyczek Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 91265303c2954387df0f500940c9af68b3c97dac
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559667"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="e4753-103">Rozpoczynanie pracy z językiem F# w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e4753-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="e4753-104">Możesz pisać F# w [Visual Studio Code](https://code.visualstudio.com) z [wtyczką Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) , aby uzyskać wspaniałe Międzyplatformowe, uproszczone zintegrowane środowisko programistyczne (IDE) korzystające z funkcji IntelliSense i refaktoryzacji kodu.</span><span class="sxs-lookup"><span data-stu-id="e4753-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span></span> <span data-ttu-id="e4753-105">Odwiedź stronę [Ionide.IO](http://ionide.io) , aby dowiedzieć się więcej na temat wtyczki.</span><span class="sxs-lookup"><span data-stu-id="e4753-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="e4753-106">Aby rozpocząć, upewnij się, że [ F# poprawnie zainstalowano wtyczkę Ionide](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="e4753-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="create-your-first-project-with-ionide"></a><span data-ttu-id="e4753-107">Tworzenie pierwszego projektu przy użyciu Ionide</span><span class="sxs-lookup"><span data-stu-id="e4753-107">Create your first project with Ionide</span></span>

<span data-ttu-id="e4753-108">Aby utworzyć nowy F# projekt, Otwórz wiersz polecenia i Utwórz nowy projekt z interfejs wiersza polecenia platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="e4753-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span></span>

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

<span data-ttu-id="e4753-109">Po jego zakończeniu Zmień katalog na projekt i otwórz Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="e4753-109">Once it completes, change directory to the project and open Visual Studio Code:</span></span>

```console
cd FirstIonideProject
code .
```

<span data-ttu-id="e4753-110">Po załadowaniu projektu na Visual Studio Code powinien zostać wyświetlony okienko F# Eksplorator rozwiązań po lewej stronie otwartego okna.</span><span class="sxs-lookup"><span data-stu-id="e4753-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span></span> <span data-ttu-id="e4753-111">Oznacza to, że Ionide pomyślnie załadował projekt, który został właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="e4753-111">This means Ionide has successfully loaded the project you just created.</span></span> <span data-ttu-id="e4753-112">Możesz napisać kod w edytorze przed tym punktem w czasie, ale gdy tak się stanie, wszystko zakończyło ładowanie.</span><span class="sxs-lookup"><span data-stu-id="e4753-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span></span>

## <a name="configure-f-interactive"></a><span data-ttu-id="e4753-113">Konfiguruj F# interaktywny</span><span class="sxs-lookup"><span data-stu-id="e4753-113">Configure F# interactive</span></span>

<span data-ttu-id="e4753-114">Najpierw upewnij się, że obsługa skryptów .NET Core jest domyślnym środowiskiem tworzenia skryptów:</span><span class="sxs-lookup"><span data-stu-id="e4753-114">First, ensure that .NET Core scripting is your default scripting environment:</span></span>

1. <span data-ttu-id="e4753-115">Otwórz ustawienia Visual Studio Code ( **preferencje** > **kodu** > **ustawień**).</span><span class="sxs-lookup"><span data-stu-id="e4753-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span></span>
1. <span data-ttu-id="e4753-116">Wyszukaj  **F# skrypt**terminowy.</span><span class="sxs-lookup"><span data-stu-id="e4753-116">Search for the term **F# Script**.</span></span>
1. <span data-ttu-id="e4753-117">Kliknij pole wyboru, które mówi **FSharp: Użyj skryptów zestawu SDK**.</span><span class="sxs-lookup"><span data-stu-id="e4753-117">Click the checkbox that says **FSharp: use SDK scripts**.</span></span>

<span data-ttu-id="e4753-118">Jest to obecnie konieczne z powodu niektórych starszych zachowań w skryptach opartych na .NET Framework, które nie współpracują z obsługą skryptów .NET Core, a Ionide jest obecnie striving w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="e4753-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span></span> <span data-ttu-id="e4753-119">W przyszłości skrypty środowiska .NET Core staną się domyślne.</span><span class="sxs-lookup"><span data-stu-id="e4753-119">In the future, .NET Core scripting will become the default.</span></span>

### <a name="write-your-first-script"></a><span data-ttu-id="e4753-120">Napisz swój pierwszy skrypt</span><span class="sxs-lookup"><span data-stu-id="e4753-120">Write your first script</span></span>

<span data-ttu-id="e4753-121">Po skonfigurowaniu Visual Studio Code do korzystania ze skryptów .NET Core przejdź do widoku Eksplorator w Visual Studio Code i Utwórz nowy plik.</span><span class="sxs-lookup"><span data-stu-id="e4753-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span></span> <span data-ttu-id="e4753-122">Nadaj mu nazwę *MyFirstScript. FSX*.</span><span class="sxs-lookup"><span data-stu-id="e4753-122">Name it *MyFirstScript.fsx*.</span></span>

<span data-ttu-id="e4753-123">Teraz Dodaj do niego następujący kod:</span><span class="sxs-lookup"><span data-stu-id="e4753-123">Now add the following code to it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="e4753-124">Ta funkcja konwertuje wyraz na formę [surówki](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="e4753-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="e4753-125">Następnym krokiem jest oszacowanie go przy użyciu opcji F# Interactive (fsi).</span><span class="sxs-lookup"><span data-stu-id="e4753-125">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="e4753-126">Zaznacz całą funkcję (powinna być 11 wierszy).</span><span class="sxs-lookup"><span data-stu-id="e4753-126">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="e4753-127">Gdy zostanie on wyróżniony, przytrzymaj wciśnięty klawisz **Alt** i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="e4753-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="e4753-128">Zobaczysz okno terminalu w dolnej części ekranu i będzie wyglądać podobnie do tego:</span><span class="sxs-lookup"><span data-stu-id="e4753-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span></span>

![Przykład danych F# wyjściowych interaktywnych z Ionide](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="e4753-130">Było to trzy rzeczy:</span><span class="sxs-lookup"><span data-stu-id="e4753-130">This did three things:</span></span>

1. <span data-ttu-id="e4753-131">Uruchomiono proces FSI.</span><span class="sxs-lookup"><span data-stu-id="e4753-131">It started the FSI process.</span></span>
2. <span data-ttu-id="e4753-132">Wysłano kod wyróżniony w procesie FSI.</span><span class="sxs-lookup"><span data-stu-id="e4753-132">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="e4753-133">Proces FSI ocenia kod, który został wysłany.</span><span class="sxs-lookup"><span data-stu-id="e4753-133">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="e4753-134">Ponieważ wysłane przez Ciebie elementy były [funkcją](../language-reference/functions/index.md), można teraz wywołać tę funkcję za pomocą FSI!</span><span class="sxs-lookup"><span data-stu-id="e4753-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="e4753-135">W oknie interaktywnym wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e4753-135">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="e4753-136">Powinien zostać wyświetlony następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="e4753-136">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="e4753-137">Teraz Wypróbujmy samogłosy jako pierwszą literę.</span><span class="sxs-lookup"><span data-stu-id="e4753-137">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="e4753-138">Wprowadź następujące dane:</span><span class="sxs-lookup"><span data-stu-id="e4753-138">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="e4753-139">Powinien zostać wyświetlony następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="e4753-139">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="e4753-140">Funkcja wydaje się działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="e4753-140">The function appears to be working as expected.</span></span> <span data-ttu-id="e4753-141">Gratulacje, po prostu Zapisano pierwszą F# funkcję w Visual Studio Code i oceniamy ją za pomocą FSI!</span><span class="sxs-lookup"><span data-stu-id="e4753-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="e4753-142">Jak zauważono, wiersze w FSI kończą się `;;`.</span><span class="sxs-lookup"><span data-stu-id="e4753-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="e4753-143">Dzieje się tak, ponieważ FSI umożliwia wprowadzanie wielu wierszy.</span><span class="sxs-lookup"><span data-stu-id="e4753-143">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="e4753-144">`;;` na końcu umożliwia FSI, gdy kod zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="e4753-144">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="e4753-145">Objaśnienie kodu</span><span class="sxs-lookup"><span data-stu-id="e4753-145">Explaining the code</span></span>

<span data-ttu-id="e4753-146">Jeśli nie masz pewności, co robi kod w rzeczywistości, wykonaj instrukcje krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="e4753-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="e4753-147">Jak widać, `toPigLatin` jest funkcją, która przyjmuje słowo jako dane wejściowe i konwertuje ją na reprezentację w formacie wieprzowiny.</span><span class="sxs-lookup"><span data-stu-id="e4753-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="e4753-148">Te reguły są następujące:</span><span class="sxs-lookup"><span data-stu-id="e4753-148">The rules for this are as follows:</span></span>

<span data-ttu-id="e4753-149">Jeśli pierwszy znak w wyrazie zaczyna się od samogłosek, Dodaj "Yay" do końca wyrazu.</span><span class="sxs-lookup"><span data-stu-id="e4753-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="e4753-150">Jeśli nie zaczyna się od samogłosek, Przenieś ten pierwszy znak na koniec wyrazu i Dodaj do niego wartość "AY".</span><span class="sxs-lookup"><span data-stu-id="e4753-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="e4753-151">W FSI mogły być zauważone następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="e4753-151">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="e4753-152">To Stany, które `toPigLatin` to funkcja, która przyjmuje `string` jako dane wejściowe (nazywane `word`) i zwraca kolejną `string`.</span><span class="sxs-lookup"><span data-stu-id="e4753-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="e4753-153">Jest to nazywane [sygnaturą typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawową częścią F# tego klucza do poznania F# kodu.</span><span class="sxs-lookup"><span data-stu-id="e4753-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="e4753-154">Zauważmy również, że po umieszczeniu wskaźnika myszy nad funkcją w Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e4753-154">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="e4753-155">W treści funkcji widoczne są dwie odrębne części:</span><span class="sxs-lookup"><span data-stu-id="e4753-155">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="e4753-156">Funkcja wewnętrzna o nazwie `isVowel`, która określa, czy dany znak (`c`) jest odgłosami przez sprawdzenie, czy pasuje do jednego z podanych wzorców przez [dopasowanie wzorca](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="e4753-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="e4753-157">Wyrażenie [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) , które sprawdza, czy pierwszy znak jest samodzielny i konstruuje zwracaną wartość z znaków wejściowych w oparciu o to, czy pierwszy znak był samogłosek lub nie:</span><span class="sxs-lookup"><span data-stu-id="e4753-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="e4753-158">Przepływ `toPigLatin` jest więc:</span><span class="sxs-lookup"><span data-stu-id="e4753-158">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="e4753-159">Sprawdź, czy pierwszy znak wyrazu wejściowego to samogłoski.</span><span class="sxs-lookup"><span data-stu-id="e4753-159">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="e4753-160">Jeśli tak, Dołącz "Yay" do końca wyrazu.</span><span class="sxs-lookup"><span data-stu-id="e4753-160">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="e4753-161">W przeciwnym razie Przenieś ten pierwszy znak na koniec wyrazu i Dodaj do niego wartość "AY".</span><span class="sxs-lookup"><span data-stu-id="e4753-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="e4753-162">Należy zwrócić uwagę na to, że nie ma żadnej bezpośredniej instrukcji zwracanej z funkcji, w przeciwieństwie do wielu innych języków.</span><span class="sxs-lookup"><span data-stu-id="e4753-162">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="e4753-163">Wynika to z F# faktu, że jest oparte na wyrażeniach, a ostatnie wyrażenie w treści funkcji jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="e4753-163">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="e4753-164">Ponieważ `if..then..else` jest samym wyrażeniem, treść bloku `then` lub treść bloku `else` zostanie zwrócona w zależności od wartości wejściowej.</span><span class="sxs-lookup"><span data-stu-id="e4753-164">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a><span data-ttu-id="e4753-165">Przekształcanie aplikacji konsolowej w generator łaciński</span><span class="sxs-lookup"><span data-stu-id="e4753-165">Turn the console app into a Pig Latin generator</span></span>

<span data-ttu-id="e4753-166">W poprzednich sekcjach tego artykułu przedstawiono typowy pierwszy krok podczas pisania F# kodu: pisanie początkowej funkcji i wykonywanie jej interaktywnie przy użyciu FSI.</span><span class="sxs-lookup"><span data-stu-id="e4753-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="e4753-167">Jest to nazywane programowaniem opartym na REPL, gdzie [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) to "Read-Szacuj-Print pętl".</span><span class="sxs-lookup"><span data-stu-id="e4753-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="e4753-168">Jest to doskonały sposób na eksperymentowanie z funkcjami do momentu, w którym będzie działać.</span><span class="sxs-lookup"><span data-stu-id="e4753-168">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="e4753-169">Następnym krokiem w programowaniu opartym na REPL polega na przeniesieniu kodu roboczego F# do pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="e4753-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="e4753-170">Może zostać następnie skompilowany przez F# kompilator do zestawu, który może być wykonywany.</span><span class="sxs-lookup"><span data-stu-id="e4753-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="e4753-171">Aby rozpocząć, Otwórz plik *program. FS* , który został utworzony wcześniej przy użyciu interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4753-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span></span> <span data-ttu-id="e4753-172">Zauważysz, że jakiś kod już istnieje.</span><span class="sxs-lookup"><span data-stu-id="e4753-172">You'll notice that some code is already in there.</span></span>

<span data-ttu-id="e4753-173">Następnie utwórz nową [`module`](../language-reference/modules.md) o nazwie `PigLatin` i skopiuj wcześniej utworzoną funkcję `toPigLatin` w taki sposób, aby:</span><span class="sxs-lookup"><span data-stu-id="e4753-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

<span data-ttu-id="e4753-174">Ten moduł powinien znajdować się powyżej funkcji `main` i poniżej deklaracji `open System`.</span><span class="sxs-lookup"><span data-stu-id="e4753-174">This module should be above the `main` function and below the `open System` declaration.</span></span> <span data-ttu-id="e4753-175">Porządek deklaracji w F#, dlatego należy zdefiniować funkcję przed wywołaniem jej w pliku.</span><span class="sxs-lookup"><span data-stu-id="e4753-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span></span>

<span data-ttu-id="e4753-176">Teraz w funkcji `main` wywołaj funkcję generatora w postaci trzody chlewnej na argumenty:</span><span class="sxs-lookup"><span data-stu-id="e4753-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span></span>

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

<span data-ttu-id="e4753-177">Teraz możesz uruchomić aplikację konsolową z poziomu wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="e4753-177">Now you can run your console app from the command line:</span></span>

```dotnetcli
dotnet run apple banana
```

<span data-ttu-id="e4753-178">Zobaczysz, że ten sam wynik będzie taki sam jak plik skryptu, ale ten czas jest uruchomionym programem.</span><span class="sxs-lookup"><span data-stu-id="e4753-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span></span>

## <a name="troubleshooting-ionide"></a><span data-ttu-id="e4753-179">Rozwiązywanie problemów z Ionide</span><span class="sxs-lookup"><span data-stu-id="e4753-179">Troubleshooting Ionide</span></span>

<span data-ttu-id="e4753-180">Poniżej przedstawiono kilka sposobów rozwiązywania niektórych problemów, które mogą być wykonywane w programie:</span><span class="sxs-lookup"><span data-stu-id="e4753-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="e4753-181">Aby uzyskać funkcje edytowania kodu Ionide, należy zapisać F# pliki na dysku i w folderze, który jest otwarty w obszarze roboczym Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e4753-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
1. <span data-ttu-id="e4753-182">Jeśli wprowadzono zmiany w systemie lub zainstalowano wymagania wstępne Ionide z Visual Studio Code Otwórz, uruchom ponownie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e4753-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
1. <span data-ttu-id="e4753-183">Jeśli w katalogach projektu znajdują się nieprawidłowe znaki, Ionide może nie zadziałał.</span><span class="sxs-lookup"><span data-stu-id="e4753-183">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="e4753-184">W takim przypadku Zmień nazwy katalogów projektu.</span><span class="sxs-lookup"><span data-stu-id="e4753-184">Rename your project directories if this is the case.</span></span>
1. <span data-ttu-id="e4753-185">Jeśli żaden z poleceń Ionide nie działa, sprawdź [powiązania klucza Visual Studio Code](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) , aby sprawdzić, czy są one zastępowane.</span><span class="sxs-lookup"><span data-stu-id="e4753-185">If none of the Ionide commands are working, check your [Visual Studio Code Key Bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) to see if you're overriding them by accident.</span></span>
1. <span data-ttu-id="e4753-186">Jeśli Ionide jest przerwany na komputerze, a żaden z powyższych elementów nie rozwiązał problemu, spróbuj usunąć katalog `ionide-fsharp` na maszynie i ponownie zainstalować pakiet wtyczek.</span><span class="sxs-lookup"><span data-stu-id="e4753-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>
1. <span data-ttu-id="e4753-187">Jeśli nie można załadować projektu ( F# Eksplorator rozwiązań będzie on widoczny), kliknij prawym przyciskiem myszy projekt i kliknij pozycję **Wyświetl szczegóły** , aby uzyskać więcej informacji diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="e4753-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span></span>

<span data-ttu-id="e4753-188">Ionide to projekt typu "open source" skompilowany i obsługiwany przez członków F# społeczności.</span><span class="sxs-lookup"><span data-stu-id="e4753-188">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="e4753-189">Zgłoś problemy i śmiało, aby współtworzyć w [repozytorium GitHub ionide-programu vscode-FSharp](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="e4753-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="e4753-190">Możesz również poszukać dalszej pomocy od deweloperów Ionide i F# społeczności w [kanale warunkom Ionide](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="e4753-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e4753-191">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e4753-191">Next steps</span></span>

<span data-ttu-id="e4753-192">Aby dowiedzieć się F# więcej na temat funkcji języka, zobacz [Przewodnik F# ](../tour.md)po stronie.</span><span class="sxs-lookup"><span data-stu-id="e4753-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
