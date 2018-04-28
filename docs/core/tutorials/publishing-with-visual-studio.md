---
title: Publikowanie aplikacji Hello World z programu Visual Studio 2017 r.
description: Publikowanie tworzy zestaw plików, które są wymagane do uruchamiania aplikacji.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.workload:
- dotnetcore
ms.openlocfilehash: f3cecbd39ee557a620cd779bdff6b630642e7f56
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="6a5b2-103">Publikowanie aplikacji Hello World z programu Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-103">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="6a5b2-104">W [tworzenia aplikacji C# Hello World z platformą .NET Core w Visual Studio 2017](with-visual-studio.md) lub [tworzenia aplikacji Visual Basic Hello World z platformą .NET Core w Visual Studio 2017](vb-with-visual-studio.md), wbudowane Hello World aplikacji konsoli .</span><span class="sxs-lookup"><span data-stu-id="6a5b2-104">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="6a5b2-105">W [debugowania aplikacji C# Hello World z programu Visual Studio 2017](debugging-with-visual-studio.md), przetestować go za pomocą debugera programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-105">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="6a5b2-106">Teraz, gdy masz pewność, że działa zgodnie z oczekiwaniami, można opublikować, aby uruchomić go innym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="6a5b2-107">Publikowanie tworzy zestaw plików, które są wymagane do uruchamiania aplikacji i plików można wdrożyć, kopiując je na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-107">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="6a5b2-108">Aby opublikować i uruchom aplikację:</span><span class="sxs-lookup"><span data-stu-id="6a5b2-108">To publish and run your application:</span></span> 

1. <span data-ttu-id="6a5b2-109">Upewnij się, że program Visual Studio tworzy wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-109">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="6a5b2-110">W razie potrzeby zmień ustawienia konfiguracji kompilacji na pasku narzędzi z **debugowania** do **wersji**.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-110">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Visual Studio paska narzędzi](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="6a5b2-112">Kliknij prawym przyciskiem myszy **HelloWorld** projektu (nie rozwiązanie HelloWorld) i wybierz **publikowania** z menu.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-112">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="6a5b2-113">Możesz też wybrać **publikowania HelloWorld** z głównym programu Visual Studio **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-113">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Visual Studio paska narzędzi](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio paska narzędzi](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="6a5b2-116">Otwórz okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-116">Open a console window.</span></span> <span data-ttu-id="6a5b2-117">Na przykład w **wpisz tutaj, aby wyszukać** tekst pola na pasku zadań systemu Windows, wprowadź `Command Prompt` (lub `cmd` skrócie) i Otwórz okno konsoli wybierając **wiersza polecenia** pulpitu Aplikacja lub naciskając klawisz Enter, jeśli jest zaznaczona w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-117">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="6a5b2-118">Przejdź do opublikowanych aplikacji w `bin\release\PublishOutput` podkatalogu w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-118">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="6a5b2-119">Jak pokazano na poniższej ilustracji, opublikowanych danych wyjściowych zawiera cztery następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="6a5b2-119">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="6a5b2-120">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="6a5b2-120">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="6a5b2-121">Plik zależności środowiska uruchomieniowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-121">The application's runtime dependencies file.</span></span> <span data-ttu-id="6a5b2-122">Definiuje składników platformy .NET Core i bibliotek (w tym biblioteki dołączanej dynamicznie, która zawiera aplikację) wymagane do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-122">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="6a5b2-123">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="6a5b2-123">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="6a5b2-124">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="6a5b2-124">*HelloWorld.dll*</span></span>

         <span data-ttu-id="6a5b2-125">Plik, który zawiera aplikację.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-125">The file that contains your application.</span></span> <span data-ttu-id="6a5b2-126">Jest biblioteką dołączaną dynamicznie, który może zostać wykonany, wprowadzając `dotnet HelloWorld.dll` polecenie w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-126">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="6a5b2-127">*HelloWorld.pdb* (opcjonalny w przypadku wdrażania)</span><span class="sxs-lookup"><span data-stu-id="6a5b2-127">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="6a5b2-128">Plik, który zawiera symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-128">A file that contains debug symbols.</span></span> <span data-ttu-id="6a5b2-129">Nie są wymagane do wdrożenia tego pliku wraz z aplikacji, ale należy zapisać go w przypadku, gdy trzeba debugowania opublikowanej wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-129">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="6a5b2-130">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="6a5b2-130">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="6a5b2-131">Plik konfiguracji środowiska uruchomieniowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-131">The application's runtime configuration file.</span></span> <span data-ttu-id="6a5b2-132">Identyfikuje wersję platformy .NET Core, utworzony aplikacji do uruchamiania na.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-132">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="6a5b2-133">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="6a5b2-133">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Wyświetlanie plików publikowanych okna konsoli](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="6a5b2-135">Proces publikowania tworzy wdrożenia zależne od framework jest typ wdrożenia, którym opublikowana aplikacja będzie działać w żadnej platformy obsługiwanej przez oprogramowanie .NET Core z platformą .NET Core zainstalowane w systemie.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-135">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="6a5b2-136">Użytkownicy mogą korzystać z aplikacji, wysyłając `dotnet HelloWorld.dll` polecenie z poziomu okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="6a5b2-136">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="6a5b2-137">Aby uzyskać więcej informacji dotyczących publikowania i wdrażania aplikacji .NET Core, zobacz [wdrażanie aplikacji .NET Core](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="6a5b2-137">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
