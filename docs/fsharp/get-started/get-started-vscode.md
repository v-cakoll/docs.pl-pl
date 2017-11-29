---
title: 'Wprowadzenie do programu F # w kodzie programu Visual Studio z Ionide'
description: "Dowiedz się, jak używanie F # za pomocą programu Visual Studio Code i Ionide suite wtyczki."
keywords: "Visual f #, f #, funkcjonalności programowania, vscode .NET, Visual Studio Code, Ionide"
author: cartermp
ms.author: phcart
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 336316eaf474f4c10d63657f178ce4a336ad7a54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-f-in-visual-studio-code-with-ionide"></a><span data-ttu-id="28bf9-104">Wprowadzenie do programu F # w kodzie programu Visual Studio z Ionide</span><span class="sxs-lookup"><span data-stu-id="28bf9-104">Getting Started with F# in Visual Studio Code with Ionide</span></span>

<span data-ttu-id="28bf9-105">Możesz pisać F # [Visual Studio Code](https://code.visualstudio.com) z [wtyczki Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), aby uzyskać doskonałe środowisko IDE i platform, lekkie IntelliSense i refaktoryzacje podstawowego kodu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-105">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight IDE experience with IntelliSense and basic code refactorings.</span></span>  <span data-ttu-id="28bf9-106">Odwiedź stronę [Ionide.io](http://ionide.io) Aby dowiedzieć się więcej o pakiecie wtyczki.</span><span class="sxs-lookup"><span data-stu-id="28bf9-106">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28bf9-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="28bf9-107">Prerequisites</span></span>

<span data-ttu-id="28bf9-108">F # 4.0 lub nowszy musi być zainstalowany na tym komputerze do użycia Ionide.</span><span class="sxs-lookup"><span data-stu-id="28bf9-108">F# 4.0 or higher must be installed on your machine to use Ionide.</span></span>

<span data-ttu-id="28bf9-109">Musi mieć również [git zainstalowane](https://git-scm.com/download) i znajduje się na ŚCIEŻCE, aby użyć szablonów projektu w Ionide.</span><span class="sxs-lookup"><span data-stu-id="28bf9-109">You must also have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span>  <span data-ttu-id="28bf9-110">Można sprawdzić, czy jest poprawnie zainstalowany, wpisując `git` na naciśnięcie prompt.and polecenia **Enter**.</span><span class="sxs-lookup"><span data-stu-id="28bf9-110">You can verify that it is installed correctly by typing `git` at a command prompt.and pressing **Enter**.</span></span>

### <a name="windows"></a><span data-ttu-id="28bf9-111">Windows</span><span class="sxs-lookup"><span data-stu-id="28bf9-111">Windows</span></span>

<span data-ttu-id="28bf9-112">Jeśli w systemie Windows, masz dwie opcje instalacji F #.</span><span class="sxs-lookup"><span data-stu-id="28bf9-112">If you're on Windows, you have two options for installing F#.</span></span>

<span data-ttu-id="28bf9-113">Jeśli wcześniej zainstalowanego programu Visual Studio i nie ma F #, możesz [zainstalować narzędzia Visual F # Tools](get-started-visual-studio.md#installing-f).</span><span class="sxs-lookup"><span data-stu-id="28bf9-113">If you've already installed Visual Studio and don't have F#, you can [Install the Visual F# Tools](get-started-visual-studio.md#installing-f).</span></span>  <span data-ttu-id="28bf9-114">Spowoduje to zainstalowanie wszystkich składników niezbędnych do zapisu, kompilowania i wykonywania kodzie języka F #.</span><span class="sxs-lookup"><span data-stu-id="28bf9-114">This will install all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="28bf9-115">Jeśli nie chcesz zainstalować program Visual Studio, użyj poniższych instrukcji:</span><span class="sxs-lookup"><span data-stu-id="28bf9-115">If you prefer not to install Visual Studio, use the following instructions:</span></span>

1. <span data-ttu-id="28bf9-116">Zainstaluj [.NET Framework 4.5 lub wyższej](https://www.microsoft.com/en-US/download/details.aspx?id=30653) w przypadku systemu Windows 7.</span><span class="sxs-lookup"><span data-stu-id="28bf9-116">Install [.NET Framework 4.5 or higher](https://www.microsoft.com/en-US/download/details.aspx?id=30653) if you're running Windows 7.</span></span>  <span data-ttu-id="28bf9-117">Jeśli używasz systemu Windows 8 lub nowszym, nie trzeba w tym celu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-117">If you're using Windows 8 or higher, you do not need to do this.</span></span>

2. <span data-ttu-id="28bf9-118">Zainstaluj zestaw Windows SDK dla Twojego systemu operacyjnego:</span><span class="sxs-lookup"><span data-stu-id="28bf9-118">Install the Windows SDK for your OS:</span></span>

    * [<span data-ttu-id="28bf9-119">Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="28bf9-119">Windows 10 SDK</span></span>](https://dev.windows.com/en-US/downloads/windows-10-sdk)
    * [<span data-ttu-id="28bf9-120">Windows 8.1 SDK</span><span class="sxs-lookup"><span data-stu-id="28bf9-120">Windows 8.1 SDK</span></span>](http://msdn.microsoft.com/windows/desktop/bg162891)
    * [<span data-ttu-id="28bf9-121">Windows 8 SDK</span><span class="sxs-lookup"><span data-stu-id="28bf9-121">Windows 8 SDK</span></span>](http://msdn.microsoft.com/windows/hardware/hh852363.aspx)
    * [<span data-ttu-id="28bf9-122">Windows 7 SDK</span><span class="sxs-lookup"><span data-stu-id="28bf9-122">Windows 7 SDK</span></span>](http://www.microsoft.com/download/details.aspx?id=8279)

3. <span data-ttu-id="28bf9-123">Zainstaluj [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).</span><span class="sxs-lookup"><span data-stu-id="28bf9-123">Install the [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).</span></span>  <span data-ttu-id="28bf9-124">Należy również zainstalować [Microsoft kompilacji narzędzia 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).</span><span class="sxs-lookup"><span data-stu-id="28bf9-124">You may also need to install [Microsoft Build Tools 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).</span></span>

4. <span data-ttu-id="28bf9-125">Zainstaluj [narzędzia Visual F #](https://www.microsoft.com/en-us/download/details.aspx?id=48179).</span><span class="sxs-lookup"><span data-stu-id="28bf9-125">Install the [Visual F# Tools](https://www.microsoft.com/en-us/download/details.aspx?id=48179).</span></span>

<span data-ttu-id="28bf9-126">W 64-bitowym systemie Windows narzędzi i kompilatora znajdują się w folderze:</span><span class="sxs-lookup"><span data-stu-id="28bf9-126">On 64-bit Windows, the compiler and tools are located here:</span></span>

```
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

<span data-ttu-id="28bf9-127">W 32-bitowym systemie Windows narzędzia kompilatora znajdują się w folderze:</span><span class="sxs-lookup"><span data-stu-id="28bf9-127">On 32-bit Windows, the compiler tools are located here:</span></span>

```
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

<span data-ttu-id="28bf9-128">Ionide automatycznie wykrywa kompilatora i narzędzi, ale jeśli z jakiegoś powodu nie (na przykład Visual F # Tools zostały zainstalowane do innego katalogu), można ręcznie dodać folderu zawierającego (`...\Microsoft SDKs\F#\4.0`) do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="28bf9-128">Ionide automatically detects the compiler and tools, but if it doesn't for some reason (for example, the Visual F# Tools were installed to a different directory), you can manually add the containing folder (`...\Microsoft SDKs\F#\4.0`) to your PATH.</span></span>

### <a name="macos"></a><span data-ttu-id="28bf9-129">System macOS</span><span class="sxs-lookup"><span data-stu-id="28bf9-129">macOS</span></span>

<span data-ttu-id="28bf9-130">Na macOS, używa Ionide [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="28bf9-130">On macOS, Ionide uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="28bf9-131">Najprostszym sposobem zainstalowania Mono na macOS odbywa się za pośrednictwem oprogramowania Homebrew.</span><span class="sxs-lookup"><span data-stu-id="28bf9-131">The easiest way to install Mono on macOS is via Homebrew.</span></span>  <span data-ttu-id="28bf9-132">W terminalu, po prostu wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="28bf9-132">Simply type the following into your terminal:</span></span>

```
brew install mono
```

### <a name="linux"></a><span data-ttu-id="28bf9-133">Linux</span><span class="sxs-lookup"><span data-stu-id="28bf9-133">Linux</span></span>

<span data-ttu-id="28bf9-134">W systemie Linux, używa również Ionide [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="28bf9-134">On Linux, Ionide also uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="28bf9-135">Jeśli używasz Debian i Ubuntu, można użyć następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="28bf9-135">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="28bf9-136">Instalowanie dodatku Ionide i Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="28bf9-136">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="28bf9-137">Można zainstalować program Visual Studio Code z [code.visualstudio.com](https://code.visualstudio.com) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="28bf9-137">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>  <span data-ttu-id="28bf9-138">Po wykonaniu tej istnieją dwa sposoby znajdowania Ionide wtyczki:</span><span class="sxs-lookup"><span data-stu-id="28bf9-138">After that, there are two ways to find the Ionide plugin:</span></span>

1. <span data-ttu-id="28bf9-139">Użyj polecenia palety (Ctrl + Shift + P w systemie Windows, ⌘ + Shift + P na macOS, Ctrl + Shift + P w systemie Linux) i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="28bf9-139">Use the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

    ```
    >ext install Ionide
    ```

2. <span data-ttu-id="28bf9-140">Kliknij ikonę rozszerzenia i wyszukaj "Ionide":</span><span class="sxs-lookup"><span data-stu-id="28bf9-140">Click the Extensions icon and search for "Ionide":</span></span>

    ![](media/getting-started-vscode/vscode-ext.png)

<span data-ttu-id="28bf9-141">Tylko wtyczki, wymagana jest obsługa F # w programie Visual Studio Code [języka fsharp Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="28bf9-141">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>  <span data-ttu-id="28bf9-142">Jednakże można także zainstalować [SFAŁSZOWANA Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) i uzyskać [SFAŁSZOWAĆ](http://fsharp.github.io/FAKE/) obsługuje i [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) uzyskanie [Paket](https://fsprojects.github.io/Paket/) obsługuje.</span><span class="sxs-lookup"><span data-stu-id="28bf9-142">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) and to get [FAKE](http://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span>  <span data-ttu-id="28bf9-143">FAŁSZYWE i Paket są dodatkowe F # społeczności narzędzia do tworzenia projektów i zarządzanie nimi zależności, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="28bf9-143">FAKE and Paket are additonal F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="28bf9-144">Tworzenie pierwszego projektu z Ionide</span><span class="sxs-lookup"><span data-stu-id="28bf9-144">Creating your first project with Ionide</span></span>

<span data-ttu-id="28bf9-145">Aby utworzyć nowy projekt F #, Otwórz program Visual Studio Code w nowym folderze (można określić nazwę dowolne).</span><span class="sxs-lookup"><span data-stu-id="28bf9-145">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

![](media/getting-started-vscode/vscode-open-dir.png)

<span data-ttu-id="28bf9-146">Następnie otwórz palety polecenia (Ctrl + Shift + P w systemie Windows, ⌘ + Shift + P na macOS, Ctrl + Shift + P w systemie Linux) i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="28bf9-146">Next, open the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

```
>f#: New Project
```

<span data-ttu-id="28bf9-147">Jest to obsługiwane przez [FORGE](https://github.com/fsharp-editing/Forge) projektu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-147">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>  <span data-ttu-id="28bf9-148">Powinny pojawić się dane podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="28bf9-148">You should see something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
<span data-ttu-id="28bf9-149">Jeśli nie widzisz powyższego, spróbuj odświeżyć szablony, uruchamiając następujące polecenie w palecie polecenia: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="28bf9-149">If you don't see the above, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="28bf9-150">Wybierz opcję "F #: nowego projektu" za pomocą **Enter**, która spowoduje przejście do tego kroku:</span><span class="sxs-lookup"><span data-stu-id="28bf9-150">Select "F#: New Project" by hitting **Enter**, which will take you to this step:</span></span>

![](media/getting-started-vscode/vscode-proj-type.png)

<span data-ttu-id="28bf9-151">Wybierz opcję szablon dla określonego typu projektu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-151">This will select a template for a specific type of project.</span></span>  <span data-ttu-id="28bf9-152">Istnieje kilka opcji, takich jak [FsLab](http://fslab.org) szablon do analizy danych lub [Suave](https://suave.io) szablon programowania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="28bf9-152">There are quite a few options here, such as an [FsLab](http://fslab.org) template for Data Science or [Suave](https://suave.io) template for Web Programming.</span></span>  <span data-ttu-id="28bf9-153">W tym artykule wykorzystano `classlib` szablon, więc podkreślenie i naciśnij **Enter**.</span><span class="sxs-lookup"><span data-stu-id="28bf9-153">This article uses the `classlib` template, so highlight that and hit **Enter**.</span></span>  <span data-ttu-id="28bf9-154">Następnie zostanie osiągnąć następny krok:</span><span class="sxs-lookup"><span data-stu-id="28bf9-154">You will then reach the following step:</span></span>

![](media/getting-started-vscode/vscode-new-dir.png)

<span data-ttu-id="28bf9-155">Dzięki temu można utworzyć projektu w innym katalogu, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="28bf9-155">This lets you create the project in a different directory, if you like.</span></span>  <span data-ttu-id="28bf9-156">Pozostaw pole puste, teraz.</span><span class="sxs-lookup"><span data-stu-id="28bf9-156">Leave it blank for now.</span></span>  <span data-ttu-id="28bf9-157">Projekt zostanie utworzony w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-157">It will create the project in the current directory.</span></span>  <span data-ttu-id="28bf9-158">Po naciśnięciu **Enter**, osiągną następujący krok:</span><span class="sxs-lookup"><span data-stu-id="28bf9-158">Once you press **Enter**, you will reach the following step:</span></span>

![](media/getting-started-vscode/vscode-proj-name.png)

<span data-ttu-id="28bf9-159">Dzięki temu można nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-159">This lets you name your project.</span></span>  <span data-ttu-id="28bf9-160">F # używa [przypadku Pascal](http://c2.com/cgi/wiki?PascalCase) dla nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-160">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span>  <span data-ttu-id="28bf9-161">W tym artykule wykorzystano `ClassLibraryDemo` jako nazwy.</span><span class="sxs-lookup"><span data-stu-id="28bf9-161">This article uses `ClassLibraryDemo` as the name.</span></span>  <span data-ttu-id="28bf9-162">Po wprowadzeniu nazwy dla projektu, kliknij przycisk **Enter**.</span><span class="sxs-lookup"><span data-stu-id="28bf9-162">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="28bf9-163">Po wykonaniu poprzednich kroków kroku, należy pobrać Visual Studio Code obszaru roboczego po lewej stronie do wyglądać mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="28bf9-163">If you followed the previous step steps, you should get the Visual Studio Code Workspace on the left-hand side to look something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

<span data-ttu-id="28bf9-164">Ten szablon generuje kilka rzeczy, które można znaleźć przydatne:</span><span class="sxs-lookup"><span data-stu-id="28bf9-164">This template generates a few things you'll find useful:</span></span>

1. <span data-ttu-id="28bf9-165">F # projektu, underneath `ClassLibraryDemo` folderu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-165">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="28bf9-166">Dodawanie pakietów za pomocą struktury poprawny katalog [ `Paket` ](http://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="28bf9-166">The correct directory structure for adding packages via [`Paket`](http://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="28bf9-167">Obsługujący wiele platform kompilacji skryptu o [ `FAKE` ](http://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="28bf9-167">A cross-platform build script with [`FAKE`](http://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="28bf9-168">`paket.exe` Plik wykonywalny, który można pobrać pakietów i rozpoznać zależności dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="28bf9-168">The `paket.exe` executable which can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="28bf9-169">A `.gitignore` plik, jeśli chcesz dodać ten projekt do kontroli źródła na podstawie Git.</span><span class="sxs-lookup"><span data-stu-id="28bf9-169">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="28bf9-170">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="28bf9-170">Writing some code</span></span>

<span data-ttu-id="28bf9-171">Otwórz *ClassLibraryDemo* folderu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-171">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="28bf9-172">Powinny pojawić się następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="28bf9-172">You should see the following files:</span></span>

1. <span data-ttu-id="28bf9-173">`ClassLibraryDemo.fs`, F # pliku z implementacją z klasą zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="28bf9-173">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="28bf9-174">`CassLibraryDemo.fsproj`, F # plik projektu używany do tworzenia tego projektu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-174">`CassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="28bf9-175">`Script.fsx`, F # pliku skryptu, który ładuje plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="28bf9-175">`Script.fsx`, an F# script file which loads the source file.</span></span>
4. <span data-ttu-id="28bf9-176">`paket.references`, plik Paket, który określa zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-176">`paket.references`, a Paket file which specifies the project dependencies.</span></span>

<span data-ttu-id="28bf9-177">Otwórz `Script.fsx`i Dodaj następujący kod na końcu:</span><span class="sxs-lookup"><span data-stu-id="28bf9-177">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="28bf9-178">Ta funkcja konwertuje wyraz do formularza z [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="28bf9-178">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span>  <span data-ttu-id="28bf9-179">Następnym krokiem jest do oceny przy użyciu języka F # Interactive (FSI).</span><span class="sxs-lookup"><span data-stu-id="28bf9-179">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="28bf9-180">Zaznacz całą funkcję (powinien być 11 wierszy).</span><span class="sxs-lookup"><span data-stu-id="28bf9-180">Highlight the entire function (it should be 11 lines long).</span></span>  <span data-ttu-id="28bf9-181">Po jego zostanie wyróżniona, przytrzymaj **Alt** klucza i trafień **Enter**.</span><span class="sxs-lookup"><span data-stu-id="28bf9-181">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span>  <span data-ttu-id="28bf9-182">Można zauważyć okno wyskakujące poniżej, a powinny mieć podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="28bf9-182">You'll notice a window pop up below, and it should show something like this:</span></span>

![](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="28bf9-183">Czy to trzy czynności:</span><span class="sxs-lookup"><span data-stu-id="28bf9-183">This did three things:</span></span>

1. <span data-ttu-id="28bf9-184">Proces FSI jego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="28bf9-184">It started the FSI process.</span></span>
2. <span data-ttu-id="28bf9-185">Wyróżniony kod go wysyłane za pośrednictwem procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="28bf9-185">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="28bf9-186">Proces FSI oceniane wysyłane przez kod.</span><span class="sxs-lookup"><span data-stu-id="28bf9-186">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="28bf9-187">Ponieważ był wysyłany za pośrednictwem [funkcja](../language-reference/functions/index.md), można teraz wywołać tej funkcji z FSI!</span><span class="sxs-lookup"><span data-stu-id="28bf9-187">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span>  <span data-ttu-id="28bf9-188">W oknie interaktywnym wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="28bf9-188">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="28bf9-189">Powinny być widoczne następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28bf9-189">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="28bf9-190">Teraz spróbujmy się od samogłosek jako pierwszą literę.</span><span class="sxs-lookup"><span data-stu-id="28bf9-190">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="28bf9-191">Wprowadź następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="28bf9-191">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="28bf9-192">Powinny być widoczne następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28bf9-192">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="28bf9-193">Funkcja może działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="28bf9-193">The function appears to be working as expected.</span></span>  <span data-ttu-id="28bf9-194">Gratulacje, po prostu zapisane pierwszej funkcji F # w programie Visual Studio Code i oceniać za jego pomocą FSI!</span><span class="sxs-lookup"><span data-stu-id="28bf9-194">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="28bf9-195">Jak można zauważyć, wiersze FSI kończą się `;;`.</span><span class="sxs-lookup"><span data-stu-id="28bf9-195">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span>  <span data-ttu-id="28bf9-196">Jest to spowodowane FSI umożliwia wprowadzanie wielu wierszy.</span><span class="sxs-lookup"><span data-stu-id="28bf9-196">This is because FSI allows you to enter multiple lines.</span></span>  <span data-ttu-id="28bf9-197">`;;` Na końcu umożliwia FSI wiedzieć, po zakończeniu kod.</span><span class="sxs-lookup"><span data-stu-id="28bf9-197">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="28bf9-198">Wyjaśniający kodu</span><span class="sxs-lookup"><span data-stu-id="28bf9-198">Explaining the code</span></span>

<span data-ttu-id="28bf9-199">Jeśli nie masz pewności o kodzie faktycznie czynności, poniżej przedstawiono krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="28bf9-199">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="28bf9-200">Jak widać, `toPigLatin` jest funkcję, która przyjmuje word jako dane wejściowe i konwertuje ją na Pig Latin reprezentację wyrazie.</span><span class="sxs-lookup"><span data-stu-id="28bf9-200">As you can see, `toPigLatin` is a function which takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span>  <span data-ttu-id="28bf9-201">Dla tej reguły są następujące:</span><span class="sxs-lookup"><span data-stu-id="28bf9-201">The rules for this are as follows:</span></span>

<span data-ttu-id="28bf9-202">Jeśli pierwszy znak w wyrazie rozpoczyna się od samogłosek, należy dodać "yay" do końca słowa.</span><span class="sxs-lookup"><span data-stu-id="28bf9-202">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span>  <span data-ttu-id="28bf9-203">Jeśli go nie zaczyna się od samogłosek, umieść ten pierwszy znak na końcu Word i "ay" Dodaj do niej.</span><span class="sxs-lookup"><span data-stu-id="28bf9-203">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="28bf9-204">Można zauważyć następujące opcje w FSI:</span><span class="sxs-lookup"><span data-stu-id="28bf9-204">You may have noticed the following in FSI:</span></span>

```
val toPigLatin : word:string -> string
```

<span data-ttu-id="28bf9-205">Ta stwierdza, że `toPigLatin` jest funkcją, która przyjmuje `string` jako dane wejściowe (nazywane `word`) i zwraca innego `string`.</span><span class="sxs-lookup"><span data-stu-id="28bf9-205">This states that `toPigLatin` is a function which takes in a `string` as input (called `word`), and returns another `string`.</span></span>  <span data-ttu-id="28bf9-206">Jest to nazywane [podpis typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawowe technologie języka F #, która jest kluczem do zrozumienia kodzie języka F #.</span><span class="sxs-lookup"><span data-stu-id="28bf9-206">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span>  <span data-ttu-id="28bf9-207">Należy także zauważyć, to jeśli Aktywuj funkcji w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="28bf9-207">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="28bf9-208">W treści funkcji można zauważyć dwa różne części:</span><span class="sxs-lookup"><span data-stu-id="28bf9-208">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="28bf9-209">Wewnętrzna funkcja wywoływana `isVowel`, która określa, czy dany znak (`c`) jest samogłoskę przez sprawdzenie, czy pasujący wzorców podana za pośrednictwem [dopasowanie wzorca](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="28bf9-209">An inner function, called `isVowel`, which determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="28bf9-210">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Wyrażenie, które sprawdza, czy pierwszy znak jest samogłoskę i konstruuje wartość zwracaną poza wprowadzanie znaków na podstawie pierwszego znaku, gdy był samogłoskę lub nie:</span><span class="sxs-lookup"><span data-stu-id="28bf9-210">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression which checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="28bf9-211">Przepływ `toPigLatin` jest w związku z tym:</span><span class="sxs-lookup"><span data-stu-id="28bf9-211">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="28bf9-212">Sprawdź, czy pierwszy znak wejściowy word samogłoskę.</span><span class="sxs-lookup"><span data-stu-id="28bf9-212">Check if the first character of the input word is a vowel.</span></span>  <span data-ttu-id="28bf9-213">Jeśli tak jest, Dołącz "yay" do końca słowa.</span><span class="sxs-lookup"><span data-stu-id="28bf9-213">If it is, attach "yay" to the end of the word.</span></span>  <span data-ttu-id="28bf9-214">W przeciwnym razie umieść ten pierwszy znak na końcu Word i "ay" Dodaj do niej.</span><span class="sxs-lookup"><span data-stu-id="28bf9-214">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="28bf9-215">Brak końcowego rzecz do Zwróć uwagę na ten temat: Brak nie jawna instrukcja ma zostać zwrócony przez funkcję, w odróżnieniu od wielu innych języków tam.</span><span class="sxs-lookup"><span data-stu-id="28bf9-215">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span>  <span data-ttu-id="28bf9-216">To dlatego F # jest oparte na wyrażeniach oraz ostatnich wyrażenie w treści funkcji jest zwracana wartość.</span><span class="sxs-lookup"><span data-stu-id="28bf9-216">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span>  <span data-ttu-id="28bf9-217">Ponieważ `if..then..else` jest wyrażenie, treść `then` bloku lub treści `else` bloku zostanie zwrócony w zależności od wartości wejściowej.</span><span class="sxs-lookup"><span data-stu-id="28bf9-217">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="28bf9-218">Przenoszenie kodu skryptu do pliku implementacji</span><span class="sxs-lookup"><span data-stu-id="28bf9-218">Moving your script code into the implementation file</span></span>

<span data-ttu-id="28bf9-219">Poprzednich sekcjach, w tym artykule przedstawiono typowe pierwszą czynnością przy tworzeniu kodzie języka F #: pisanie początkowej funkcji i jej wykonanie interakcyjnie z FSI.</span><span class="sxs-lookup"><span data-stu-id="28bf9-219">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span>  <span data-ttu-id="28bf9-220">Jest to nazywane REPL-driven development, gdzie oznacza REPL "Pętlę odczytu oceny-drukarek".</span><span class="sxs-lookup"><span data-stu-id="28bf9-220">This is known as REPL-driven development, where REPL stands for "Read-Evaluate-Print Loop".</span></span>  <span data-ttu-id="28bf9-221">Jest to dobry sposób na wypróbowanie funkcji, aż do uzyskania elementu pracy.</span><span class="sxs-lookup"><span data-stu-id="28bf9-221">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="28bf9-222">Następny krok w REPL-driven development, jest Przenieś pracy kod do pliku implementacji F #.</span><span class="sxs-lookup"><span data-stu-id="28bf9-222">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span>  <span data-ttu-id="28bf9-223">Go można następnie można skompilować przez kompilator języka F # do zestawu, które mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="28bf9-223">It can then be compiled by the F# compiler into an assembly which can be executed.</span></span>

<span data-ttu-id="28bf9-224">Aby rozpocząć, otwórz `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="28bf9-224">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="28bf9-225">Można zauważyć, że kod jest już istnieje.</span><span class="sxs-lookup"><span data-stu-id="28bf9-225">You'll notice that some code is already in there.</span></span>  <span data-ttu-id="28bf9-226">Przejdź dalej i usunąć definicji klasy, ale pamiętaj pozostawić [ `namespace` ](../language-reference/namespaces.md) deklaracji u góry.</span><span class="sxs-lookup"><span data-stu-id="28bf9-226">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="28bf9-227">Następnie należy utworzyć nowy [ `module` ](../language-reference/modules.md) o nazwie `PigLatin` i skopiuj `toPigLatin` funkcji w nim sposób:</span><span class="sxs-lookup"><span data-stu-id="28bf9-227">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="28bf9-228">Jest to jedna z wielu sposobów, jeśli chcesz także wywoływanie kodu z języka C# lub Visual Basic, projekty można organizować funkcje w kodzie języka F # i typowym podejściem.</span><span class="sxs-lookup"><span data-stu-id="28bf9-228">This is one of the many ways you can organize functions in F# code, and a common approach if you also want to call your code from C# or Visual Basic projects.</span></span>

<span data-ttu-id="28bf9-229">Następnie otwórz folder `Script.fsx` ponownie, a następnie usuń całą `toPigLatin` działać, ale pamiętaj zachować następujące dwa wiersze w pliku:</span><span class="sxs-lookup"><span data-stu-id="28bf9-229">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="28bf9-230">Pierwszy wiersz jest wymagany dla skryptów do załadowania FSI `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="28bf9-230">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="28bf9-231">Drugi wiersz jest udogodnienie: pomijając go jest opcjonalne, ale będzie musiał podać `open ClassLibraryDemo` w oknie FSI, jeśli chcesz wyświetlić `ToPigLatin` modułu do zakresu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-231">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="28bf9-232">Następnie w oknie FSI, wywołaj funkcję z `PigLatin` moduł, który został zdefiniowany wcześniej:</span><span class="sxs-lookup"><span data-stu-id="28bf9-232">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="28bf9-233">Powodzenie!</span><span class="sxs-lookup"><span data-stu-id="28bf9-233">Success!</span></span>  <span data-ttu-id="28bf9-234">Pobierz wyniki przed, ale teraz załadowanego z pliku implementacji F #.</span><span class="sxs-lookup"><span data-stu-id="28bf9-234">You get the same results as before, but now loaded from an F# implementation file.</span></span>  <span data-ttu-id="28bf9-235">W tym miejscu główna różnica polega na tym, że pliki źródłowe języka F # są skompilowane w zestawy, które mogą być wykonywane w dowolnym miejscu, nie tylko w FSI.</span><span class="sxs-lookup"><span data-stu-id="28bf9-235">The major difference here is that F# source files are compiled into assemblies which can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="28bf9-236">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="28bf9-236">Summary</span></span>

<span data-ttu-id="28bf9-237">W tym artykule kiedy znasz już:</span><span class="sxs-lookup"><span data-stu-id="28bf9-237">In this article, you've learned:</span></span>

1. <span data-ttu-id="28bf9-238">Jak skonfigurować program Visual Studio Code z Ionide.</span><span class="sxs-lookup"><span data-stu-id="28bf9-238">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="28bf9-239">Jak utworzyć pierwszy projekt F # z Ionide.</span><span class="sxs-lookup"><span data-stu-id="28bf9-239">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="28bf9-240">Jak używać F # skryptów do zapisywania pierwszej funkcji F # w Ionide i wykonaj go w FSI.</span><span class="sxs-lookup"><span data-stu-id="28bf9-240">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="28bf9-241">Jak przeprowadzić migrację skryptu kodu źródłowego języka F #, a następnie wywołać kodu z FSI.</span><span class="sxs-lookup"><span data-stu-id="28bf9-241">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="28bf9-242">Teraz jest wyposażona w kodzie znacznie więcej F # za pomocą programu Visual Studio Code i Ionide.</span><span class="sxs-lookup"><span data-stu-id="28bf9-242">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="28bf9-243">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="28bf9-243">Troubleshooting</span></span>

<span data-ttu-id="28bf9-244">Poniżej przedstawiono kilka sposobów, można rozwiązać niektóre problemy, które mogą być uruchamiane na:</span><span class="sxs-lookup"><span data-stu-id="28bf9-244">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="28bf9-245">Aby uzyskać funkcji Ionide edycji kodu, plikach języka F # trzeba zapisać na dysku i wewnątrz folderu, który jest otwarty w obszarze roboczym Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="28bf9-245">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="28bf9-246">Jeśli zostały wprowadzone zmiany w systemie lub zainstalowane wymagania wstępne Ionide z programu Visual Studio Code Otwórz, uruchom ponownie program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="28bf9-246">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="28bf9-247">Sprawdź, czy można użyć kompilator języka F # i F # interactive w wierszu polecenia bez w pełni kwalifikowaną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="28bf9-247">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span>  <span data-ttu-id="28bf9-248">Możesz to zrobić, wpisując `fsc` w wierszu polecenia, aby uzyskać kompilator języka F # i `fsi` lub `fsharpi` Visual F # tools w systemach Windows i Mono na system Mac/Linux, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="28bf9-248">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="28bf9-249">Jeśli masz nieprawidłowe znaki w katalogach projektu Ionide może nie działać.</span><span class="sxs-lookup"><span data-stu-id="28bf9-249">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="28bf9-250">Jeśli jest to możliwe, Zmień nazwy katalogów projektu.</span><span class="sxs-lookup"><span data-stu-id="28bf9-250">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="28bf9-251">Brak polecenia Ionide pracy, sprawdź Twojej [powiązań kluczy programu Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) aby zobaczyć, czy jest zastępowanie ich przypadkowo.</span><span class="sxs-lookup"><span data-stu-id="28bf9-251">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="28bf9-252">Jeśli Ionide jest dzielony na komputerze, a żadne z powyższych poprawił problemu, spróbuj usunąć `ionide-fsharp` katalogu na komputerze i ponowne zainstalowanie zestawu dodatku.</span><span class="sxs-lookup"><span data-stu-id="28bf9-252">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="28bf9-253">Ionide to projekt typu open source, wbudowane i obsługiwana przez członków społeczności F #.</span><span class="sxs-lookup"><span data-stu-id="28bf9-253">Ionide is an open source project built and maintained by members of the F# community.</span></span>  <span data-ttu-id="28bf9-254">Sprawdź zgłaszania problemów i możesz zająć się na [Ionide VSCode: repozytorium GitHub języka FSharp](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="28bf9-254">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="28bf9-255">Jeśli masz problem do raportu, postępuj [instrukcje dotyczące pobierania dzienników do użycia podczas raportowania problemu](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="28bf9-255">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="28bf9-256">Możesz również poprosić Aby uzyskać dalszą pomoc od Ionide deweloperów i F # społeczności w [kanału Ionide Gitter](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="28bf9-256">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="28bf9-257">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="28bf9-257">Next steps</span></span>

<span data-ttu-id="28bf9-258">Aby dowiedzieć się więcej na temat języka F # i funkcji języka, zapoznaj się [samouczek programu F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="28bf9-258">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="28bf9-259">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28bf9-259">See also</span></span>

[<span data-ttu-id="28bf9-260">Samouczek języka F #</span><span class="sxs-lookup"><span data-stu-id="28bf9-260">Tour of F#</span></span>](../tour.md)

[<span data-ttu-id="28bf9-261">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="28bf9-261">F# Language Reference</span></span>](../language-reference/index.md)

[<span data-ttu-id="28bf9-262">Funkcje</span><span class="sxs-lookup"><span data-stu-id="28bf9-262">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="28bf9-263">Moduły</span><span class="sxs-lookup"><span data-stu-id="28bf9-263">Modules</span></span>](../language-reference/modules.md)

[<span data-ttu-id="28bf9-264">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="28bf9-264">Namespaces</span></span>](../language-reference/namespaces.md)

[<span data-ttu-id="28bf9-265">Ionide VSCode: języka FSharp</span><span class="sxs-lookup"><span data-stu-id="28bf9-265">Ionide-VSCode: FSharp</span></span>](https://github.com/ionide/ionide-vscode-fsharp)
