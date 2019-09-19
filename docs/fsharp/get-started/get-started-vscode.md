---
title: Rozpoczynanie pracy F# z usługą w Visual Studio Code
description: Dowiedz się, F# jak używać programu z Visual Studio Code i pakietem wtyczek Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082990"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="25dd6-103">Rozpoczynanie pracy F# z usługą w Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="25dd6-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="25dd6-104">Możesz pisać F# w [Visual Studio Code](https://code.visualstudio.com) z [wtyczką Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) , aby uzyskać wspaniałe Międzyplatformowe, uproszczone zintegrowane środowisko programistyczne (IDE) z technologią IntelliSense i podstawowymi refaktoryzacjami kodu.</span><span class="sxs-lookup"><span data-stu-id="25dd6-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="25dd6-105">Odwiedź stronę [Ionide.IO](http://ionide.io) , aby dowiedzieć się więcej na temat wtyczki.</span><span class="sxs-lookup"><span data-stu-id="25dd6-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="25dd6-106">Aby rozpocząć, upewnij się, że [ F# poprawnie zainstalowano wtyczkę Ionide](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="25dd6-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

> [!NOTE]
> <span data-ttu-id="25dd6-107">Ionide będzie generować projekty F# .NET Framework, a nie rdzeń dotnet, które mogą mieć problemy ze zgodnością między platformami.</span><span class="sxs-lookup"><span data-stu-id="25dd6-107">Ionide will generate .NET Framework F# projects, not dotnet core, which can have cross-platform compatibility issues.</span></span> <span data-ttu-id="25dd6-108">Jeśli pracujesz w systemie **Linux** lub **OSX**, prostszym sposobem na rozpoczęcie pracy jest użycie [narzędzi wiersza polecenia](get-started-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="25dd6-108">If you are running on **Linux** or **OSX**, a simpler way to get started is to use the [command-line tools](get-started-command-line.md).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="25dd6-109">Tworzenie pierwszego projektu przy użyciu Ionide</span><span class="sxs-lookup"><span data-stu-id="25dd6-109">Creating your first project with Ionide</span></span>

<span data-ttu-id="25dd6-110">Aby utworzyć nowy F# projekt, otwórz Visual Studio Code w nowym folderze (można go nazwać w dowolny sposób).</span><span class="sxs-lookup"><span data-stu-id="25dd6-110">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="25dd6-111">Następnie Otwórz paletę poleceń (**wyświetl > palecie poleceń**) i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="25dd6-111">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```console
> F# new project
```

<span data-ttu-id="25dd6-112">Jest to obsługiwane przez projekt [podrabiania](https://github.com/fsharp-editing/Forge) .</span><span class="sxs-lookup"><span data-stu-id="25dd6-112">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
> <span data-ttu-id="25dd6-113">Jeśli nie widzisz opcji szablonu, spróbuj odświeżyć szablony, uruchamiając następujące polecenie w palecie poleceń `>F#: Refresh Project Templates`:.</span><span class="sxs-lookup"><span data-stu-id="25dd6-113">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="25dd6-114">Wybierz pozycjęF#": Nowy projekt "przez naciśnięcie **klawisza ENTER**.</span><span class="sxs-lookup"><span data-stu-id="25dd6-114">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="25dd6-115">Spowoduje to przejście do następnego kroku, który służy do wybierania szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="25dd6-115">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="25dd6-116">Wybierz szablon i naciśnij klawisz **Enter.** `classlib`</span><span class="sxs-lookup"><span data-stu-id="25dd6-116">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="25dd6-117">Następnie wybierz katalog, w którym zostanie utworzony projekt.</span><span class="sxs-lookup"><span data-stu-id="25dd6-117">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="25dd6-118">Jeśli pozostawisz to pole puste, zostanie użyty bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="25dd6-118">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="25dd6-119">Na koniec Nadaj projektowi nazwę w ostatnim kroku.</span><span class="sxs-lookup"><span data-stu-id="25dd6-119">Finally, name your project in the final step.</span></span> <span data-ttu-id="25dd6-120">F#używa [przypadku języka Pascal](http://c2.com/cgi/wiki?PascalCase) dla nazw projektów.</span><span class="sxs-lookup"><span data-stu-id="25dd6-120">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="25dd6-121">W tym artykule `ClassLibraryDemo` jest stosowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="25dd6-121">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="25dd6-122">Po wprowadzeniu nazwy dla projektu naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="25dd6-122">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="25dd6-123">Jeśli wykonano poprzedni krok, należy uzyskać obszar roboczy Visual Studio Code po lewej stronie, aby wyświetlić następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="25dd6-123">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="25dd6-124">Sam F# projekt, poniżej `ClassLibraryDemo` folderu.</span><span class="sxs-lookup"><span data-stu-id="25dd6-124">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="25dd6-125">Poprawna struktura katalogów służąca do [`Paket`](https://fsprojects.github.io/Paket/)dodawania pakietów za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="25dd6-125">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="25dd6-126">Międzyplatformowy skrypt kompilacji z [`FAKE`](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="25dd6-126">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="25dd6-127">`paket.exe` Plik wykonywalny, który może pobierać pakiety i rozwiązywać zależności.</span><span class="sxs-lookup"><span data-stu-id="25dd6-127">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="25dd6-128">Plik `.gitignore` , jeśli chcesz dodać ten projekt do kontroli źródła opartej na git.</span><span class="sxs-lookup"><span data-stu-id="25dd6-128">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="25dd6-129">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="25dd6-129">Writing some code</span></span>

<span data-ttu-id="25dd6-130">Otwórz folder *ClassLibraryDemo* .</span><span class="sxs-lookup"><span data-stu-id="25dd6-130">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="25dd6-131">Powinny zostać wyświetlone następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="25dd6-131">You should see the following files:</span></span>

1. <span data-ttu-id="25dd6-132">`ClassLibraryDemo.fs`, plik F# implementacji z zdefiniowaną klasą.</span><span class="sxs-lookup"><span data-stu-id="25dd6-132">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="25dd6-133">`ClassLibraryDemo.fsproj`, plik F# projektu używany do kompilowania tego projektu.</span><span class="sxs-lookup"><span data-stu-id="25dd6-133">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="25dd6-134">`Script.fsx`, plik F# skryptu ładujący plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="25dd6-134">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="25dd6-135">`paket.references`, plik Paket, który określa zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="25dd6-135">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="25dd6-136">Otwórz `Script.fsx`i Dodaj następujący kod na końcu:</span><span class="sxs-lookup"><span data-stu-id="25dd6-136">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="25dd6-137">Ta funkcja konwertuje wyraz na formę [surówki](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="25dd6-137">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="25dd6-138">Następnym krokiem jest oszacowanie go przy użyciu opcji F# Interactive (fsi).</span><span class="sxs-lookup"><span data-stu-id="25dd6-138">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="25dd6-139">Zaznacz całą funkcję (powinna być 11 wierszy).</span><span class="sxs-lookup"><span data-stu-id="25dd6-139">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="25dd6-140">Gdy zostanie ono wyróżnione, przytrzymaj klawisz **Alt** i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="25dd6-140">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="25dd6-141">Zobaczysz okno podręczne poniżej i będzie ono wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="25dd6-141">You'll notice a window pop up below, and it should show something like this:</span></span>

![Przykład danych F# wyjściowych interaktywnych z Ionide](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="25dd6-143">Było to trzy rzeczy:</span><span class="sxs-lookup"><span data-stu-id="25dd6-143">This did three things:</span></span>

1. <span data-ttu-id="25dd6-144">Uruchomiono proces FSI.</span><span class="sxs-lookup"><span data-stu-id="25dd6-144">It started the FSI process.</span></span>
2. <span data-ttu-id="25dd6-145">Wysłano kod wyróżniony w procesie FSI.</span><span class="sxs-lookup"><span data-stu-id="25dd6-145">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="25dd6-146">Proces FSI ocenia kod, który został wysłany.</span><span class="sxs-lookup"><span data-stu-id="25dd6-146">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="25dd6-147">Ponieważ wysłane przez Ciebie elementy były [funkcją](../language-reference/functions/index.md), można teraz wywołać tę funkcję za pomocą FSI!</span><span class="sxs-lookup"><span data-stu-id="25dd6-147">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="25dd6-148">W oknie interaktywnym wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="25dd6-148">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="25dd6-149">Powinien zostać wyświetlony następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="25dd6-149">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="25dd6-150">Teraz Wypróbujmy samogłosy jako pierwszą literę.</span><span class="sxs-lookup"><span data-stu-id="25dd6-150">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="25dd6-151">Wprowadź następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="25dd6-151">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="25dd6-152">Powinien zostać wyświetlony następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="25dd6-152">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="25dd6-153">Funkcja wydaje się działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="25dd6-153">The function appears to be working as expected.</span></span> <span data-ttu-id="25dd6-154">Gratulacje, po prostu Zapisano pierwszą F# funkcję w Visual Studio Code i oceniamy ją za pomocą FSI!</span><span class="sxs-lookup"><span data-stu-id="25dd6-154">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="25dd6-155">Jak zauważono, wiersze w FSI są kończone z `;;`.</span><span class="sxs-lookup"><span data-stu-id="25dd6-155">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="25dd6-156">Dzieje się tak, ponieważ FSI umożliwia wprowadzanie wielu wierszy.</span><span class="sxs-lookup"><span data-stu-id="25dd6-156">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="25dd6-157">`;;` Na końcu FSI wie, kiedy kod został ukończony.</span><span class="sxs-lookup"><span data-stu-id="25dd6-157">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="25dd6-158">Objaśnienie kodu</span><span class="sxs-lookup"><span data-stu-id="25dd6-158">Explaining the code</span></span>

<span data-ttu-id="25dd6-159">Jeśli nie masz pewności, co robi kod w rzeczywistości, wykonaj instrukcje krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="25dd6-159">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="25dd6-160">Jak widać, `toPigLatin` to funkcja, która przyjmuje słowo jako dane wejściowe i konwertuje ją na reprezentację w postaci tuszowej.</span><span class="sxs-lookup"><span data-stu-id="25dd6-160">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="25dd6-161">Te reguły są następujące:</span><span class="sxs-lookup"><span data-stu-id="25dd6-161">The rules for this are as follows:</span></span>

<span data-ttu-id="25dd6-162">Jeśli pierwszy znak w wyrazie zaczyna się od samogłosek, Dodaj "Yay" do końca wyrazu.</span><span class="sxs-lookup"><span data-stu-id="25dd6-162">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="25dd6-163">Jeśli nie zaczyna się od samogłosek, Przenieś ten pierwszy znak na koniec wyrazu i Dodaj do niego wartość "AY".</span><span class="sxs-lookup"><span data-stu-id="25dd6-163">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="25dd6-164">W FSI mogły być zauważone następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="25dd6-164">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="25dd6-165">To Stany `toPigLatin` , które są funkcją, która przyjmuje `string` jako dane wejściowe (nazywane `word`) i zwraca inną `string`.</span><span class="sxs-lookup"><span data-stu-id="25dd6-165">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="25dd6-166">Jest to nazywane [sygnaturą typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawową częścią F# tego klucza do poznania F# kodu.</span><span class="sxs-lookup"><span data-stu-id="25dd6-166">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="25dd6-167">Zauważmy również, że po umieszczeniu wskaźnika myszy nad funkcją w Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="25dd6-167">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="25dd6-168">W treści funkcji widoczne są dwie odrębne części:</span><span class="sxs-lookup"><span data-stu-id="25dd6-168">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="25dd6-169">Wewnętrzna funkcja, wywołana `isVowel`, która określa, czy dany znak (`c`) jest wygłosami przez sprawdzenie, czy pasuje do jednego z dostarczonych wzorców przez [dopasowanie wzorca](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="25dd6-169">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="25dd6-170">[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) Wyrażenie, które sprawdza, czy pierwszy znak jest samogłosek i konstruuje zwracaną wartość z znaków wejściowych w oparciu o to, czy pierwszy znak był samogłosek lub nie:</span><span class="sxs-lookup"><span data-stu-id="25dd6-170">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="25dd6-171">Przepływ `toPigLatin` jest następujący:</span><span class="sxs-lookup"><span data-stu-id="25dd6-171">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="25dd6-172">Sprawdź, czy pierwszy znak wyrazu wejściowego to samogłoski.</span><span class="sxs-lookup"><span data-stu-id="25dd6-172">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="25dd6-173">Jeśli tak, Dołącz "Yay" do końca wyrazu.</span><span class="sxs-lookup"><span data-stu-id="25dd6-173">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="25dd6-174">W przeciwnym razie Przenieś ten pierwszy znak na koniec wyrazu i Dodaj do niego wartość "AY".</span><span class="sxs-lookup"><span data-stu-id="25dd6-174">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="25dd6-175">Należy zwrócić uwagę na to, że nie ma żadnej bezpośredniej instrukcji zwracanej z funkcji, w przeciwieństwie do wielu innych języków.</span><span class="sxs-lookup"><span data-stu-id="25dd6-175">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="25dd6-176">Wynika to z F# faktu, że jest oparte na wyrażeniach, a ostatnie wyrażenie w treści funkcji jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="25dd6-176">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="25dd6-177">Ponieważ `if..then..else` sama jest wyrażeniem, treść `then` bloku `else` lub treści bloku zostanie zwrócona w zależności od wartości wejściowej.</span><span class="sxs-lookup"><span data-stu-id="25dd6-177">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="25dd6-178">Przeniesienie kodu skryptu do pliku implementacji</span><span class="sxs-lookup"><span data-stu-id="25dd6-178">Moving your script code into the implementation file</span></span>

<span data-ttu-id="25dd6-179">W poprzednich sekcjach tego artykułu przedstawiono typowy pierwszy krok podczas pisania F# kodu: pisanie początkowej funkcji i wykonywanie jej interaktywnie przy użyciu FSI.</span><span class="sxs-lookup"><span data-stu-id="25dd6-179">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="25dd6-180">Jest to nazywane programowaniem opartym na REPL, gdzie [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) to "Read-Szacuj-Print pętl".</span><span class="sxs-lookup"><span data-stu-id="25dd6-180">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="25dd6-181">Jest to doskonały sposób na eksperymentowanie z funkcjami do momentu, w którym będzie działać.</span><span class="sxs-lookup"><span data-stu-id="25dd6-181">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="25dd6-182">Następnym krokiem w programowaniu opartym na REPL polega na przeniesieniu kodu roboczego F# do pliku implementacji.</span><span class="sxs-lookup"><span data-stu-id="25dd6-182">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="25dd6-183">Może zostać następnie skompilowany przez F# kompilator do zestawu, który może być wykonywany.</span><span class="sxs-lookup"><span data-stu-id="25dd6-183">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="25dd6-184">Aby rozpocząć, Otwórz `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="25dd6-184">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="25dd6-185">Zauważysz, że jakiś kod już istnieje.</span><span class="sxs-lookup"><span data-stu-id="25dd6-185">You'll notice that some code is already in there.</span></span> <span data-ttu-id="25dd6-186">Przejdź dalej i usuń definicję klasy, ale upewnij się, że [`namespace`](../language-reference/namespaces.md) deklaracja znajduje się u góry.</span><span class="sxs-lookup"><span data-stu-id="25dd6-186">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="25dd6-187">Następnie utwórz nową [`module`](../language-reference/modules.md) nazwę `PigLatin` i skopiuj `toPigLatin` funkcję do niej w taki sposób:</span><span class="sxs-lookup"><span data-stu-id="25dd6-187">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="25dd6-188">Następnie ponownie Otwórz `Script.fsx` plik i Usuń całą `toPigLatin` funkcję, ale pamiętaj, aby zachować następujące dwa wiersze w pliku:</span><span class="sxs-lookup"><span data-stu-id="25dd6-188">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="25dd6-189">Zaznacz oba wiersze tekstu i naciśnij klawisze ALT + ENTER, aby wykonać te wiersze w FSI.</span><span class="sxs-lookup"><span data-stu-id="25dd6-189">Select both lines of text and press Alt+Enter to execute these lines in FSI.</span></span> <span data-ttu-id="25dd6-190">Spowoduje to załadowanie zawartości biblioteki z wieprzowiny do procesu FSI i `open` `ClassLibraryDemo` przestrzeni nazw w celu uzyskania dostępu do funkcji.</span><span class="sxs-lookup"><span data-stu-id="25dd6-190">These will load the contents of the Pig Latin library into the FSI process and `open` the `ClassLibraryDemo` namespace so that you have access to the functionality.</span></span>

<span data-ttu-id="25dd6-191">Następnie w oknie FSI wywołaj funkcję przy użyciu `PigLatin` zdefiniowanego wcześniej modułu:</span><span class="sxs-lookup"><span data-stu-id="25dd6-191">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="25dd6-192">Prawnego!</span><span class="sxs-lookup"><span data-stu-id="25dd6-192">Success!</span></span> <span data-ttu-id="25dd6-193">Uzyskasz te same wyniki jak poprzednio, ale teraz załadowano je z pliku F# implementacji.</span><span class="sxs-lookup"><span data-stu-id="25dd6-193">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="25dd6-194">Istotną różnicą jest to F# , że pliki źródłowe są kompilowane do zestawów, które można wykonać w dowolnym miejscu, a nie tylko w FSI.</span><span class="sxs-lookup"><span data-stu-id="25dd6-194">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="25dd6-195">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="25dd6-195">Summary</span></span>

<span data-ttu-id="25dd6-196">W tym artykule przedstawiono następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="25dd6-196">In this article, you've learned:</span></span>

1. <span data-ttu-id="25dd6-197">Jak skonfigurować Visual Studio Code za pomocą Ionide.</span><span class="sxs-lookup"><span data-stu-id="25dd6-197">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="25dd6-198">Jak utworzyć swój pierwszy F# projekt przy użyciu Ionide.</span><span class="sxs-lookup"><span data-stu-id="25dd6-198">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="25dd6-199">Używanie F# skryptów do pisania pierwszej F# funkcji w Ionide, a następnie wykonywania jej w FSI.</span><span class="sxs-lookup"><span data-stu-id="25dd6-199">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="25dd6-200">Jak przeprowadzić migrację kodu skryptu do F# źródła, a następnie wywołać ten kod z FSI.</span><span class="sxs-lookup"><span data-stu-id="25dd6-200">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="25dd6-201">Teraz możesz napisać znacznie więcej F# kodu przy użyciu Visual Studio Code i Ionide.</span><span class="sxs-lookup"><span data-stu-id="25dd6-201">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="25dd6-202">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="25dd6-202">Troubleshooting</span></span>

<span data-ttu-id="25dd6-203">Poniżej przedstawiono kilka sposobów rozwiązywania niektórych problemów, które mogą być wykonywane w programie:</span><span class="sxs-lookup"><span data-stu-id="25dd6-203">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="25dd6-204">Aby uzyskać funkcje edytowania kodu Ionide, należy zapisać F# pliki na dysku i w folderze, który jest otwarty w obszarze roboczym Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="25dd6-204">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="25dd6-205">Jeśli wprowadzono zmiany w systemie lub zainstalowano wymagania wstępne Ionide z Visual Studio Code Otwórz, uruchom ponownie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="25dd6-205">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="25dd6-206">Sprawdź, czy można użyć F# kompilatora i F# interaktywnie z wiersza polecenia bez w pełni kwalifikowanej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="25dd6-206">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="25dd6-207">Można to zrobić `fsc` , wpisując w wierszu polecenia F# kompilatora `fsi` i lub `fsharpi` dla narzędzi wizualnych F# w systemach Windows i mono odpowiednio na komputerze Mac/Linux.</span><span class="sxs-lookup"><span data-stu-id="25dd6-207">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="25dd6-208">Jeśli w katalogach projektu znajdują się nieprawidłowe znaki, Ionide może nie zadziałał.</span><span class="sxs-lookup"><span data-stu-id="25dd6-208">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="25dd6-209">W takim przypadku Zmień nazwy katalogów projektu.</span><span class="sxs-lookup"><span data-stu-id="25dd6-209">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="25dd6-210">Jeśli żaden z poleceń Ionide nie działa, sprawdź powiązania klawiszy [Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) , aby sprawdzić, czy są one zastępowane przypadkowo.</span><span class="sxs-lookup"><span data-stu-id="25dd6-210">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="25dd6-211">Jeśli Ionide jest przerwany na komputerze, a żaden z powyższych elementów nie rozwiązał problemu, spróbuj usunąć `ionide-fsharp` katalog na maszynie i ponownie zainstalować pakiet wtyczek.</span><span class="sxs-lookup"><span data-stu-id="25dd6-211">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="25dd6-212">Ionide to projekt typu "open source" skompilowany i obsługiwany przez członków F# społeczności.</span><span class="sxs-lookup"><span data-stu-id="25dd6-212">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="25dd6-213">Zgłoś problemy i śmiało, aby współtworzyć [Ionide-programu vscode: FSharp repozytorium](https://github.com/ionide/ionide-vscode-fsharp)GitHub.</span><span class="sxs-lookup"><span data-stu-id="25dd6-213">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="25dd6-214">Jeśli masz problem z raportem, postępuj zgodnie [z instrukcjami dotyczącymi pobierania dzienników do użycia podczas zgłaszania problemu](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="25dd6-214">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="25dd6-215">Możesz również poszukać dalszej pomocy od deweloperów Ionide i F# społeczności w [kanale warunkom Ionide](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="25dd6-215">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="25dd6-216">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="25dd6-216">Next steps</span></span>

<span data-ttu-id="25dd6-217">Aby dowiedzieć się F# więcej na temat funkcji języka, zobacz [Przewodnik F# ](../tour.md)po stronie.</span><span class="sxs-lookup"><span data-stu-id="25dd6-217">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
