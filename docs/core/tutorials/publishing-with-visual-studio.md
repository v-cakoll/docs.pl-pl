---
title: Publikowanie aplikacji Hello World z programu Visual Studio 2017 r.
description: "Publikowanie tworzy zestaw plików, które są wymagane do uruchamiania aplikacji."
keywords: "Aplikacji konsoli .NET i .NET core publikacji wdrożenia"
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.openlocfilehash: a3e5bda5c99144c9ab5bbaf5e2f5566261af4813
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="46f99-104">Publikowanie aplikacji Hello World z programu Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="46f99-104">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="46f99-105">W [tworzenia aplikacji C# Hello World z platformą .NET Core w Visual Studio 2017](with-visual-studio.md) lub [tworzenia aplikacji Visual Basic Hello World z platformą .NET Core w Visual Studio 2017](vb-with-visual-studio.md), wbudowane Hello World aplikacji konsoli .</span><span class="sxs-lookup"><span data-stu-id="46f99-105">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="46f99-106">W [debugowania aplikacji C# Hello World z programu Visual Studio 2017](debugging-with-visual-studio.md), przetestować go za pomocą debugera programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46f99-106">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="46f99-107">Teraz, gdy masz pewność, że działa zgodnie z oczekiwaniami, można opublikować, aby uruchomić go innym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="46f99-107">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="46f99-108">Publikowanie tworzy zestaw plików, które są wymagane do uruchamiania aplikacji i plików można wdrożyć, kopiując je na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="46f99-108">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="46f99-109">Aby opublikować i uruchom aplikację:</span><span class="sxs-lookup"><span data-stu-id="46f99-109">To publish and run your application:</span></span> 

1. <span data-ttu-id="46f99-110">Upewnij się, że program Visual Studio tworzy wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46f99-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="46f99-111">W razie potrzeby zmień ustawienia konfiguracji kompilacji na pasku narzędzi z **debugowania** do **wersji**.</span><span class="sxs-lookup"><span data-stu-id="46f99-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Visual Studio paska narzędzi](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="46f99-113">Kliknij prawym przyciskiem myszy **HelloWorld** projektu (nie rozwiązanie HelloWorld) i wybierz **publikowania** z menu.</span><span class="sxs-lookup"><span data-stu-id="46f99-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="46f99-114">Możesz też wybrać **publikowania HelloWorld** z głównym programu Visual Studio **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="46f99-114">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Visual Studio paska narzędzi](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio paska narzędzi](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="46f99-117">Otwórz okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="46f99-117">Open a console window.</span></span> <span data-ttu-id="46f99-118">Na przykład w **wpisz tutaj, aby wyszukać** tekst pola na pasku zadań systemu Windows, wprowadź `Command Prompt` (lub `cmd` skrócie) i Otwórz okno konsoli wybierając **wiersza polecenia** pulpitu Aplikacja lub naciskając klawisz Enter, jeśli jest zaznaczona w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="46f99-118">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="46f99-119">Przejdź do opublikowanych aplikacji w `bin\release\PublishOutput` podkatalogu w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="46f99-119">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="46f99-120">Jak pokazano na poniższej ilustracji, opublikowanych danych wyjściowych zawiera cztery następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="46f99-120">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="46f99-121">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="46f99-121">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="46f99-122">Plik zależności środowiska uruchomieniowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46f99-122">The application's runtime dependencies file.</span></span> <span data-ttu-id="46f99-123">Definiuje składników platformy .NET Core i bibliotek (w tym biblioteki dołączanej dynamicznie, która zawiera aplikację) wymagane do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46f99-123">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="46f99-124">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="46f99-124">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="46f99-125">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="46f99-125">*HelloWorld.dll*</span></span>

         <span data-ttu-id="46f99-126">Plik, który zawiera aplikację.</span><span class="sxs-lookup"><span data-stu-id="46f99-126">The file that contains your application.</span></span> <span data-ttu-id="46f99-127">Jest biblioteką dołączaną dynamicznie, który może zostać wykonany, wprowadzając `dotnet HelloWorld.dll` polecenie w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="46f99-127">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="46f99-128">*HelloWorld.pdb* (opcjonalny w przypadku wdrażania)</span><span class="sxs-lookup"><span data-stu-id="46f99-128">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="46f99-129">Plik, który zawiera symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="46f99-129">A file that contains debug symbols.</span></span> <span data-ttu-id="46f99-130">Nie są wymagane do wdrożenia tego pliku wraz z aplikacji, ale należy zapisać go w przypadku, gdy trzeba debugowania opublikowanej wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46f99-130">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="46f99-131">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="46f99-131">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="46f99-132">Plik konfiguracji środowiska uruchomieniowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46f99-132">The application's runtime configuration file.</span></span> <span data-ttu-id="46f99-133">Identyfikuje wersję platformy .NET Core, utworzony aplikacji do uruchamiania na.</span><span class="sxs-lookup"><span data-stu-id="46f99-133">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="46f99-134">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="46f99-134">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Wyświetlanie plików publikowanych okna konsoli](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="46f99-136">Proces publikowania tworzy wdrożenia zależne od framework jest typ wdrożenia, którym opublikowana aplikacja będzie działać w żadnej platformy obsługiwanej przez oprogramowanie .NET Core z platformą .NET Core zainstalowane w systemie.</span><span class="sxs-lookup"><span data-stu-id="46f99-136">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="46f99-137">Użytkownicy mogą korzystać z aplikacji, wysyłając `dotnet HelloWorld.dll` polecenie z poziomu okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="46f99-137">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="46f99-138">Aby uzyskać więcej informacji dotyczących publikowania i wdrażania aplikacji .NET Core, zobacz [wdrażanie aplikacji .NET Core](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="46f99-138">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
