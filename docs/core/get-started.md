---
title: Rozpoczynanie pracy z platformą .NET Core
description: Znajdź zasoby, aby dowiedzieć się, jak do kompilowania aplikacji platformy .NET Core w systemie Windows, Linux i macOS.
author: thraka
ms.author: adegeo
ms.date: 06/27/2018
ms.openlocfilehash: 2ec7f57250db8779552305b2ee69cbcf1db55d0c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977180"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="61308-103">Rozpoczynanie pracy z platformą .NET Core</span><span class="sxs-lookup"><span data-stu-id="61308-103">Get started with .NET Core</span></span>

<span data-ttu-id="61308-104">Ten artykuł zawiera informacje na temat rozpoczynania pracy z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="61308-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="61308-105">.NET core można zainstalować na Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="61308-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="61308-106">Można programować w swoim ulubionym edytorze tekstów i tworzenia bibliotek dla wielu platform i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="61308-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="61308-107">Jeśli wiesz nowości platformy .NET Core lub jak on odnosi się do innych technologii .NET, skorzystaj z [co to jest .NET](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet) Przegląd.</span><span class="sxs-lookup"><span data-stu-id="61308-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="61308-108">Najprościej mówiąc, .NET Core jest implementacją open source, dla wielu platform .NET.</span><span class="sxs-lookup"><span data-stu-id="61308-108">Put simply, .NET Core is an open-source, cross-platform, implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="61308-109">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="61308-109">Create an application</span></span>

<span data-ttu-id="61308-110">Najpierw należy pobrać i zainstalować [zestawu .NET Core SDK](https://www.microsoft.com/net/download/) na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="61308-110">First, download and install the [.NET Core SDK](https://www.microsoft.com/net/download/) on your computer.</span></span>

<span data-ttu-id="61308-111">Następnie otwórz terminal, takich jak **PowerShell**, **polecenia**, lub **bash**.</span><span class="sxs-lookup"><span data-stu-id="61308-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="61308-112">Wpisz następujące polecenie `dotnet` polecenia, aby utworzyć i uruchomić aplikację w języku C#.</span><span class="sxs-lookup"><span data-stu-id="61308-112">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="61308-113">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="61308-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="61308-114">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="61308-114">Congratulations!</span></span> <span data-ttu-id="61308-115">Utworzono prostą aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="61308-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="61308-116">Można również użyć [programu Visual Studio Code](tutorials/with-visual-studio-code.md), [programu Visual Studio 2017](tutorials/with-visual-studio.md) (tylko Windows), lub [programu Visual Studio dla komputerów Mac](tutorials/using-on-mac-vs.md) (macOS tylko), aby utworzyć aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="61308-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio 2017](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="61308-117">Samouczki</span><span class="sxs-lookup"><span data-stu-id="61308-117">Tutorials</span></span>

<span data-ttu-id="61308-118">Możesz rozpocząć tworzenie aplikacji .NET Core, wykonując te samouczki krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="61308-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="61308-119">Windows</span><span class="sxs-lookup"><span data-stu-id="61308-119">Windows</span></span>](#tab/windows)

* [<span data-ttu-id="61308-120">Utwórz aplikację "Hello World" C# za pomocą programu .NET Core w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="61308-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)

* [<span data-ttu-id="61308-121">Tworzenie biblioteki klas C#, w języku .NET Core w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="61308-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)

* [<span data-ttu-id="61308-122">Tworzenie aplikacji Visual Basic "Hello World" przy użyciu platformy .NET Core w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="61308-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)

* [<span data-ttu-id="61308-123">Tworzenie biblioteki klas w języku Visual Basic i .NET Core w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="61308-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  

* <span data-ttu-id="61308-124">Obejrzyj film wideo na [jak zainstalować i używać programu Visual Studio Code i platformy .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span><span class="sxs-lookup"><span data-stu-id="61308-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>

* <span data-ttu-id="61308-125">Obejrzyj film wideo na [jak zainstalować i korzystać z programu Visual Studio 2017 i .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span><span class="sxs-lookup"><span data-stu-id="61308-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>

* [<span data-ttu-id="61308-126">Wprowadzenie do platformy .NET Core przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61308-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

<span data-ttu-id="61308-127">Zobacz [rozwoju wymagania wstępne dla Windows](windows-prerequisites.md) artykule Aby uzyskać listę obsługiwanych wersji Windows.</span><span class="sxs-lookup"><span data-stu-id="61308-127">See the [Prerequisites for Windows development](windows-prerequisites.md) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="61308-128">Linux</span><span class="sxs-lookup"><span data-stu-id="61308-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="61308-129">Możesz rozpocząć tworzenie aplikacji .NET Core, wykonując te samouczki krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="61308-129">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* [<span data-ttu-id="61308-130">Wprowadzenie do platformy .NET Core przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61308-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* <span data-ttu-id="61308-131">Obejrzyj film wideo na [rozpoczęcie korzystania z programu Visual Studio Code przy użyciu języka C# i .NET Core w systemie Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="61308-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="61308-132">Zobacz [wymagania wstępne dotyczące programowania systemu Linux](linux-prerequisites.md) artykułu, aby uzyskać listę obsługiwane dystrybucje systemu Linux i wersji.</span><span class="sxs-lookup"><span data-stu-id="61308-132">See the [Prerequisites for Linux development](linux-prerequisites.md) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="61308-133">macOS</span><span class="sxs-lookup"><span data-stu-id="61308-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="61308-134">Możesz rozpocząć tworzenie aplikacji .NET Core, wykonując te samouczki krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="61308-134">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* <span data-ttu-id="61308-135">Obejrzyj film wideo na [rozpoczęcie korzystania z programu Visual Studio Code przy użyciu języka C# i .NET Core w systemie macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="61308-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>

* [<span data-ttu-id="61308-136">Wprowadzenie do platformy .NET Core w systemie macOS przy użyciu programu Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="61308-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)

* [<span data-ttu-id="61308-137">Wprowadzenie do platformy .NET Core przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61308-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* [<span data-ttu-id="61308-138">Wprowadzenie do platformy .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="61308-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)

* [<span data-ttu-id="61308-139">Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="61308-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="61308-140">Zobacz [wymagania wstępne dotyczące programowania dla systemu macOS](macos-prerequisites.md) artykułu listę obsługiwanych systemów operacyjnych X / wersji systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="61308-140">See the [Prerequisites for macOS development](macos-prerequisites.md) article for a list of the supported OS X / macOS versions.</span></span>

---
