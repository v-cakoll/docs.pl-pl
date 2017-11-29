---
title: "Wprowadzenie do języka C# i Visual Studio Code — przewodnik C#"
description: "Informacje o sposobie tworzenia i debugowania w języku C# za pomocą programu Visual Studio Code pierwszej aplikacji platformy .NET Core."
keywords: "C#, Get pracę, nabycia, instalacji programu Visual Studio Code Cross Platform"
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.openlocfilehash: 3a9de689946507e4b6d89f684461d65049b3375a
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="38cdd-104">Wprowadzenie do języka C# i Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="38cdd-104">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="38cdd-105">Oprogramowanie .NET core umożliwia szybka, modularna platforma do tworzenia aplikacji działających w systemach Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="38cdd-105">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="38cdd-106">Za pomocą programu Visual Studio Code rozszerzenia C# Aby uzyskać zaawansowane edytowania z pełną obsługę funkcji IntelliSense języka C# (uzupełnianie kodu inteligentne) i debugowania.</span><span class="sxs-lookup"><span data-stu-id="38cdd-106">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="38cdd-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="38cdd-107">Prerequisites</span></span>

1. <span data-ttu-id="38cdd-108">Zainstaluj [kodu programu Visual Studio](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="38cdd-108">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="38cdd-109">Zainstaluj [.NET Core SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="38cdd-109">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="38cdd-110">Zainstaluj [C# rozszerzenia](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) z Visual Studio Marketplace kodu.</span><span class="sxs-lookup"><span data-stu-id="38cdd-110">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) from the Visual Studio Code Marketplace.</span></span>

## <a name="hello-world"></a><span data-ttu-id="38cdd-111">Witaj Świecie</span><span class="sxs-lookup"><span data-stu-id="38cdd-111">Hello World</span></span>

<span data-ttu-id="38cdd-112">Rozpocznijmy prosty program .NET Core "Hello World":</span><span class="sxs-lookup"><span data-stu-id="38cdd-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="38cdd-113">Otwórz projekt:</span><span class="sxs-lookup"><span data-stu-id="38cdd-113">Open a project:</span></span>

    * <span data-ttu-id="38cdd-114">Otwórz kod programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="38cdd-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="38cdd-115">Kliknij ikonę Explorer z menu po lewej stronie, a następnie kliknij przycisk **Otwórz Folder**.</span><span class="sxs-lookup"><span data-stu-id="38cdd-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="38cdd-116">Wybierz **pliku** > **Otwórz Folder** z poziomu menu głównego, aby otworzyć folder ma projektu C# w i kliknij przycisk **wybierz Folder**.</span><span class="sxs-lookup"><span data-stu-id="38cdd-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="38cdd-117">W naszym przykładzie tworzymy folderu dla naszych projektu o nazwie *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="38cdd-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. <span data-ttu-id="38cdd-119">Inicjowanie projektu C#:</span><span class="sxs-lookup"><span data-stu-id="38cdd-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="38cdd-120">Otwórz Terminal zintegrowane z kodem Visual Studio, wybierając **widoku** > **zintegrowane Terminal** z poziomu menu głównego.</span><span class="sxs-lookup"><span data-stu-id="38cdd-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="38cdd-121">W oknie terminalu wpisz `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="38cdd-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="38cdd-122">To polecenie tworzy `Program.cs` plik w folderze z programem proste "Hello World" już zapisane razem z pliku projektu C# o nazwie `HelloWorld.csproj`.</span><span class="sxs-lookup"><span data-stu-id="38cdd-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![Nowe polecenie dotnet](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="38cdd-124">Aby usunąć zasoby kompilacji:</span><span class="sxs-lookup"><span data-stu-id="38cdd-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="38cdd-125">Aby uzyskać **.NET Core 1.x**, typ `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="38cdd-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="38cdd-126">Uruchomiona `dotnet restore` zapewnia dostęp do wymagane pakiety platformy .NET Core, które są wymagane, aby skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="38cdd-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Polecenie restore dotnet](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="38cdd-128">Uruchom program "Hello World":</span><span class="sxs-lookup"><span data-stu-id="38cdd-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="38cdd-129">Typ `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="38cdd-129">Type `dotnet run`.</span></span> 

      ![Dotnet, uruchom polecenie](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="38cdd-131">Można również obejrzeć krótki samouczek wideo, aby uzyskać dalszą pomoc Instalatora na [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), lub [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="38cdd-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="38cdd-132">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="38cdd-132">Debug</span></span>

1. <span data-ttu-id="38cdd-133">Otwórz *Program.cs* , klikając go.</span><span class="sxs-lookup"><span data-stu-id="38cdd-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="38cdd-134">Przy pierwszym otwarciu pliku C# w programie Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) ładuje w edytorze.</span><span class="sxs-lookup"><span data-stu-id="38cdd-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otwórz plik Program.cs](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="38cdd-136">Visual Studio Code powinien monit o dodanie brakujące zasoby do tworzenia i debugowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38cdd-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="38cdd-137">Wybierz **tak**.</span><span class="sxs-lookup"><span data-stu-id="38cdd-137">Select **Yes**.</span></span> 

    ![Monituj o brakujących zasobów](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="38cdd-139">Aby otworzyć widok debugowania, kliknij ikonę debugowanie z menu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="38cdd-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otwórz kartę debugowania](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="38cdd-141">Zlokalizuj zieloną strzałkę u góry okienka.</span><span class="sxs-lookup"><span data-stu-id="38cdd-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="38cdd-142">Upewnij się, że ma listy rozwijanej obok niej `.NET Core Launch (console)` wybrane.</span><span class="sxs-lookup"><span data-stu-id="38cdd-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![Wybieranie platformy .NET Core](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="38cdd-144">Dodaj punkt przerwania do projektu, klikając **marginesu edytora**, czyli miejsce po lewej stronie numerów wierszy w edytorze, obok wiersza 9.</span><span class="sxs-lookup"><span data-stu-id="38cdd-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9.</span></span>

    ![Ustawienia punktu przerwania](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="38cdd-146">Aby rozpocząć debugowanie, wybierz <kbd>F5</kbd> lub zieloną strzałkę.</span><span class="sxs-lookup"><span data-stu-id="38cdd-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="38cdd-147">Debuger zatrzymuje wykonanie programu, po osiągnięciu punktu przerwania ustawionych w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="38cdd-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="38cdd-148">Podczas debugowania, możesz wyświetlić zmiennych lokalnych w górnym okienku po lewej stronie lub za pomocą konsoli debugowania.</span><span class="sxs-lookup"><span data-stu-id="38cdd-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

    ![Uruchom i debugowania](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="38cdd-150">Wybierz zieloną strzałkę u góry, aby kontynuować, debugowanie, lub czerwonego kwadratu u góry, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="38cdd-150">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP] 
> <span data-ttu-id="38cdd-151">Aby uzyskać więcej informacji oraz wskazówki na debugowanie .NET Core za pomocą OmniSharp w programie Visual Studio Code, zobacz [instrukcje dotyczące konfigurowania debuger .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="38cdd-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38cdd-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38cdd-152">See also</span></span>
<span data-ttu-id="38cdd-153">[Konfigurowanie programu Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span><span class="sxs-lookup"><span data-stu-id="38cdd-153">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span></span>  
[<span data-ttu-id="38cdd-154">Profilowanie kodu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="38cdd-154">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
