---
title: 'Rozpoczynanie pracy z F # w kodzie programu Visual Studio'
description: "Dowiedz się, jak używanie F # za pomocą programu Visual Studio Code i Ionide suite wtyczki."
keywords: visual f#, f#, functional programming, .NET, Visual Studio Code, vscode, Ionide
author: cartermp
ms.author: phcart
ms.date: 02/28/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: c452e791b27bc3f32e137a515011d953005344c6
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="93fbd-104">Rozpoczynanie pracy z F # w kodzie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="93fbd-104">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="93fbd-105">Możesz pisać F # [Visual Studio Code](https://code.visualstudio.com) z [wtyczki Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)w celu uzyskania maksymalnego komfortu obsługi IDE (Integrade programowanie Enivronment) i platform, lekkie IntelliSense i podstawowe kodu refaktoryzacje.</span><span class="sxs-lookup"><span data-stu-id="93fbd-105">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight IDE (Integrade Development Enivronment) experience with IntelliSense and basic code refactorings.</span></span>  <span data-ttu-id="93fbd-106">Odwiedź stronę [Ionide.io](http://ionide.io) Aby dowiedzieć się więcej o pakiecie wtyczki.</span><span class="sxs-lookup"><span data-stu-id="93fbd-106">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="93fbd-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="93fbd-107">Prerequisites</span></span>

<span data-ttu-id="93fbd-108">Musi mieć [git zainstalowane](https://git-scm.com/download) i znajduje się na ŚCIEŻCE, aby użyć szablonów projektu w Ionide.</span><span class="sxs-lookup"><span data-stu-id="93fbd-108">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span>  <span data-ttu-id="93fbd-109">Można sprawdzić, czy jest poprawnie zainstalowany, wpisując `git --version` w wierszu polecenia i naciskając klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="93fbd-109">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="93fbd-110">macOS</span><span class="sxs-lookup"><span data-stu-id="93fbd-110">macOS</span></span>](#tab/macos)

<span data-ttu-id="93fbd-111">Używa Ionide [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="93fbd-111">Ionide uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="93fbd-112">Najprostszym sposobem zainstalowania Mono na macOS odbywa się za pośrednictwem oprogramowania Homebrew.</span><span class="sxs-lookup"><span data-stu-id="93fbd-112">The easiest way to install Mono on macOS is via Homebrew.</span></span>  <span data-ttu-id="93fbd-113">W terminalu, po prostu wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="93fbd-113">Simply type the following into your terminal:</span></span>

```
brew install mono
```

<span data-ttu-id="93fbd-114">Należy również zainstalować [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="93fbd-114">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="93fbd-115">Linux</span><span class="sxs-lookup"><span data-stu-id="93fbd-115">Linux</span></span>](#tab/linux)

<span data-ttu-id="93fbd-116">W systemie Linux, używa również Ionide [Mono](https://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="93fbd-116">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="93fbd-117">Jeśli używasz Debian i Ubuntu, można użyć następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="93fbd-117">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="93fbd-118">Należy również zainstalować [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="93fbd-118">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="93fbd-119">Windows</span><span class="sxs-lookup"><span data-stu-id="93fbd-119">Windows</span></span>](#tab/windows)

<span data-ttu-id="93fbd-120">Jeśli w systemie Windows, należy najpierw [zainstalować program Visual Studio z obsługą F #](get-started-visual-studio.md#installing-f).</span><span class="sxs-lookup"><span data-stu-id="93fbd-120">If you're on Windows, you must [install Visual Studio with F# support](get-started-visual-studio.md#installing-f).</span></span> <span data-ttu-id="93fbd-121">Spowoduje to zainstalowanie wszystkich składników niezbędnych do zapisu, kompilowania i wykonywania kodzie języka F #.</span><span class="sxs-lookup"><span data-stu-id="93fbd-121">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="93fbd-122">Należy również zainstalować [.NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="93fbd-122">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="93fbd-123">Instalowanie dodatku Ionide i Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="93fbd-123">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="93fbd-124">Można zainstalować program Visual Studio Code z [code.visualstudio.com](https://code.visualstudio.com) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="93fbd-124">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span> <span data-ttu-id="93fbd-125">Po wykonaniu tej istnieją dwa sposoby znajdowania Ionide wtyczki:</span><span class="sxs-lookup"><span data-stu-id="93fbd-125">After that, there are two ways to find the Ionide plugin:</span></span>

1. <span data-ttu-id="93fbd-126">Użyj polecenia palety (Ctrl + Shift + P w systemie Windows, ⌘ + Shift + P na macOS, Ctrl + Shift + P w systemie Linux) i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="93fbd-126">Use the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

    ```
    >ext install Ionide
    ```

2. <span data-ttu-id="93fbd-127">Kliknij ikonę rozszerzenia i wyszukaj "Ionide":</span><span class="sxs-lookup"><span data-stu-id="93fbd-127">Click the Extensions icon and search for "Ionide":</span></span>

    ![](media/getting-started-vscode/vscode-ext.png)

<span data-ttu-id="93fbd-128">Tylko wtyczki, wymagana jest obsługa F # w programie Visual Studio Code [języka fsharp Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="93fbd-128">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="93fbd-129">Jednakże można także zainstalować [SFAŁSZOWANA Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) i uzyskać [SFAŁSZOWAĆ](https://fsharp.github.io/FAKE/) obsługuje i [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) uzyskanie [Paket](https://fsprojects.github.io/Paket/) obsługuje.</span><span class="sxs-lookup"><span data-stu-id="93fbd-129">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) and to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="93fbd-130">FAŁSZYWE i Paket są dodatkowe F # społeczności narzędzia do tworzenia projektów i zarządzanie nimi zależności, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="93fbd-130">FAKE and Paket are additonal F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="93fbd-131">Tworzenie pierwszego projektu z Ionide</span><span class="sxs-lookup"><span data-stu-id="93fbd-131">Creating your first project with Ionide</span></span>

<span data-ttu-id="93fbd-132">Aby utworzyć nowy projekt F #, Otwórz program Visual Studio Code w nowym folderze (można określić nazwę dowolne).</span><span class="sxs-lookup"><span data-stu-id="93fbd-132">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

![](media/getting-started-vscode/vscode-open-dir.png)

<span data-ttu-id="93fbd-133">Następnie otwórz palety polecenia (Ctrl + Shift + P w systemie Windows, ⌘ + Shift + P na macOS, Ctrl + Shift + P w systemie Linux) i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="93fbd-133">Next, open the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

```
>f#: New Project
```

<span data-ttu-id="93fbd-134">Jest to obsługiwane przez [FORGE](https://github.com/fsharp-editing/Forge) projektu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-134">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>  <span data-ttu-id="93fbd-135">Powinny pojawić się dane podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="93fbd-135">You should see something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
<span data-ttu-id="93fbd-136">Jeśli nie widzisz powyższego, spróbuj odświeżyć szablony, uruchamiając następujące polecenie w palecie polecenia: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="93fbd-136">If you don't see the above, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="93fbd-137">Wybierz opcję "F #: nowego projektu" za pomocą **Enter**, która spowoduje przejście do tego kroku:</span><span class="sxs-lookup"><span data-stu-id="93fbd-137">Select "F#: New Project" by hitting **Enter**, which will take you to this step:</span></span>

![](media/getting-started-vscode/vscode-proj-type.png)

<span data-ttu-id="93fbd-138">Wybierz opcję szablon dla określonego typu projektu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-138">This will select a template for a specific type of project.</span></span>  <span data-ttu-id="93fbd-139">Istnieje kilka opcji, takich jak [FsLab](https://fslab.org) szablon do analizy danych lub [Suave](https://suave.io) szablon programowania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="93fbd-139">There are quite a few options here, such as an [FsLab](https://fslab.org) template for Data Science or [Suave](https://suave.io) template for Web Programming.</span></span>  <span data-ttu-id="93fbd-140">W tym artykule wykorzystano `classlib` szablon, więc podkreślenie i naciśnij **Enter**.</span><span class="sxs-lookup"><span data-stu-id="93fbd-140">This article uses the `classlib` template, so highlight that and hit **Enter**.</span></span>  <span data-ttu-id="93fbd-141">Następnie zostanie osiągnąć następny krok:</span><span class="sxs-lookup"><span data-stu-id="93fbd-141">You will then reach the following step:</span></span>

![](media/getting-started-vscode/vscode-new-dir.png)

<span data-ttu-id="93fbd-142">Dzięki temu można utworzyć projektu w innym katalogu, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="93fbd-142">This lets you create the project in a different directory, if you like.</span></span>  <span data-ttu-id="93fbd-143">Pozostaw pole puste, teraz.</span><span class="sxs-lookup"><span data-stu-id="93fbd-143">Leave it blank for now.</span></span>  <span data-ttu-id="93fbd-144">Projekt zostanie utworzony w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-144">It will create the project in the current directory.</span></span>  <span data-ttu-id="93fbd-145">Po naciśnięciu **Enter**, osiągną następujący krok:</span><span class="sxs-lookup"><span data-stu-id="93fbd-145">Once you press **Enter**, you will reach the following step:</span></span>

![](media/getting-started-vscode/vscode-proj-name.png)

<span data-ttu-id="93fbd-146">Dzięki temu można nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-146">This lets you name your project.</span></span>  <span data-ttu-id="93fbd-147">F # używa [przypadku Pascal](http://c2.com/cgi/wiki?PascalCase) dla nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-147">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span>  <span data-ttu-id="93fbd-148">W tym artykule wykorzystano `ClassLibraryDemo` jako nazwy.</span><span class="sxs-lookup"><span data-stu-id="93fbd-148">This article uses `ClassLibraryDemo` as the name.</span></span>  <span data-ttu-id="93fbd-149">Po wprowadzeniu nazwy dla projektu, kliknij przycisk **Enter**.</span><span class="sxs-lookup"><span data-stu-id="93fbd-149">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="93fbd-150">Po wykonaniu poprzednich kroków kroku, należy pobrać Visual Studio Code obszaru roboczego po lewej stronie do wyglądać mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="93fbd-150">If you followed the previous step steps, you should get the Visual Studio Code Workspace on the left-hand side to look something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

<span data-ttu-id="93fbd-151">Ten szablon generuje kilka rzeczy, które można znaleźć przydatne:</span><span class="sxs-lookup"><span data-stu-id="93fbd-151">This template generates a few things you'll find useful:</span></span>

1. <span data-ttu-id="93fbd-152">F # projektu, underneath `ClassLibraryDemo` folderu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-152">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="93fbd-153">Dodawanie pakietów za pomocą struktury poprawny katalog [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="93fbd-153">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="93fbd-154">Obsługujący wiele platform kompilacji skryptu o [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="93fbd-154">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="93fbd-155">`paket.exe` Plik wykonywalny, który można pobrać pakietów i rozpoznać zależności dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="93fbd-155">The `paket.exe` executable which can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="93fbd-156">A `.gitignore` plik, jeśli chcesz dodać ten projekt do kontroli źródła na podstawie Git.</span><span class="sxs-lookup"><span data-stu-id="93fbd-156">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="93fbd-157">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="93fbd-157">Writing some code</span></span>

<span data-ttu-id="93fbd-158">Otwórz *ClassLibraryDemo* folderu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-158">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="93fbd-159">Powinny pojawić się następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="93fbd-159">You should see the following files:</span></span>

1. <span data-ttu-id="93fbd-160">`ClassLibraryDemo.fs`, F # pliku z implementacją z klasą zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="93fbd-160">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="93fbd-161">`CassLibraryDemo.fsproj`, F # plik projektu używany do tworzenia tego projektu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-161">`CassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="93fbd-162">`Script.fsx`, F # pliku skryptu, który ładuje plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="93fbd-162">`Script.fsx`, an F# script file which loads the source file.</span></span>
4. <span data-ttu-id="93fbd-163">`paket.references`, plik Paket, który określa zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-163">`paket.references`, a Paket file which specifies the project dependencies.</span></span>

<span data-ttu-id="93fbd-164">Otwórz `Script.fsx`i Dodaj następujący kod na końcu:</span><span class="sxs-lookup"><span data-stu-id="93fbd-164">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="93fbd-165">Ta funkcja konwertuje wyraz do formularza z [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="93fbd-165">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span>  <span data-ttu-id="93fbd-166">Następnym krokiem jest do oceny przy użyciu języka F # Interactive (FSI).</span><span class="sxs-lookup"><span data-stu-id="93fbd-166">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="93fbd-167">Zaznacz całą funkcję (powinien być 11 wierszy).</span><span class="sxs-lookup"><span data-stu-id="93fbd-167">Highlight the entire function (it should be 11 lines long).</span></span>  <span data-ttu-id="93fbd-168">Po jego zostanie wyróżniona, przytrzymaj **Alt** klucza i trafień **Enter**.</span><span class="sxs-lookup"><span data-stu-id="93fbd-168">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span>  <span data-ttu-id="93fbd-169">Można zauważyć okno wyskakujące poniżej, a powinny mieć podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="93fbd-169">You'll notice a window pop up below, and it should show something like this:</span></span>

![](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="93fbd-170">Czy to trzy czynności:</span><span class="sxs-lookup"><span data-stu-id="93fbd-170">This did three things:</span></span>

1. <span data-ttu-id="93fbd-171">Proces FSI jego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="93fbd-171">It started the FSI process.</span></span>
2. <span data-ttu-id="93fbd-172">Wyróżniony kod go wysyłane za pośrednictwem procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="93fbd-172">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="93fbd-173">Proces FSI oceniane wysyłane przez kod.</span><span class="sxs-lookup"><span data-stu-id="93fbd-173">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="93fbd-174">Ponieważ był wysyłany za pośrednictwem [funkcja](../language-reference/functions/index.md), można teraz wywołać tej funkcji z FSI!</span><span class="sxs-lookup"><span data-stu-id="93fbd-174">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span>  <span data-ttu-id="93fbd-175">W oknie interaktywnym wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="93fbd-175">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="93fbd-176">Powinny być widoczne następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="93fbd-176">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="93fbd-177">Teraz spróbujmy się od samogłosek jako pierwszą literę.</span><span class="sxs-lookup"><span data-stu-id="93fbd-177">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="93fbd-178">Wprowadź następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="93fbd-178">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="93fbd-179">Powinny być widoczne następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="93fbd-179">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="93fbd-180">Funkcja może działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="93fbd-180">The function appears to be working as expected.</span></span>  <span data-ttu-id="93fbd-181">Gratulacje, po prostu zapisane pierwszej funkcji F # w programie Visual Studio Code i oceniać za jego pomocą FSI!</span><span class="sxs-lookup"><span data-stu-id="93fbd-181">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="93fbd-182">Jak można zauważyć, wiersze FSI kończą się `;;`.</span><span class="sxs-lookup"><span data-stu-id="93fbd-182">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span>  <span data-ttu-id="93fbd-183">Jest to spowodowane FSI umożliwia wprowadzanie wielu wierszy.</span><span class="sxs-lookup"><span data-stu-id="93fbd-183">This is because FSI allows you to enter multiple lines.</span></span>  <span data-ttu-id="93fbd-184">`;;` Na końcu umożliwia FSI wiedzieć, po zakończeniu kod.</span><span class="sxs-lookup"><span data-stu-id="93fbd-184">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="93fbd-185">Wyjaśniający kodu</span><span class="sxs-lookup"><span data-stu-id="93fbd-185">Explaining the code</span></span>

<span data-ttu-id="93fbd-186">Jeśli nie masz pewności o kodzie faktycznie czynności, poniżej przedstawiono krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="93fbd-186">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="93fbd-187">Jak widać, `toPigLatin` jest funkcję, która przyjmuje word jako dane wejściowe i konwertuje ją na Pig Latin reprezentację wyrazie.</span><span class="sxs-lookup"><span data-stu-id="93fbd-187">As you can see, `toPigLatin` is a function which takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span>  <span data-ttu-id="93fbd-188">Dla tej reguły są następujące:</span><span class="sxs-lookup"><span data-stu-id="93fbd-188">The rules for this are as follows:</span></span>

<span data-ttu-id="93fbd-189">Jeśli pierwszy znak w wyrazie rozpoczyna się od samogłosek, należy dodać "yay" do końca słowa.</span><span class="sxs-lookup"><span data-stu-id="93fbd-189">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span>  <span data-ttu-id="93fbd-190">Jeśli go nie zaczyna się od samogłosek, umieść ten pierwszy znak na końcu Word i "ay" Dodaj do niej.</span><span class="sxs-lookup"><span data-stu-id="93fbd-190">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="93fbd-191">Można zauważyć następujące opcje w FSI:</span><span class="sxs-lookup"><span data-stu-id="93fbd-191">You may have noticed the following in FSI:</span></span>

```
val toPigLatin : word:string -> string
```

<span data-ttu-id="93fbd-192">Ta stwierdza, że `toPigLatin` jest funkcją, która przyjmuje `string` jako dane wejściowe (nazywane `word`) i zwraca innego `string`.</span><span class="sxs-lookup"><span data-stu-id="93fbd-192">This states that `toPigLatin` is a function which takes in a `string` as input (called `word`), and returns another `string`.</span></span>  <span data-ttu-id="93fbd-193">Jest to nazywane [podpis typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawowe technologie języka F #, która jest kluczem do zrozumienia kodzie języka F #.</span><span class="sxs-lookup"><span data-stu-id="93fbd-193">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span>  <span data-ttu-id="93fbd-194">Należy także zauważyć, to jeśli Aktywuj funkcji w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="93fbd-194">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="93fbd-195">W treści funkcji można zauważyć dwa różne części:</span><span class="sxs-lookup"><span data-stu-id="93fbd-195">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="93fbd-196">Wewnętrzna funkcja wywoływana `isVowel`, która określa, czy dany znak (`c`) jest samogłoskę przez sprawdzenie, czy pasujący wzorców podana za pośrednictwem [dopasowanie wzorca](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="93fbd-196">An inner function, called `isVowel`, which determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="93fbd-197">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Wyrażenie, które sprawdza, czy pierwszy znak jest samogłoskę i konstruuje wartość zwracaną poza wprowadzanie znaków na podstawie pierwszego znaku, gdy był samogłoskę lub nie:</span><span class="sxs-lookup"><span data-stu-id="93fbd-197">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression which checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="93fbd-198">Przepływ `toPigLatin` jest w związku z tym:</span><span class="sxs-lookup"><span data-stu-id="93fbd-198">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="93fbd-199">Sprawdź, czy pierwszy znak wejściowy word samogłoskę.</span><span class="sxs-lookup"><span data-stu-id="93fbd-199">Check if the first character of the input word is a vowel.</span></span>  <span data-ttu-id="93fbd-200">Jeśli tak jest, Dołącz "yay" do końca słowa.</span><span class="sxs-lookup"><span data-stu-id="93fbd-200">If it is, attach "yay" to the end of the word.</span></span>  <span data-ttu-id="93fbd-201">W przeciwnym razie umieść ten pierwszy znak na końcu Word i "ay" Dodaj do niej.</span><span class="sxs-lookup"><span data-stu-id="93fbd-201">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="93fbd-202">Brak końcowego rzecz do Zwróć uwagę na ten temat: Brak nie jawna instrukcja ma zostać zwrócony przez funkcję, w odróżnieniu od wielu innych języków tam.</span><span class="sxs-lookup"><span data-stu-id="93fbd-202">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span>  <span data-ttu-id="93fbd-203">To dlatego F # jest oparte na wyrażeniach oraz ostatnich wyrażenie w treści funkcji jest zwracana wartość.</span><span class="sxs-lookup"><span data-stu-id="93fbd-203">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span>  <span data-ttu-id="93fbd-204">Ponieważ `if..then..else` jest wyrażenie, treść `then` bloku lub treści `else` bloku zostanie zwrócony w zależności od wartości wejściowej.</span><span class="sxs-lookup"><span data-stu-id="93fbd-204">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="93fbd-205">Przenoszenie kodu skryptu do pliku implementacji</span><span class="sxs-lookup"><span data-stu-id="93fbd-205">Moving your script code into the implementation file</span></span>

<span data-ttu-id="93fbd-206">Poprzednich sekcjach, w tym artykule przedstawiono typowe pierwszą czynnością przy tworzeniu kodzie języka F #: pisanie początkowej funkcji i jej wykonanie interakcyjnie z FSI.</span><span class="sxs-lookup"><span data-stu-id="93fbd-206">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span>  <span data-ttu-id="93fbd-207">Jest to nazywane REPL-driven development, gdzie oznacza REPL "Pętlę odczytu oceny-drukarek".</span><span class="sxs-lookup"><span data-stu-id="93fbd-207">This is known as REPL-driven development, where REPL stands for "Read-Evaluate-Print Loop".</span></span>  <span data-ttu-id="93fbd-208">Jest to dobry sposób na wypróbowanie funkcji, aż do uzyskania elementu pracy.</span><span class="sxs-lookup"><span data-stu-id="93fbd-208">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="93fbd-209">Następny krok w REPL-driven development, jest Przenieś pracy kod do pliku implementacji F #.</span><span class="sxs-lookup"><span data-stu-id="93fbd-209">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span>  <span data-ttu-id="93fbd-210">Go można następnie można skompilować przez kompilator języka F # do zestawu, które mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="93fbd-210">It can then be compiled by the F# compiler into an assembly which can be executed.</span></span>

<span data-ttu-id="93fbd-211">Aby rozpocząć, otwórz `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="93fbd-211">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="93fbd-212">Można zauważyć, że kod jest już istnieje.</span><span class="sxs-lookup"><span data-stu-id="93fbd-212">You'll notice that some code is already in there.</span></span>  <span data-ttu-id="93fbd-213">Przejdź dalej i usunąć definicji klasy, ale pamiętaj pozostawić [ `namespace` ](../language-reference/namespaces.md) deklaracji u góry.</span><span class="sxs-lookup"><span data-stu-id="93fbd-213">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="93fbd-214">Następnie należy utworzyć nowy [ `module` ](../language-reference/modules.md) o nazwie `PigLatin` i skopiuj `toPigLatin` funkcji w nim sposób:</span><span class="sxs-lookup"><span data-stu-id="93fbd-214">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="93fbd-215">Jest to jedna z wielu sposobów, jeśli chcesz także wywoływanie kodu z języka C# lub Visual Basic, projekty można organizować funkcje w kodzie języka F # i typowym podejściem.</span><span class="sxs-lookup"><span data-stu-id="93fbd-215">This is one of the many ways you can organize functions in F# code, and a common approach if you also want to call your code from C# or Visual Basic projects.</span></span>

<span data-ttu-id="93fbd-216">Następnie otwórz folder `Script.fsx` ponownie, a następnie usuń całą `toPigLatin` działać, ale pamiętaj zachować następujące dwa wiersze w pliku:</span><span class="sxs-lookup"><span data-stu-id="93fbd-216">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="93fbd-217">Pierwszy wiersz jest wymagany dla skryptów do załadowania FSI `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="93fbd-217">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="93fbd-218">Drugi wiersz jest udogodnienie: pomijając go jest opcjonalne, ale będzie musiał podać `open ClassLibraryDemo` w oknie FSI, jeśli chcesz wyświetlić `ToPigLatin` modułu do zakresu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-218">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="93fbd-219">Następnie w oknie FSI, wywołaj funkcję z `PigLatin` moduł, który został zdefiniowany wcześniej:</span><span class="sxs-lookup"><span data-stu-id="93fbd-219">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="93fbd-220">Powodzenie!</span><span class="sxs-lookup"><span data-stu-id="93fbd-220">Success!</span></span>  <span data-ttu-id="93fbd-221">Pobierz wyniki przed, ale teraz załadowanego z pliku implementacji F #.</span><span class="sxs-lookup"><span data-stu-id="93fbd-221">You get the same results as before, but now loaded from an F# implementation file.</span></span>  <span data-ttu-id="93fbd-222">W tym miejscu główna różnica polega na tym, że pliki źródłowe języka F # są skompilowane w zestawy, które mogą być wykonywane w dowolnym miejscu, nie tylko w FSI.</span><span class="sxs-lookup"><span data-stu-id="93fbd-222">The major difference here is that F# source files are compiled into assemblies which can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="93fbd-223">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="93fbd-223">Summary</span></span>

<span data-ttu-id="93fbd-224">W tym artykule kiedy znasz już:</span><span class="sxs-lookup"><span data-stu-id="93fbd-224">In this article, you've learned:</span></span>

1. <span data-ttu-id="93fbd-225">Jak skonfigurować program Visual Studio Code z Ionide.</span><span class="sxs-lookup"><span data-stu-id="93fbd-225">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="93fbd-226">Jak utworzyć pierwszy projekt F # z Ionide.</span><span class="sxs-lookup"><span data-stu-id="93fbd-226">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="93fbd-227">Jak używać F # skryptów do zapisywania pierwszej funkcji F # w Ionide i wykonaj go w FSI.</span><span class="sxs-lookup"><span data-stu-id="93fbd-227">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="93fbd-228">Jak przeprowadzić migrację skryptu kodu źródłowego języka F #, a następnie wywołać kodu z FSI.</span><span class="sxs-lookup"><span data-stu-id="93fbd-228">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="93fbd-229">Teraz jest wyposażona w kodzie znacznie więcej F # za pomocą programu Visual Studio Code i Ionide.</span><span class="sxs-lookup"><span data-stu-id="93fbd-229">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="93fbd-230">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="93fbd-230">Troubleshooting</span></span>

<span data-ttu-id="93fbd-231">Poniżej przedstawiono kilka sposobów, można rozwiązać niektóre problemy, które mogą być uruchamiane na:</span><span class="sxs-lookup"><span data-stu-id="93fbd-231">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="93fbd-232">Aby uzyskać funkcji Ionide edycji kodu, plikach języka F # trzeba zapisać na dysku i wewnątrz folderu, który jest otwarty w obszarze roboczym Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="93fbd-232">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="93fbd-233">Jeśli zostały wprowadzone zmiany w systemie lub zainstalowane wymagania wstępne Ionide z programu Visual Studio Code Otwórz, uruchom ponownie program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="93fbd-233">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="93fbd-234">Sprawdź, czy można użyć kompilator języka F # i F # interactive w wierszu polecenia bez w pełni kwalifikowaną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="93fbd-234">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span>  <span data-ttu-id="93fbd-235">Możesz to zrobić, wpisując `fsc` w wierszu polecenia, aby uzyskać kompilator języka F # i `fsi` lub `fsharpi` Visual F # tools w systemach Windows i Mono na system Mac/Linux, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="93fbd-235">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="93fbd-236">Jeśli masz nieprawidłowe znaki w katalogach projektu Ionide może nie działać.</span><span class="sxs-lookup"><span data-stu-id="93fbd-236">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="93fbd-237">Jeśli jest to możliwe, Zmień nazwy katalogów projektu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-237">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="93fbd-238">Brak polecenia Ionide pracy, sprawdź Twojej [powiązań kluczy programu Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) aby zobaczyć, czy jest zastępowanie ich przypadkowo.</span><span class="sxs-lookup"><span data-stu-id="93fbd-238">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="93fbd-239">Jeśli Ionide jest dzielony na komputerze, a żadne z powyższych poprawił problemu, spróbuj usunąć `ionide-fsharp` katalogu na komputerze i ponowne zainstalowanie zestawu dodatku.</span><span class="sxs-lookup"><span data-stu-id="93fbd-239">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="93fbd-240">Ionide to projekt typu open source, wbudowane i obsługiwana przez członków społeczności F #.</span><span class="sxs-lookup"><span data-stu-id="93fbd-240">Ionide is an open source project built and maintained by members of the F# community.</span></span>  <span data-ttu-id="93fbd-241">Sprawdź zgłaszania problemów i możesz zająć się na [Ionide VSCode: repozytorium GitHub języka FSharp](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="93fbd-241">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="93fbd-242">Jeśli masz problem do raportu, postępuj [instrukcje dotyczące pobierania dzienników do użycia podczas raportowania problemu](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="93fbd-242">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="93fbd-243">Możesz również poprosić Aby uzyskać dalszą pomoc od Ionide deweloperów i F # społeczności w [kanału Ionide Gitter](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="93fbd-243">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="93fbd-244">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="93fbd-244">Next steps</span></span>

<span data-ttu-id="93fbd-245">Aby dowiedzieć się więcej na temat języka F # i funkcji języka, zapoznaj się [samouczek programu F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="93fbd-245">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="93fbd-246">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93fbd-246">See also</span></span>

[<span data-ttu-id="93fbd-247">Przewodnik po F#</span><span class="sxs-lookup"><span data-stu-id="93fbd-247">Tour of F#</span></span>](../tour.md)

[<span data-ttu-id="93fbd-248">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="93fbd-248">F# Language Reference</span></span>](../language-reference/index.md)

[<span data-ttu-id="93fbd-249">Funkcje</span><span class="sxs-lookup"><span data-stu-id="93fbd-249">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="93fbd-250">Moduły</span><span class="sxs-lookup"><span data-stu-id="93fbd-250">Modules</span></span>](../language-reference/modules.md)

[<span data-ttu-id="93fbd-251">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="93fbd-251">Namespaces</span></span>](../language-reference/namespaces.md)

[<span data-ttu-id="93fbd-252">Ionide-VSCode: FSharp</span><span class="sxs-lookup"><span data-stu-id="93fbd-252">Ionide-VSCode: FSharp</span></span>](https://github.com/ionide/ionide-vscode-fsharp)
