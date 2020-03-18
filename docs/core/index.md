---
title: Przewodnik platformy .NET Core
description: .NET Core to modułowa implementacja platformy .NET o wysokiej wydajności do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o .NET Core, aby rozpocząć.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 3db98d21a7cdc80d8a98b23782a81ffa37520937
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75740744"
---
# <a name="net-core-guide"></a><span data-ttu-id="efd86-104">Przewodnik platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="efd86-104">.NET Core guide</span></span>

<span data-ttu-id="efd86-105">[.NET Core](about.md) to platforma deweloperska [typu open source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)general-purpose prowadzona przez firmę Microsoft i społeczność .NET w [usłudze GitHub.](https://github.com/dotnet/core)</span><span class="sxs-lookup"><span data-stu-id="efd86-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="efd86-106">Jest wieloplatformowy (obsługujący systemy Windows, macOS i Linux) i może być używany do tworzenia aplikacji urządzeń, chmury i IoT.</span><span class="sxs-lookup"><span data-stu-id="efd86-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="efd86-107">Zobacz [temat .NET Core,](about.md) aby dowiedzieć się więcej o .NET Core, w tym jego właściwości, obsługiwane języki i struktury oraz kluczowe interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="efd86-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="efd86-108">Zapoznaj się z [samouczkami .NET Core,](tutorials/index.md) aby dowiedzieć się, jak utworzyć prostą aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="efd86-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="efd86-109">Uruchomienie pierwszej aplikacji zajmuje tylko kilka minut.</span><span class="sxs-lookup"><span data-stu-id="efd86-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="efd86-110">Jeśli chcesz wypróbować program .NET Core w przeglądarce, zapoznaj się z samouczkiem [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online.</span><span class="sxs-lookup"><span data-stu-id="efd86-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="efd86-111">Pobierz program .NET Core</span><span class="sxs-lookup"><span data-stu-id="efd86-111">Download .NET Core</span></span>

<span data-ttu-id="efd86-112">Pobierz zestaw [.NET Core SDK,](https://www.microsoft.com/net/download) aby wypróbować program .NET Core na komputerze z systemem Windows, macOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="efd86-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="efd86-113">A jeśli wolisz używać kontenerów platformy Docker, odwiedź [centrum docker .NET Core .](https://hub.docker.com/_/microsoft-dotnet-core/)</span><span class="sxs-lookup"><span data-stu-id="efd86-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="efd86-114">Wszystkie wersje .NET Core są dostępne w [plikach do pobrania .NET Core,](https://dotnet.microsoft.com/download/dotnet-core) jeśli szukasz innej wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="efd86-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="efd86-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="efd86-115">.NET Core 3.1</span></span>

<span data-ttu-id="efd86-116">Najnowsza wersja to .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="efd86-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="efd86-117">3.1 zawiera drobne ulepszenia w stosunku do .NET Core 3.0, jednak .NET Core 3.1 jest [długoterminową obsługiwaną wersją.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="efd86-117">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="efd86-118">Aby uzyskać więcej informacji na temat wersji .NET Core 3.1, zobacz [Co nowego w .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="efd86-118">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="efd86-119">Tworzenie pierwszej aplikacji</span><span class="sxs-lookup"><span data-stu-id="efd86-119">Create your first application</span></span>

<span data-ttu-id="efd86-120">Po zainstalowaniu sdk .NET Core otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="efd86-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="efd86-121">Wprowadź następujące `dotnet` polecenia, aby utworzyć i uruchomić aplikację C#:</span><span class="sxs-lookup"><span data-stu-id="efd86-121">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="efd86-122">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="efd86-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="efd86-123">Pomoc techniczna</span><span class="sxs-lookup"><span data-stu-id="efd86-123">Support</span></span>

<span data-ttu-id="efd86-124">.NET Core jest [obsługiwany przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy), w systemach Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="efd86-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="efd86-125">Jest aktualizowany pod kątem bezpieczeństwa i jakości kilka razy w roku, zazwyczaj co miesiąc.</span><span class="sxs-lookup"><span data-stu-id="efd86-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="efd86-126">Dystrybucje binarne .NET Core są tworzone i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i obsługiwane tak jak każdy produkt firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="efd86-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="efd86-127">[Red Hat obsługuje program .NET Core](http://redhatloves.net/) w systemie Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="efd86-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="efd86-128">Red Hat buduje .NET Core ze źródła i udostępnia go w [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="efd86-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="efd86-129">Red Hat i Microsoft współpracują, aby upewnić się, że program .NET Core działa dobrze w systemie RHEL.</span><span class="sxs-lookup"><span data-stu-id="efd86-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
