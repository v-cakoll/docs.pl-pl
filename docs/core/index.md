---
title: Przewodnik platformy .NET Core
description: .NET Core to modułowa, wydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o .NET Core, aby rozpocząć.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 6d2ce5951fa01ca3945ce0e64aa58fbadc8ab5af
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546552"
---
# <a name="net-core-guide"></a><span data-ttu-id="e1390-104">Przewodnik platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1390-104">.NET Core guide</span></span>

<span data-ttu-id="e1390-105">[.NET Core](about.md) jest platformą programową [typu open source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)ogólnego przeznaczenia prowadzoną przez firmę Microsoft i społeczność .NET w [witrynie GitHub.](https://github.com/dotnet/core)</span><span class="sxs-lookup"><span data-stu-id="e1390-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="e1390-106">Jest wieloplatformowy (obsługujący systemy Windows, macOS i Linux) i może być używany do tworzenia urządzeń, chmury i aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="e1390-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="e1390-107">Zobacz [Temat .NET Core,](about.md) aby dowiedzieć się więcej o .NET Core, w tym jego charakterystyki, obsługiwane języki i struktury oraz kluczowe interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="e1390-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="e1390-108">Zapoznaj się z [samouczkami .NET Core,](tutorials/index.md) aby dowiedzieć się, jak utworzyć prostą aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1390-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="e1390-109">Uruchomienie pierwszej aplikacji zajmuje tylko kilka minut.</span><span class="sxs-lookup"><span data-stu-id="e1390-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="e1390-110">Jeśli chcesz wypróbować .NET Core w przeglądarce, spójrz na [numery w języku C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) samouczka online.</span><span class="sxs-lookup"><span data-stu-id="e1390-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="e1390-111">Pobierz .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1390-111">Download .NET Core</span></span>

<span data-ttu-id="e1390-112">Pobierz [podstawowy sdk .NET,](https://dotnet.microsoft.com/download) aby wypróbować program .NET Core na komputerze z systemem Windows, macOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="e1390-112">Download the [.NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="e1390-113">A jeśli wolisz używać kontenerów platformy Docker, odwiedź [centrum docker .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="e1390-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="e1390-114">Wszystkie wersje .NET Core są dostępne w [.NET Core Downloads,](https://dotnet.microsoft.com/download/dotnet-core) jeśli szukasz innej wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1390-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="e1390-115">.NET Rdzeń 3.1</span><span class="sxs-lookup"><span data-stu-id="e1390-115">.NET Core 3.1</span></span>

<span data-ttu-id="e1390-116">Najnowsza wersja to .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="e1390-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="e1390-117">3.1 zawiera drobne ulepszenia w stosunku do .NET Core 3.0, jednak .NET Core 3.1 jest [długoterminową wersją obsługiwaną.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="e1390-117">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="e1390-118">Aby uzyskać więcej informacji na temat wersji .NET Core 3.1, zobacz [Co nowego w .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="e1390-118">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="e1390-119">Tworzenie pierwszej aplikacji</span><span class="sxs-lookup"><span data-stu-id="e1390-119">Create your first application</span></span>

<span data-ttu-id="e1390-120">Po zainstalowaniu zestawu .NET Core SDK otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1390-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="e1390-121">Wprowadź następujące `dotnet` polecenia, aby utworzyć i uruchomić aplikację języka C#:</span><span class="sxs-lookup"><span data-stu-id="e1390-121">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="e1390-122">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e1390-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="e1390-123">Pomoc techniczna</span><span class="sxs-lookup"><span data-stu-id="e1390-123">Support</span></span>

<span data-ttu-id="e1390-124">Program .NET Core jest [obsługiwany przez](https://dotnet.microsoft.com/platform/support/policy)firmę Microsoft , w systemach Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="e1390-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="e1390-125">Jest aktualizowany pod kątem bezpieczeństwa i jakości kilka razy w roku, zazwyczaj co miesiąc.</span><span class="sxs-lookup"><span data-stu-id="e1390-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="e1390-126">Dystrybucje binarne .NET Core są tworzone i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i obsługiwane tak jak każdy produkt firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e1390-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="e1390-127">[Red Hat obsługuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="e1390-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="e1390-128">Red Hat buduje .NET Core ze źródła i udostępnia go w [red hat software collections](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="e1390-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="e1390-129">Red Hat i Microsoft współpracują, aby zapewnić, że program .NET Core działa dobrze na RHEL.</span><span class="sxs-lookup"><span data-stu-id="e1390-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
