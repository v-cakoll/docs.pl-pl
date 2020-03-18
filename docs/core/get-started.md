---
title: Wprowadzenie do programu .NET Core
description: Znajdź zasoby, aby dowiedzieć się, jak tworzyć aplikacje .NET Core w systemach Windows, Linux i macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714393"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="0b25d-103">Wprowadzenie do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="0b25d-103">Get started with .NET Core</span></span>

<span data-ttu-id="0b25d-104">Ten artykuł zawiera informacje dotyczące rozpoczynania pracy z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0b25d-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="0b25d-105">Program .NET Core można zainstalować w systemach Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="0b25d-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="0b25d-106">Możesz kodować w swoim ulubionym edytorze tekstu i tworzyć biblioteki i aplikacje międzyplatformowe.</span><span class="sxs-lookup"><span data-stu-id="0b25d-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="0b25d-107">Jeśli nie masz pewności, co to jest program .NET Core lub jak odnosi się do innych technologii .NET, rozpocznij od omówienie Co to [jest .NET.](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet)</span><span class="sxs-lookup"><span data-stu-id="0b25d-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="0b25d-108">Mówiąc prościej, .NET Core jest implementacją platformy .NET typu open source na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="0b25d-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="0b25d-109">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="0b25d-109">Create an application</span></span>

<span data-ttu-id="0b25d-110">Najpierw pobierz i zainstaluj zestaw [SDK .NET Core](https://dotnet.microsoft.com/download) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0b25d-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="0b25d-111">Następnie otwórz terminal, taki jak **PowerShell,** **Wiersz polecenia**lub **bash**.</span><span class="sxs-lookup"><span data-stu-id="0b25d-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="0b25d-112">Wpisz `dotnet` następujące polecenia, aby utworzyć i uruchomić aplikację C#:</span><span class="sxs-lookup"><span data-stu-id="0b25d-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="0b25d-113">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0b25d-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="0b25d-114">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="0b25d-114">Congratulations!</span></span> <span data-ttu-id="0b25d-115">Utworzono prostą aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0b25d-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="0b25d-116">Można również użyć [kodu programu Visual Studio](./tutorials/with-visual-studio-code.md), Visual [Studio](./tutorials/with-visual-studio.md) (tylko windows) lub Visual Studio dla [komputerów Mac](./tutorials/using-on-mac-vs.md) (tylko macOS), aby utworzyć aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0b25d-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](./tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="0b25d-117">Samouczki</span><span class="sxs-lookup"><span data-stu-id="0b25d-117">Tutorials</span></span>

<span data-ttu-id="0b25d-118">Wprowadzenie do tworzenia aplikacji .NET Core, wykonując następujące samouczki krok po kroku:</span><span class="sxs-lookup"><span data-stu-id="0b25d-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="0b25d-119">Windows</span><span class="sxs-lookup"><span data-stu-id="0b25d-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="0b25d-120">Tworzenie pierwszej aplikacji konsoli .NET Core w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="0b25d-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="0b25d-121">Tworzenie biblioteki klas za pomocą programu .NET Standard w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b25d-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="0b25d-122">Wprowadzenie do programu .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="0b25d-122">Get started with .NET Core using the .NET Core CLI</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="0b25d-123">![ikona kamery filmowych dla wideo](./media/video-icon.png "Obejrzyj film")</span><span class="sxs-lookup"><span data-stu-id="0b25d-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="0b25d-124">Zobacz, [jak zainstalować i używać programu Visual Studio Code i wideo .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) w kanale 9.</span><span class="sxs-lookup"><span data-stu-id="0b25d-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="0b25d-125">![ikona kamery filmowych dla wideo](./media/video-icon.png "Obejrzyj film")</span><span class="sxs-lookup"><span data-stu-id="0b25d-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="0b25d-126">Obejrzyj filmy [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) w YouTube.</span><span class="sxs-lookup"><span data-stu-id="0b25d-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="0b25d-127">Zobacz [.NET Core zależności i wymagania](install/dependencies.md?pivots=os-windows) artykułu dla listy obsługiwanych wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0b25d-127">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="0b25d-128">Linux</span><span class="sxs-lookup"><span data-stu-id="0b25d-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="0b25d-129">Wprowadzenie do tworzenia aplikacji .NET Core, wykonując następujące samouczki krok po kroku:</span><span class="sxs-lookup"><span data-stu-id="0b25d-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="0b25d-130">Wprowadzenie do programu .NET Core przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="0b25d-130">Get started with .NET Core using the command line</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="0b25d-131">![ikona kamery filmowych dla wideo](./media/video-icon.png "Obejrzyj film")</span><span class="sxs-lookup"><span data-stu-id="0b25d-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="0b25d-132">Obejrzyj klip wideo przedstawiający [wprowadzenie do programu Visual Studio Code przy użyciu wersji C# i .NET Core w programie Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="0b25d-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="0b25d-133">Zobacz [.NET Core zależności i wymagania](install/dependencies.md?pivots=os-linux) artykułu dla listy obsługiwanych dystrybucji systemu Linux i wersji.</span><span class="sxs-lookup"><span data-stu-id="0b25d-133">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="0b25d-134">Macos</span><span class="sxs-lookup"><span data-stu-id="0b25d-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="0b25d-135">Wprowadzenie do tworzenia aplikacji .NET Core, wykonując następujące samouczki krok po kroku:</span><span class="sxs-lookup"><span data-stu-id="0b25d-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="0b25d-136">Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0b25d-136">Get started with .NET Core on macOS using Visual Studio Code</span></span>](./tutorials/using-on-macos.md)
- [<span data-ttu-id="0b25d-137">Wprowadzenie do programu .NET Core przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="0b25d-137">Get started with .NET Core using the command-line</span></span>](./tutorials/cli-create-console-app.md)
- [<span data-ttu-id="0b25d-138">Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="0b25d-138">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="0b25d-139">Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="0b25d-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| <span data-ttu-id="0b25d-140">![ikona kamery filmowych dla wideo](media/video-icon.png "Obejrzyj film")</span><span class="sxs-lookup"><span data-stu-id="0b25d-140">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="0b25d-141">Obejrzyj klip wideo przedstawiający [wprowadzenie do programu Visual Studio Code przy użyciu języka C# i programu .NET Core w systemie macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="0b25d-141">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="0b25d-142">Zobacz [.NET Core zależności i wymagania](install/dependencies.md?pivots=os-macos) artykułu dla listy obsługiwanych wersji systemu OS X / macOS.</span><span class="sxs-lookup"><span data-stu-id="0b25d-142">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
