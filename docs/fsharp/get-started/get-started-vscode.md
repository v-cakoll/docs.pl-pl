---
title: 'Rozpoczynanie pracy z F # w kodzie programu Visual Studio'
description: 'Dowiedz się, jak używanie F # za pomocą programu Visual Studio Code i Ionide suite wtyczki.'
ms.date: 05/28/2018
ms.openlocfilehash: e56274caf36be231338876ded5a6d7c7968906b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728631"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="35aaa-103">Rozpoczynanie pracy z F # w kodzie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="35aaa-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="35aaa-104">Możesz pisać F # [Visual Studio Code](https://code.visualstudio.com) z [wtyczki Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)w celu uzyskania maksymalnego komfortu obsługi zintegrowane środowisko rozwoju (IDE) i platform, lekkie IntelliSense i podstawowe kodu refaktoryzacje.</span><span class="sxs-lookup"><span data-stu-id="35aaa-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="35aaa-105">Odwiedź stronę [Ionide.io](http://ionide.io) Aby dowiedzieć się więcej o pakiecie wtyczki.</span><span class="sxs-lookup"><span data-stu-id="35aaa-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="35aaa-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="35aaa-106">Prerequisites</span></span>

<span data-ttu-id="35aaa-107">Musi mieć [git zainstalowane](https://git-scm.com/download) i znajduje się na ŚCIEŻCE, aby użyć szablonów projektu w Ionide.</span><span class="sxs-lookup"><span data-stu-id="35aaa-107">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span> <span data-ttu-id="35aaa-108">Można sprawdzić, czy jest poprawnie zainstalowany, wpisując `git --version` w wierszu polecenia i naciskając klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="35aaa-108">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="35aaa-109">macOS</span><span class="sxs-lookup"><span data-stu-id="35aaa-109">macOS</span></span>](#tab/macos)

<span data-ttu-id="35aaa-110">Używa Ionide [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="35aaa-110">Ionide uses [Mono](http://www.mono-project.com).</span></span> <span data-ttu-id="35aaa-111">Najprostszym sposobem zainstalowania Mono na macOS odbywa się za pośrednictwem oprogramowania Homebrew.</span><span class="sxs-lookup"><span data-stu-id="35aaa-111">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="35aaa-112">W terminalu, po prostu wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="35aaa-112">Simply type the following into your terminal:</span></span>

```
brew install mono
```

<span data-ttu-id="35aaa-113">Należy również zainstalować [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="35aaa-113">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="35aaa-114">Linux</span><span class="sxs-lookup"><span data-stu-id="35aaa-114">Linux</span></span>](#tab/linux)

<span data-ttu-id="35aaa-115">W systemie Linux, używa również Ionide [Mono](https://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="35aaa-115">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="35aaa-116">Jeśli używasz Debian i Ubuntu, można użyć następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="35aaa-116">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="35aaa-117">Należy również zainstalować [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="35aaa-117">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="35aaa-118">Windows</span><span class="sxs-lookup"><span data-stu-id="35aaa-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="35aaa-119">Jeśli w systemie Windows, należy najpierw [zainstalować program Visual Studio z obsługą F #](get-started-visual-studio.md#installing-f).</span><span class="sxs-lookup"><span data-stu-id="35aaa-119">If you're on Windows, you must [install Visual Studio with F# support](get-started-visual-studio.md#installing-f).</span></span> <span data-ttu-id="35aaa-120">Spowoduje to zainstalowanie wszystkich składników niezbędnych do zapisu, kompilowania i wykonywania kodzie języka F #.</span><span class="sxs-lookup"><span data-stu-id="35aaa-120">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="35aaa-121">Należy również zainstalować [.NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="35aaa-121">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="35aaa-122">Instalowanie dodatku Ionide i Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="35aaa-122">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="35aaa-123">Można zainstalować program Visual Studio Code z [code.visualstudio.com](https://code.visualstudio.com) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="35aaa-123">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>

<span data-ttu-id="35aaa-124">Następnie kliknij ikonę rozszerzenia i wyszukaj "Ionide":</span><span class="sxs-lookup"><span data-stu-id="35aaa-124">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="35aaa-125">Tylko wtyczki, wymagana jest obsługa F # w programie Visual Studio Code [języka fsharp Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="35aaa-125">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="35aaa-126">Jednakże można także zainstalować [SFAŁSZOWANA Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) uzyskanie [SFAŁSZOWAĆ](https://fsharp.github.io/FAKE/) obsługuje i [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) można pobrać [Paket](https://fsprojects.github.io/Paket/) obsługuje.</span><span class="sxs-lookup"><span data-stu-id="35aaa-126">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="35aaa-127">FAŁSZYWE i Paket są dodatkowe narzędzia społeczności F # do tworzenia projektów i zarządzanie zależności, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="35aaa-127">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="35aaa-128">Tworzenie pierwszego projektu z Ionide</span><span class="sxs-lookup"><span data-stu-id="35aaa-128">Creating your first project with Ionide</span></span>

<span data-ttu-id="35aaa-129">Aby utworzyć nowy projekt F #, Otwórz program Visual Studio Code w nowym folderze (można określić nazwę dowolne).</span><span class="sxs-lookup"><span data-stu-id="35aaa-129">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="35aaa-130">Następnie otwórz folder pallette polecenia (**Widok > Pallette polecenia**) i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="35aaa-130">Next, open the command pallette (**View > Command Pallette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="35aaa-131">Jest to obsługiwane przez [FORGE](https://github.com/fsharp-editing/Forge) projektu.</span><span class="sxs-lookup"><span data-stu-id="35aaa-131">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
<span data-ttu-id="35aaa-132">Jeśli nie widzisz opcji szablonu, spróbuj odświeżyć szablony, uruchamiając następujące polecenie w palecie polecenia: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="35aaa-132">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="35aaa-133">Wybierz opcję "F #: nowego projektu" za pomocą **Enter**.</span><span class="sxs-lookup"><span data-stu-id="35aaa-133">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="35aaa-134">Powoduje to przejście do następnego kroku, czyli wybierania szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="35aaa-134">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="35aaa-135">Wybierz `classlib` szablonu i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="35aaa-135">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="35aaa-136">Następnie wybierz katalog do tworzenia projektu w.</span><span class="sxs-lookup"><span data-stu-id="35aaa-136">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="35aaa-137">Jeśli pole pozostanie puste, używa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="35aaa-137">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="35aaa-138">Na koniec nazwy projektu w ostatnim kroku.</span><span class="sxs-lookup"><span data-stu-id="35aaa-138">Finally, name your project in the final step.</span></span> <span data-ttu-id="35aaa-139">F # używa [przypadku Pascal](http://c2.com/cgi/wiki?PascalCase) dla nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="35aaa-139">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="35aaa-140">W tym artykule wykorzystano `ClassLibraryDemo` jako nazwy.</span><span class="sxs-lookup"><span data-stu-id="35aaa-140">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="35aaa-141">Po wprowadzeniu nazwy dla projektu, kliknij przycisk **Enter**.</span><span class="sxs-lookup"><span data-stu-id="35aaa-141">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="35aaa-142">Po wykonaniu poprzedniego kroku, należy pobrać Visual Studio kod obszaru roboczego po lewej stronie się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="35aaa-142">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="35aaa-143">F # projektu, underneath `ClassLibraryDemo` folderu.</span><span class="sxs-lookup"><span data-stu-id="35aaa-143">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="35aaa-144">Dodawanie pakietów za pomocą struktury poprawny katalog [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="35aaa-144">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="35aaa-145">Obsługujący wiele platform kompilacji skryptu o [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="35aaa-145">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="35aaa-146">`paket.exe` Pliku wykonywalnego, który można pobrać pakietów i rozpoznać zależności dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="35aaa-146">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="35aaa-147">A `.gitignore` plik, jeśli chcesz dodać ten projekt do kontroli źródła na podstawie Git.</span><span class="sxs-lookup"><span data-stu-id="35aaa-147">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="35aaa-148">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="35aaa-148">Writing some code</span></span>

<span data-ttu-id="35aaa-149">Otwórz *ClassLibraryDemo* folderu.</span><span class="sxs-lookup"><span data-stu-id="35aaa-149">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="35aaa-150">Powinny pojawić się następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="35aaa-150">You should see the following files:</span></span>

1. <span data-ttu-id="35aaa-151">`ClassLibraryDemo.fs`, F # pliku z implementacją z klasą zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="35aaa-151">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="35aaa-152">`ClassLibraryDemo.fsproj`, F # plik projektu używany do tworzenia tego projektu.</span><span class="sxs-lookup"><span data-stu-id="35aaa-152">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="35aaa-153">`Script.fsx`, F # plik skryptu, który ładuje plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="35aaa-153">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="35aaa-154">`paket.references`, plik Paket, który określa zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="35aaa-154">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="35aaa-155">Otwórz `Script.fsx`i Dodaj następujący kod na końcu:</span><span class="sxs-lookup"><span data-stu-id="35aaa-155">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="35aaa-156">Ta funkcja konwertuje wyraz do formularza z [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="35aaa-156">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="35aaa-157">Następnym krokiem jest do oceny przy użyciu języka F # Interactive (FSI).</span><span class="sxs-lookup"><span data-stu-id="35aaa-157">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="35aaa-158">Zaznacz całą funkcję (powinien być 11 wierszy).</span><span class="sxs-lookup"><span data-stu-id="35aaa-158">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="35aaa-159">Po jego zostanie wyróżniona, przytrzymaj **Alt** klucza i trafień **Enter**.</span><span class="sxs-lookup"><span data-stu-id="35aaa-159">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="35aaa-160">Można zauważyć okno wyskakujące poniżej, a powinny mieć podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="35aaa-160">You'll notice a window pop up below, and it should show something like this:</span></span>

![Przykład F # Interactive danych wyjściowych z Ionide](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="35aaa-162">Czy to trzy czynności:</span><span class="sxs-lookup"><span data-stu-id="35aaa-162">This did three things:</span></span>

1. <span data-ttu-id="35aaa-163">Proces FSI jego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="35aaa-163">It started the FSI process.</span></span>
2. <span data-ttu-id="35aaa-164">Wyróżniony kod go wysyłane za pośrednictwem procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="35aaa-164">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="35aaa-165">Proces FSI oceniane wysyłane przez kod.</span><span class="sxs-lookup"><span data-stu-id="35aaa-165">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="35aaa-166">Ponieważ był wysyłany za pośrednictwem [funkcja](../language-reference/functions/index.md), można teraz wywołać tej funkcji z FSI!</span><span class="sxs-lookup"><span data-stu-id="35aaa-166">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="35aaa-167">W oknie interaktywnym wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="35aaa-167">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="35aaa-168">Powinny być widoczne następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="35aaa-168">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="35aaa-169">Teraz spróbujmy się od samogłosek jako pierwszą literę.</span><span class="sxs-lookup"><span data-stu-id="35aaa-169">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="35aaa-170">Wprowadź następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="35aaa-170">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="35aaa-171">Powinny być widoczne następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="35aaa-171">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="35aaa-172">Funkcja może działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="35aaa-172">The function appears to be working as expected.</span></span> <span data-ttu-id="35aaa-173">Gratulacje, po prostu zapisane pierwszej funkcji F # w programie Visual Studio Code i oceniać za jego pomocą FSI!</span><span class="sxs-lookup"><span data-stu-id="35aaa-173">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="35aaa-174">Jak można zauważyć, wiersze FSI kończą się `;;`.</span><span class="sxs-lookup"><span data-stu-id="35aaa-174">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="35aaa-175">Jest to spowodowane FSI umożliwia wprowadzanie wielu wierszy.</span><span class="sxs-lookup"><span data-stu-id="35aaa-175">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="35aaa-176">`;;` Na końcu umożliwia FSI wiedzieć, po zakończeniu kod.</span><span class="sxs-lookup"><span data-stu-id="35aaa-176">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="35aaa-177">Wyjaśniający kodu</span><span class="sxs-lookup"><span data-stu-id="35aaa-177">Explaining the code</span></span>

<span data-ttu-id="35aaa-178">Jeśli nie masz pewności o kodzie faktycznie czynności, poniżej przedstawiono krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="35aaa-178">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="35aaa-179">Jak widać, `toPigLatin` jest funkcją, która przyjmuje word jako dane wejściowe i konwertuje ją na Pig Latin reprezentację wyrazie.</span><span class="sxs-lookup"><span data-stu-id="35aaa-179">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="35aaa-180">Dla tej reguły są następujące:</span><span class="sxs-lookup"><span data-stu-id="35aaa-180">The rules for this are as follows:</span></span>

<span data-ttu-id="35aaa-181">Jeśli pierwszy znak w wyrazie rozpoczyna się od samogłosek, należy dodać "yay" do końca słowa.</span><span class="sxs-lookup"><span data-stu-id="35aaa-181">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="35aaa-182">Jeśli go nie zaczyna się od samogłosek, umieść ten pierwszy znak na końcu Word i "ay" Dodaj do niej.</span><span class="sxs-lookup"><span data-stu-id="35aaa-182">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="35aaa-183">Można zauważyć następujące opcje w FSI:</span><span class="sxs-lookup"><span data-stu-id="35aaa-183">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="35aaa-184">Stanowi to, że `toPigLatin` to funkcja, która przyjmuje `string` jako dane wejściowe (nazywane `word`) i zwraca innego `string`.</span><span class="sxs-lookup"><span data-stu-id="35aaa-184">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="35aaa-185">Jest to nazywane [podpis typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawowe technologie języka F #, która jest kluczem do zrozumienia kodzie języka F #.</span><span class="sxs-lookup"><span data-stu-id="35aaa-185">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="35aaa-186">Należy także zauważyć, to jeśli Aktywuj funkcji w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="35aaa-186">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="35aaa-187">W treści funkcji można zauważyć dwa różne części:</span><span class="sxs-lookup"><span data-stu-id="35aaa-187">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="35aaa-188">Wewnętrzna funkcja wywoływana `isVowel`, określający, jeśli dany znak (`c`) jest samogłoskę przez sprawdzenie, czy pasujący wzorców podana za pośrednictwem [dopasowanie wzorca](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="35aaa-188">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="35aaa-189">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Wyrażenie, która sprawdza, czy pierwszy znak samogłoskę, a konstrukcje zwracanym wartość poza wprowadzanie znaków oparte na jeśli pierwszym znakiem jest samogłoskę lub nie:</span><span class="sxs-lookup"><span data-stu-id="35aaa-189">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="35aaa-190">Przepływ `toPigLatin` jest w związku z tym:</span><span class="sxs-lookup"><span data-stu-id="35aaa-190">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="35aaa-191">Sprawdź, czy pierwszy znak wejściowy word samogłoskę.</span><span class="sxs-lookup"><span data-stu-id="35aaa-191">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="35aaa-192">Jeśli tak jest, Dołącz "yay" do końca słowa.</span><span class="sxs-lookup"><span data-stu-id="35aaa-192">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="35aaa-193">W przeciwnym razie umieść ten pierwszy znak na końcu Word i "ay" Dodaj do niej.</span><span class="sxs-lookup"><span data-stu-id="35aaa-193">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="35aaa-194">Brak końcowego rzecz do Zwróć uwagę na ten temat: Brak nie jawna instrukcja ma zostać zwrócony przez funkcję, w odróżnieniu od wielu innych języków tam.</span><span class="sxs-lookup"><span data-stu-id="35aaa-194">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="35aaa-195">To dlatego F # jest oparte na wyrażeniach oraz ostatnich wyrażenie w treści funkcji jest zwracana wartość.</span><span class="sxs-lookup"><span data-stu-id="35aaa-195">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="35aaa-196">Ponieważ `if..then..else` jest wyrażenie, treść `then` bloku lub treści `else` bloku zostanie zwrócony w zależności od wartości wejściowej.</span><span class="sxs-lookup"><span data-stu-id="35aaa-196">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="35aaa-197">Przenoszenie kodu skryptu do pliku implementacji</span><span class="sxs-lookup"><span data-stu-id="35aaa-197">Moving your script code into the implementation file</span></span>

<span data-ttu-id="35aaa-198">Poprzednich sekcjach, w tym artykule przedstawiono typowe pierwszą czynnością przy tworzeniu kodzie języka F #: pisanie początkowej funkcji i jej wykonanie interakcyjnie z FSI.</span><span class="sxs-lookup"><span data-stu-id="35aaa-198">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="35aaa-199">Jest to nazywane REPL-driven development, gdzie [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) oznacza "Pętlę odczytu oceny-drukarek".</span><span class="sxs-lookup"><span data-stu-id="35aaa-199">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="35aaa-200">Jest to dobry sposób na wypróbowanie funkcji, aż do uzyskania elementu pracy.</span><span class="sxs-lookup"><span data-stu-id="35aaa-200">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="35aaa-201">Następny krok w REPL-driven development, jest Przenieś pracy kod do pliku implementacji F #.</span><span class="sxs-lookup"><span data-stu-id="35aaa-201">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="35aaa-202">Go można następnie zbierane przez kompilator języka F # w zespół, który może zostać wykonany.</span><span class="sxs-lookup"><span data-stu-id="35aaa-202">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="35aaa-203">Aby rozpocząć, otwórz `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="35aaa-203">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="35aaa-204">Można zauważyć, że kod jest już istnieje.</span><span class="sxs-lookup"><span data-stu-id="35aaa-204">You'll notice that some code is already in there.</span></span> <span data-ttu-id="35aaa-205">Przejdź dalej i usunąć definicji klasy, ale pamiętaj pozostawić [ `namespace` ](../language-reference/namespaces.md) deklaracji u góry.</span><span class="sxs-lookup"><span data-stu-id="35aaa-205">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="35aaa-206">Następnie należy utworzyć nowy [ `module` ](../language-reference/modules.md) o nazwie `PigLatin` i skopiuj `toPigLatin` funkcji w nim sposób:</span><span class="sxs-lookup"><span data-stu-id="35aaa-206">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="35aaa-207">Następnie otwórz folder `Script.fsx` ponownie, a następnie usuń całą `toPigLatin` działać, ale pamiętaj zachować następujące dwa wiersze w pliku:</span><span class="sxs-lookup"><span data-stu-id="35aaa-207">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="35aaa-208">Pierwszy wiersz jest wymagany dla skryptów do załadowania FSI `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="35aaa-208">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="35aaa-209">Drugi wiersz jest udogodnienie: pomijając go jest opcjonalne, ale będzie musiał podać `open ClassLibraryDemo` w oknie FSI, jeśli chcesz wyświetlić `ToPigLatin` modułu do zakresu.</span><span class="sxs-lookup"><span data-stu-id="35aaa-209">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="35aaa-210">Następnie w oknie FSI, wywołaj funkcję z `PigLatin` moduł, który został zdefiniowany wcześniej:</span><span class="sxs-lookup"><span data-stu-id="35aaa-210">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="35aaa-211">Powodzenie!</span><span class="sxs-lookup"><span data-stu-id="35aaa-211">Success!</span></span> <span data-ttu-id="35aaa-212">Pobierz wyniki przed, ale teraz załadowanego z pliku implementacji F #.</span><span class="sxs-lookup"><span data-stu-id="35aaa-212">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="35aaa-213">Główną różnicą jest kompilowane pliki źródłowe języka F # w zestawy, które mogą być wykonywane w dowolnym miejscu, nie tylko w FSI.</span><span class="sxs-lookup"><span data-stu-id="35aaa-213">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="35aaa-214">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="35aaa-214">Summary</span></span>

<span data-ttu-id="35aaa-215">W tym artykule kiedy znasz już:</span><span class="sxs-lookup"><span data-stu-id="35aaa-215">In this article, you've learned:</span></span>

1. <span data-ttu-id="35aaa-216">Jak skonfigurować program Visual Studio Code z Ionide.</span><span class="sxs-lookup"><span data-stu-id="35aaa-216">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="35aaa-217">Jak utworzyć pierwszy projekt F # z Ionide.</span><span class="sxs-lookup"><span data-stu-id="35aaa-217">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="35aaa-218">Jak używać F # skryptów do zapisywania pierwszej funkcji F # w Ionide i wykonaj go w FSI.</span><span class="sxs-lookup"><span data-stu-id="35aaa-218">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="35aaa-219">Jak przeprowadzić migrację skryptu kodu źródłowego języka F #, a następnie wywołać kodu z FSI.</span><span class="sxs-lookup"><span data-stu-id="35aaa-219">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="35aaa-220">Teraz jest wyposażona w kodzie znacznie więcej F # za pomocą programu Visual Studio Code i Ionide.</span><span class="sxs-lookup"><span data-stu-id="35aaa-220">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="35aaa-221">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="35aaa-221">Troubleshooting</span></span>

<span data-ttu-id="35aaa-222">Poniżej przedstawiono kilka sposobów, można rozwiązać niektóre problemy, które mogą być uruchamiane na:</span><span class="sxs-lookup"><span data-stu-id="35aaa-222">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="35aaa-223">Aby uzyskać funkcji Ionide edycji kodu, plikach języka F # trzeba zapisać na dysku i wewnątrz folderu, który jest otwarty w obszarze roboczym Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="35aaa-223">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="35aaa-224">Jeśli zostały wprowadzone zmiany w systemie lub zainstalowane wymagania wstępne Ionide z programu Visual Studio Code Otwórz, uruchom ponownie program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="35aaa-224">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="35aaa-225">Sprawdź, czy można użyć kompilator języka F # i F # interactive w wierszu polecenia bez w pełni kwalifikowaną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="35aaa-225">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="35aaa-226">Możesz to zrobić, wpisując `fsc` w wierszu polecenia, aby uzyskać kompilator języka F # i `fsi` lub `fsharpi` Visual F # tools w systemach Windows i Mono na system Mac/Linux, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="35aaa-226">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="35aaa-227">Jeśli masz nieprawidłowe znaki w katalogach projektu Ionide może nie działać.</span><span class="sxs-lookup"><span data-stu-id="35aaa-227">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="35aaa-228">Jeśli jest to możliwe, Zmień nazwy katalogów projektu.</span><span class="sxs-lookup"><span data-stu-id="35aaa-228">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="35aaa-229">Brak polecenia Ionide pracy, sprawdź Twojej [powiązań kluczy programu Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) aby zobaczyć, czy jest zastępowanie ich przypadkowo.</span><span class="sxs-lookup"><span data-stu-id="35aaa-229">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="35aaa-230">Jeśli Ionide jest dzielony na komputerze, a żadne z powyższych poprawił problemu, spróbuj usunąć `ionide-fsharp` katalogu na komputerze i ponowne zainstalowanie zestawu dodatku.</span><span class="sxs-lookup"><span data-stu-id="35aaa-230">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="35aaa-231">Ionide to projekt typu open source, wbudowane i obsługiwana przez członków społeczności F #.</span><span class="sxs-lookup"><span data-stu-id="35aaa-231">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="35aaa-232">Sprawdź zgłaszania problemów i możesz zająć się na [Ionide VSCode: repozytorium GitHub języka FSharp](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="35aaa-232">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="35aaa-233">Jeśli masz problem do raportu, postępuj [instrukcje dotyczące pobierania dzienników do użycia podczas raportowania problemu](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="35aaa-233">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="35aaa-234">Możesz również poprosić Aby uzyskać dalszą pomoc od Ionide deweloperów i F # społeczności w [kanału Ionide Gitter](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="35aaa-234">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="35aaa-235">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="35aaa-235">Next steps</span></span>

<span data-ttu-id="35aaa-236">Aby dowiedzieć się więcej na temat języka F # i funkcji języka, zapoznaj się [samouczek programu F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="35aaa-236">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
