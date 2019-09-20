---
title: Wprowadzenie do platformy .NET Core
description: Znajdź zasoby, aby dowiedzieć się, jak tworzyć aplikacje .NET Core w systemach Windows, Linux i macOS.
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 7dc134696e7dacf531fa6c7f4d84b63eb785ef25
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2019
ms.locfileid: "71151508"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="61e73-103">Wprowadzenie do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="61e73-103">Get started with .NET Core</span></span>

<span data-ttu-id="61e73-104">Ten artykuł zawiera informacje na temat rozpoczynania pracy z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="61e73-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="61e73-105">Program .NET Core można zainstalować w systemach Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="61e73-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="61e73-106">Możesz zakodować w ulubionym edytorze tekstów i tworzyć Międzyplatformowe biblioteki i aplikacje.</span><span class="sxs-lookup"><span data-stu-id="61e73-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="61e73-107">Jeśli nie masz pewności, co to jest platforma .NET Core, lub jak odnosi się do innych technologii .NET, Zacznij od omówienia [programu .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="61e73-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="61e73-108">Po prostu, .NET Core to wieloplatformowa implementacja platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="61e73-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="61e73-109">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="61e73-109">Create an application</span></span>

<span data-ttu-id="61e73-110">Najpierw pobierz i zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="61e73-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="61e73-111">Następnie otwórz Terminal, taki jak **PowerShell**, **wiersza polecenia**lub **bash**.</span><span class="sxs-lookup"><span data-stu-id="61e73-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="61e73-112">Wpisz następujące `dotnet` polecenia, aby utworzyć i uruchomić C# aplikację.</span><span class="sxs-lookup"><span data-stu-id="61e73-112">Type the following `dotnet` commands to create and run a C# application.</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="61e73-113">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="61e73-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="61e73-114">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="61e73-114">Congratulations!</span></span> <span data-ttu-id="61e73-115">Utworzono prostą aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="61e73-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="61e73-116">Można również użyć [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (tylko Windows) lub [Visual Studio dla komputerów Mac](tutorials/using-on-mac-vs.md) (tylko macOS), aby utworzyć aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="61e73-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="61e73-117">Samouczki</span><span class="sxs-lookup"><span data-stu-id="61e73-117">Tutorials</span></span>

<span data-ttu-id="61e73-118">Możesz rozpocząć tworzenie aplikacji platformy .NET Core, wykonując te Samouczki krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="61e73-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="61e73-119">Windows</span><span class="sxs-lookup"><span data-stu-id="61e73-119">Windows</span></span>](#tab/windows)

* [<span data-ttu-id="61e73-120">Kompiluj aplikację C# "Hello World" przy użyciu platformy .NET Core w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="61e73-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)

* [<span data-ttu-id="61e73-121">Kompiluj bibliotekę C# klas z platformą .NET Core w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="61e73-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)

* [<span data-ttu-id="61e73-122">Kompiluj Visual Basic "Hello world" z platformą .NET Core w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="61e73-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)

* [<span data-ttu-id="61e73-123">Kompiluj bibliotekę klas z Visual Basic i .NET Core w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="61e73-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  

* <span data-ttu-id="61e73-124">Obejrzyj film wideo na [temat sposobu instalowania i używania Visual Studio Code i platformy .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span><span class="sxs-lookup"><span data-stu-id="61e73-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>

* <span data-ttu-id="61e73-125">Obejrzyj film wideo na [temat sposobu instalowania i używania programów Visual Studio 2017 i .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span><span class="sxs-lookup"><span data-stu-id="61e73-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>

* [<span data-ttu-id="61e73-126">Wprowadzenie do programu .NET Core przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61e73-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

<span data-ttu-id="61e73-127">Listę obsługiwanych wersji systemu Windows można znaleźć w artykule [dotyczącym wymagań wstępnych dotyczących programowania systemu Windows](windows-prerequisites.md) .</span><span class="sxs-lookup"><span data-stu-id="61e73-127">See the [Prerequisites for Windows development](windows-prerequisites.md) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="61e73-128">Linux</span><span class="sxs-lookup"><span data-stu-id="61e73-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="61e73-129">Możesz rozpocząć tworzenie aplikacji .NET Core, wykonując te Samouczki krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="61e73-129">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* [<span data-ttu-id="61e73-130">Wprowadzenie do programu .NET Core przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61e73-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* <span data-ttu-id="61e73-131">Obejrzyj film wideo [z wprowadzeniem do Visual Studio Code przy C# użyciu oprogramowania i platformy .NET Core w systemie Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="61e73-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="61e73-132">Listę obsługiwanych dystrybucje i wersji systemu Linux można znaleźć w artykule dotyczącym [wymagań wstępnych dotyczących programowania w systemie Linux](linux-prerequisites.md) .</span><span class="sxs-lookup"><span data-stu-id="61e73-132">See the [Prerequisites for Linux development](linux-prerequisites.md) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="61e73-133">macOS</span><span class="sxs-lookup"><span data-stu-id="61e73-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="61e73-134">Możesz rozpocząć tworzenie aplikacji .NET Core, wykonując te Samouczki krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="61e73-134">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* <span data-ttu-id="61e73-135">Obejrzyj film wideo [z wprowadzeniem do Visual Studio Code przy C# użyciu oprogramowania i platformy .NET Core w systemie macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="61e73-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>

* [<span data-ttu-id="61e73-136">Wprowadzenie do programu .NET Core w systemie macOS przy użyciu Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="61e73-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)

* [<span data-ttu-id="61e73-137">Wprowadzenie do programu .NET Core przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61e73-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* [<span data-ttu-id="61e73-138">Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu Visual Studio dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="61e73-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)

* [<span data-ttu-id="61e73-139">Utwórz kompletne rozwiązanie platformy .NET Core w systemie macOS przy użyciu Visual Studio dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="61e73-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="61e73-140">Listę obsługiwanych wersji systemu OS X/macOS można znaleźć w artykule [dotyczącym wymagań wstępnych dotyczących programowania macOS](macos-prerequisites.md) .</span><span class="sxs-lookup"><span data-stu-id="61e73-140">See the [Prerequisites for macOS development](macos-prerequisites.md) article for a list of the supported OS X / macOS versions.</span></span>

---
