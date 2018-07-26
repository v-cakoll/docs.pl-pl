---
title: 'Wprowadzenie do języka F # w programie Visual Studio Code'
description: 'Dowiedz się, jak używać języka F # za pomocą programu Visual Studio Code i Ionide zestawu wtyczki.'
ms.date: 05/28/2018
ms.openlocfilehash: 1afe985a4fe73d18b1e47b071b119c15a4672022
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874354"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="4cbb4-103">Wprowadzenie do języka F # w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4cbb4-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="4cbb4-104">Można napisać F # w [programu Visual Studio Code](https://code.visualstudio.com) z [wtyczki Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) uzyskać dla wielu platform, proste tworzenie środowiska IDE (Integrated) spełni za pomocą funkcji IntelliSense i podstawowego kodu operacje refaktoryzacji.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="4cbb4-105">Odwiedź stronę [Ionide.io](http://ionide.io) Aby dowiedzieć się więcej na temat dodatku plug-in.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="4cbb4-106">Aby rozpocząć, upewnij się, że [języka F # i poprawnie zainstalowaną wtyczką Ionide](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="4cbb4-107">Tworzenie pierwszego projektu za pomocą Ionide</span><span class="sxs-lookup"><span data-stu-id="4cbb4-107">Creating your first project with Ionide</span></span>

<span data-ttu-id="4cbb4-108">Aby utworzyć nowy projekt języka F #, Otwórz program Visual Studio Code w nowym folderze (można określić nazwę wedle uznania).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-108">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="4cbb4-109">Następnie otwórz pallette polecenia (**Widok > Pallette polecenia**) i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-109">Next, open the command pallette (**View > Command Pallette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="4cbb4-110">Jest to obsługiwane przez [FORGE](https://github.com/fsharp-editing/Forge) projektu.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-110">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
<span data-ttu-id="4cbb4-111">Jeśli nie widzisz opcji szablonów, Odśwież szablony, uruchamiając następujące polecenie w palecie poleceń: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-111">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="4cbb4-112">Wybierz pozycję "projektu języka F #: nowe", naciskając **Enter**.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-112">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="4cbb4-113">Spowoduje to przejście do następnego kroku, która jest przez wybranie szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-113">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="4cbb4-114">Wybierz `classlib` szablonu, a następnie wybierz pozycję **Enter**.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-114">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="4cbb4-115">Następnie wybierz katalog, aby utworzyć projekt w programie.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-115">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="4cbb4-116">Jeśli pole pozostanie puste, zostanie użyta bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-116">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="4cbb4-117">Na koniec nazwę projektu w ostatnim kroku.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-117">Finally, name your project in the final step.</span></span> <span data-ttu-id="4cbb4-118">F # stosuje [pisanymi wielkimi literami](http://c2.com/cgi/wiki?PascalCase) dotyczące nazw projektów.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-118">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="4cbb4-119">W tym artykule wykorzystano `ClassLibraryDemo` jako nazwę.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-119">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="4cbb4-120">Po wprowadzeniu nazwę dla projektu trafień **Enter**.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-120">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="4cbb4-121">Jeśli wykonano poprzedniego kroku, należy uzyskać Visual Studio Code obszaru roboczego po lewej stronie do pojawiają się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-121">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="4cbb4-122">F # sam projekt poniżej `ClassLibraryDemo` folderu.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-122">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="4cbb4-123">Trwa dodawanie pakietów przy użyciu struktury katalogu poprawny [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-123">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="4cbb4-124">Dla wielu platform, tworzenie skript [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-124">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="4cbb4-125">`paket.exe` Plik wykonywalny, który można pobrać pakiety i rozwiązywanie zależności.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-125">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="4cbb4-126">A `.gitignore` plik, jeśli chcesz dodać ten projekt do kontroli źródła opartych o Git.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-126">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="4cbb4-127">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="4cbb4-127">Writing some code</span></span>

<span data-ttu-id="4cbb4-128">Otwórz *ClassLibraryDemo* folderu.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-128">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="4cbb4-129">Powinny zostać wyświetlone następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-129">You should see the following files:</span></span>

1. <span data-ttu-id="4cbb4-130">`ClassLibraryDemo.fs`, pliku implementacji F # za pomocą klasy zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-130">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="4cbb4-131">`ClassLibraryDemo.fsproj`, F # plik projektu używany do tworzenia tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-131">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="4cbb4-132">`Script.fsx`, plik skryptu F #, umożliwiający załadowanie pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-132">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="4cbb4-133">`paket.references`, plik Paket, który określa zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-133">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="4cbb4-134">Otwórz `Script.fsx`i Dodaj następujący kod na końcu:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-134">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="4cbb4-135">Ta funkcja konwertuje słowo na formę [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-135">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="4cbb4-136">Następnym krokiem jest, aby ocenić ją przy użyciu języka F # Interactive (FSI).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-136">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="4cbb4-137">Zaznacz całą funkcję (powinno wskazywać 11 wierszy).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-137">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="4cbb4-138">Gdy jest wyróżniona, przytrzymaj **Alt** kluczy i kliknij przycisk **Enter**.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-138">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="4cbb4-139">Można zauważyć okno wyskakujące okienko poniżej, a powinna ona zostać wyświetlona mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-139">You'll notice a window pop up below, and it should show something like this:</span></span>

![Przykład danych wyjściowych Ionide F # Interactive](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="4cbb4-141">To wykonanie trzech czynności:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-141">This did three things:</span></span>

1. <span data-ttu-id="4cbb4-142">Proces FSI jego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-142">It started the FSI process.</span></span>
2. <span data-ttu-id="4cbb4-143">Kod, który zostanie wyróżniony go przesyłane za pośrednictwem procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-143">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="4cbb4-144">Proces FSI oceniane kod, który wysyłane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-144">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="4cbb4-145">Ponieważ był wysyłany za pośrednictwem [funkcja](../language-reference/functions/index.md), teraz można wywołać tę funkcję za pomocą FSI!</span><span class="sxs-lookup"><span data-stu-id="4cbb4-145">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="4cbb4-146">W oknie interaktywnym wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-146">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="4cbb4-147">Powinny zostać wyświetlone następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-147">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="4cbb4-148">Teraz Wypróbujmy się od samogłosek jako pierwszą literę.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-148">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="4cbb4-149">Wprowadź następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-149">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="4cbb4-150">Powinny zostać wyświetlone następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-150">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="4cbb4-151">Funkcja wydaje się działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-151">The function appears to be working as expected.</span></span> <span data-ttu-id="4cbb4-152">Gratulacje, właśnie napisał pierwszej funkcji F # w programie Visual Studio Code i oceniać je za pomocą FSI!</span><span class="sxs-lookup"><span data-stu-id="4cbb4-152">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="4cbb4-153">Jak być może zauważono, wiersze FSI kończą się za pomocą `;;`.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-153">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="4cbb4-154">Jest to spowodowane FSI pozwala wprowadzić wiele wierszy.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-154">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="4cbb4-155">`;;` Na końcu umożliwia FSI dowiedzieć się, gdy kod jest zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-155">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="4cbb4-156">Wyjaśniające, kod</span><span class="sxs-lookup"><span data-stu-id="4cbb4-156">Explaining the code</span></span>

<span data-ttu-id="4cbb4-157">Jeśli nie masz pewności, o jakie rzeczywiście jest zastosowanie danego kodu, poniżej przedstawiono instrukcje krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-157">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="4cbb4-158">Jak widać, `toPigLatin` jest funkcją, która przyjmuje word jako dane wejściowe i konwertuje ją na reprezentację w postaci Pig Latin tego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-158">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="4cbb4-159">Dostępne są następujące reguły, w tym:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-159">The rules for this are as follows:</span></span>

<span data-ttu-id="4cbb4-160">Jeśli pierwszy znak w wyraz rozpoczyna się od samogłosek, należy dodać "yay" do końca słowa.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-160">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="4cbb4-161">Jeśli go nie zaczyna się od samogłosek, Przenieś pierwszym znaku do końca słowa i "ay" Dodaj do niej.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-161">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="4cbb4-162">Być może zauważono FSI następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-162">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="4cbb4-163">Stanowi to, że `toPigLatin` jest funkcją, która przyjmuje `string` jako dane wejściowe (o nazwie `word`) i zwraca innego `string`.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-163">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="4cbb4-164">Jest to nazywane [sygnatura typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawowe fragment F #, który jest kluczem do zrozumienia kodzie języka F #.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-164">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="4cbb4-165">Należy także zauważyć, to po umieszczeniu wskaźnika myszy nad funkcji w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-165">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="4cbb4-166">W treści funkcji można zauważyć dwa oddzielne części:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-166">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="4cbb4-167">Wewnętrzna funkcja wywoływana `isVowel`, która określa, czy dany znak (`c`) jest samogłosek, sprawdzając, jeśli jest on zgodny z jednym z wzorców podanych za pośrednictwem [dopasowywania do wzorca](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="4cbb4-167">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="4cbb4-168">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Wyrażenie, które sprawdza, czy pierwszym znakiem jest samogłosek i konstrukcji, wartość zwracana z wprowadzonych znaków na podstawie jeśli pierwszym znakiem jest samogłosek, lub nie:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-168">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="4cbb4-169">Przepływ `toPigLatin` jest w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-169">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="4cbb4-170">Sprawdź, czy pierwszy znak wyrazu danych wejściowych jest samogłosek.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-170">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="4cbb4-171">Jeśli tak jest, należy dołączyć "yay" do końca słowa.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-171">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="4cbb4-172">W przeciwnym razie przenieść pierwszym znaku do końca słowa i "ay" Dodaj do niej.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-172">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="4cbb4-173">Istnieje jedno końcowe należy zwrócić uwagę na ten temat: jest nie jawnego instrukcji, zostać zwrócony przez funkcję, w przeciwieństwie do wielu innych języków tam.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-173">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="4cbb4-174">Jest to spowodowane F # to oparte na wyrażeniach i ostatniego wyrażenia w treści funkcji jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-174">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="4cbb4-175">Ponieważ `if..then..else` sama jest wyrażenie treści `then` bloku lub treści `else` blok zostanie zwrócona, w zależności od wartości wejściowej.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-175">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="4cbb4-176">Przenoszenie kodu skryptu w pliku implementacji</span><span class="sxs-lookup"><span data-stu-id="4cbb4-176">Moving your script code into the implementation file</span></span>

<span data-ttu-id="4cbb4-177">Poprzednie sekcje w tym artykule przedstawiono typowe, pierwszym krokiem w pisaniu kodu F #: pisanie funkcję początkową i wykonywania w interaktywnie przy użyciu FSI.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-177">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="4cbb4-178">Jest to nazywane projektowania opartego na REPL, gdzie [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) oznacza "Odczytu oceny — Drukuj pętlę".</span><span class="sxs-lookup"><span data-stu-id="4cbb4-178">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="4cbb4-179">Jest to doskonały sposób na wypróbowanie funkcji, aż do uzyskania elementu pracy.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-179">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="4cbb4-180">Następnym krokiem projektowania opartego na REPL jest przeniesienie działającego kodu do pliku implementacji F #.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-180">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="4cbb4-181">Go może następnie być kompilowane przez kompilator F # w zestawie, który może zostać wykonany.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-181">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="4cbb4-182">Aby rozpocząć, otwórz `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-182">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="4cbb4-183">Można zauważyć, że jakiś kod jest już istnieje.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-183">You'll notice that some code is already in there.</span></span> <span data-ttu-id="4cbb4-184">Przejdź dalej i usuń definicję klasy, ale pamiętaj pozostawić [ `namespace` ](../language-reference/namespaces.md) deklaracji u góry.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-184">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="4cbb4-185">Następnie utwórz nową [ `module` ](../language-reference/modules.md) o nazwie `PigLatin` i skopiuj `toPigLatin` funkcji do niego w związku z tym:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-185">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="4cbb4-186">Następnie otwórz `Script.fsx` ponownie plik, a następnie usuń całą `toPigLatin` działać, ale pamiętaj zapewnić następujące dwa wiersze w pliku:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-186">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="4cbb4-187">Pierwszy wiersz jest wymagany w przypadku skryptów można załadować FSI `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-187">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="4cbb4-188">Drugi wiersz jest wygoda: pomijając go jest opcjonalne, ale będzie trzeba wpisywać `open ClassLibraryDemo` w oknie FSI, jeśli chcesz wyświetlić `ToPigLatin` modułu do zakresu.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-188">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="4cbb4-189">Następnie w oknie FSI Wywołaj funkcję z `PigLatin` moduł, który wcześniej zdefiniowaną:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-189">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="4cbb4-190">SUKCES!</span><span class="sxs-lookup"><span data-stu-id="4cbb4-190">Success!</span></span> <span data-ttu-id="4cbb4-191">Możesz uzyskać te same wyniki przed, ale teraz załadowanego z pliku implementacji F #.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-191">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="4cbb4-192">W tym miejscu główna różnica polega na tym, że pliki źródłowe języka F # są kompilowane do zestawów, które mogą być wykonywane w dowolnym miejscu, nie tylko w FSI.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-192">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="4cbb4-193">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="4cbb4-193">Summary</span></span>

<span data-ttu-id="4cbb4-194">W tym artykule wyjaśniono:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-194">In this article, you've learned:</span></span>

1. <span data-ttu-id="4cbb4-195">Jak skonfigurować program Visual Studio Code za pomocą Ionide.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-195">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="4cbb4-196">Jak utworzyć swój pierwszy projekt F # za pomocą Ionide.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-196">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="4cbb4-197">Jak za pomocą skryptów języka F # pisania pierwszej funkcji F # w Ionide, a następnie uruchomić go w FSI.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-197">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="4cbb4-198">Jak przeprowadzić migrację skryptu kod źródłowy języka F #, a następnie wywołać kod z FSI.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-198">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="4cbb4-199">Teraz jest wyposażona w kodzie znacznie więcej F # za pomocą programu Visual Studio Code i Ionide.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-199">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="4cbb4-200">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="4cbb4-200">Troubleshooting</span></span>

<span data-ttu-id="4cbb4-201">Oto kilka sposobów, które można rozwiązać niektóre problemy, które możesz napotkać:</span><span class="sxs-lookup"><span data-stu-id="4cbb4-201">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="4cbb4-202">Aby uzyskać funkcji Ionide edycji kodu, pliki F # muszą zostać zapisane na dysku i wewnątrz folderu, która jest otwarta w obszarze roboczym programu Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-202">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="4cbb4-203">Jeśli zostały wprowadzone zmiany do systemu lub zainstalować wstępnie wymagane składniki Ionide za pomocą programu Visual Studio Code Otwórz, uruchom ponownie program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-203">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="4cbb4-204">Sprawdź, czy można użyć kompilatora języka F # i F # interactive z wiersza polecenia bez w pełni kwalifikowaną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-204">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="4cbb4-205">Możesz to zrobić, wpisując `fsc` w wierszu polecenia dla kompilatora F # i `fsi` lub `fsharpi` dla programu Visual F # narzędzia Windows i platformy Mono na Mac/Linux, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-205">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="4cbb4-206">Jeśli masz nieprawidłowe znaki w katalogach projektu Ionide mogą nie działać.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-206">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="4cbb4-207">Jeśli jest to możliwe, należy zmienić nazwy katalogów projektu.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-207">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="4cbb4-208">Brak polecenia Ionide pracy, sprawdź swoje [powiązania klawiszy programu Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) aby zobaczyć, jeśli masz zastępowania ich przypadkowo.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-208">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="4cbb4-209">Jeśli Ionide jest dzielony na komputerze, a żadne z powyższych poprawił problemu, spróbuj usunąć `ionide-fsharp` katalogu na komputerze i ponowne zainstalowanie pakietu wtyczki.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-209">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="4cbb4-210">Ionide to projekt typu open source wbudowane i obsługiwana przez członków społeczności pasjonatów języka F #.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-210">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="4cbb4-211">Należy zgłaszać problemy i możesz współtworzyć na [Ionide VSCode: repozytorium FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-211">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="4cbb4-212">Jeśli masz problem do raportu, wykonaj [instrukcje dotyczące pobierania dzienników do użycia podczas zgłoszenia problemu dotyczącego](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-212">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="4cbb4-213">Możesz również poprosić Aby uzyskać dalszą pomoc od deweloperów Ionide i społeczność pasjonatów języka F # w [kanału Ionide dotyczącym oprogramowania Gitter](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-213">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4cbb4-214">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4cbb4-214">Next steps</span></span>

<span data-ttu-id="4cbb4-215">Aby dowiedzieć się więcej na temat języka F # i funkcji języka, zapoznaj się z [samouczek programu F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-215">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
