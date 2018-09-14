---
title: Publikowanie aplikacji Hello World w programie Visual Studio 2017
description: Publikowanie tworzy zbiór plików, które są wymagane do uruchamiania aplikacji.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet
ms.openlocfilehash: e44ae69c9cd8f0767e369791737cef9b4c33f963
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45593143"
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="01e7c-103">Publikowanie aplikacji Hello World w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="01e7c-103">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="01e7c-104">W [kompilacji C# aplikacji Hello World z platformą .NET Core w programie Visual Studio 2017](with-visual-studio.md) lub [tworzenie aplikacji Visual Basic Hello World z platformą .NET Core w programie Visual Studio 2017](vb-with-visual-studio.md), utworzoną aplikację konsolową w języku Hello World .</span><span class="sxs-lookup"><span data-stu-id="01e7c-104">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="01e7c-105">W [debugowania języka C# aplikacji Hello World w programie Visual Studio 2017](debugging-with-visual-studio.md), przetestowane za pomocą debugera programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="01e7c-105">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="01e7c-106">Teraz, gdy masz pewność, że działa zgodnie z oczekiwaniami, możesz ją opublikować tak, aby uruchomić ją innym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="01e7c-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="01e7c-107">Publikowanie tworzy zbiór plików, które są wymagane do uruchamiania aplikacji i plików można wdrożyć, kopiując je na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="01e7c-107">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="01e7c-108">Aby opublikować, a następnie uruchom aplikację:</span><span class="sxs-lookup"><span data-stu-id="01e7c-108">To publish and run your application:</span></span> 

1. <span data-ttu-id="01e7c-109">Upewnij się, że Visual Studio jest tworzenie wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01e7c-109">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="01e7c-110">W razie potrzeby zmień ustawienie konfiguracji kompilacji, na pasku narzędzi z **debugowania** do **wersji**.</span><span class="sxs-lookup"><span data-stu-id="01e7c-110">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Visual Studio pasek narzędzi](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="01e7c-112">Kliknij prawym przyciskiem myszy **HelloWorld** projektu (nie rozwiązanie HelloWorld), a następnie wybierz **Publikuj** z menu.</span><span class="sxs-lookup"><span data-stu-id="01e7c-112">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="01e7c-113">Możesz również wybrać **publikowania HelloWorld** z głównym programu Visual Studio **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="01e7c-113">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Visual Studio pasek narzędzi](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio pasek narzędzi](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="01e7c-116">Otwórz okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="01e7c-116">Open a console window.</span></span> <span data-ttu-id="01e7c-117">Na przykład w **wpisz tutaj, aby wyszukać** tekstu pola na pasku zadań Windows, należy wprowadzić `Command Prompt` (lub `cmd` w skrócie) i Otwórz okno konsoli, wybierając **polecenia** pulpitu Aplikacja lub naciskając klawisz Enter, jeśli została wybrana w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="01e7c-117">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="01e7c-118">Przejdź do aplikacji opublikowanych w `bin\release\PublishOutput` podkatalogu katalogu projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01e7c-118">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="01e7c-119">Jak pokazano na poniższej ilustracji, opublikowane dane wyjściowe zawiera następujące cztery pliki:</span><span class="sxs-lookup"><span data-stu-id="01e7c-119">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="01e7c-120">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="01e7c-120">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="01e7c-121">Plik zależności środowiska uruchomieniowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01e7c-121">The application's runtime dependencies file.</span></span> <span data-ttu-id="01e7c-122">Definiuje składniki platformy .NET Core i bibliotek (w tym biblioteki dołączanej dynamicznie, która zawiera aplikację) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01e7c-122">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="01e7c-123">Aby uzyskać więcej informacji, zobacz [plików konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="01e7c-123">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="01e7c-124">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="01e7c-124">*HelloWorld.dll*</span></span>

         <span data-ttu-id="01e7c-125">Plik, który zawiera aplikację.</span><span class="sxs-lookup"><span data-stu-id="01e7c-125">The file that contains your application.</span></span> <span data-ttu-id="01e7c-126">Jest biblioteka dołączana dynamicznie, który może zostać wykonany, wprowadzając `dotnet HelloWorld.dll` polecenia w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="01e7c-126">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="01e7c-127">*HelloWorld.pdb* (opcjonalnie na potrzeby wdrożenia)</span><span class="sxs-lookup"><span data-stu-id="01e7c-127">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="01e7c-128">Plik, który zawiera symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="01e7c-128">A file that contains debug symbols.</span></span> <span data-ttu-id="01e7c-129">Aby wdrożyć ten plik, wraz z aplikacją, nie są wymagane, mimo że w przypadku, gdy konieczne zdebugowanie opublikowanej wersji aplikacji należy go zapisać.</span><span class="sxs-lookup"><span data-stu-id="01e7c-129">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="01e7c-130">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="01e7c-130">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="01e7c-131">Plik konfiguracji środowiska uruchomieniowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01e7c-131">The application's runtime configuration file.</span></span> <span data-ttu-id="01e7c-132">Go identyfikuje wersję programu .NET Core, która aplikacja została skompilowana do uruchamiania na.</span><span class="sxs-lookup"><span data-stu-id="01e7c-132">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="01e7c-133">Aby uzyskać więcej informacji, zobacz [plików konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="01e7c-133">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Wyświetlana plików publikowanych w oknie konsoli](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="01e7c-135">Proces publikowania tworzy wdrożenia zależny od struktury jest typu wdrożenia, gdzie opublikowana aplikacja jest uruchamiana na dowolnej platformie, obsługiwana przez platformy .NET Core za pomocą programu .NET Core, zainstalowane w systemie.</span><span class="sxs-lookup"><span data-stu-id="01e7c-135">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="01e7c-136">Użytkownicy mogą uruchamiać aplikację, wysyłając `dotnet HelloWorld.dll` polecenia z okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="01e7c-136">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="01e7c-137">Aby uzyskać więcej informacji na temat publikowania i wdrażania aplikacji .NET Core, zobacz [wdrożenie aplikacji programu .NET Core](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="01e7c-137">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
