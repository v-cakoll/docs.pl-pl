---
title: Przewodnik platformy .NET Core
description: .NET Core to modularna, wielowydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o programie .NET Core, aby rozpocząć pracę.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 80a3b12972e24c3022ac2aa14406aa60635815a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341367"
---
# <a name="net-core-guide"></a><span data-ttu-id="8aab2-104">Przewodnik platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="8aab2-104">.NET Core Guide</span></span>

<span data-ttu-id="8aab2-105">[.NET Core](about.md) to platforma programistyczna ["Open Source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)", która jest obsługiwana przez firmę Microsoft i społeczność programu .NET w serwisie [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="8aab2-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="8aab2-106">Jest to międzyplatformowe (pomocnicze systemy Windows, macOS i Linux) i mogą być używane do tworzenia aplikacji dla urządzeń, usług w chmurze i IoT.</span><span class="sxs-lookup"><span data-stu-id="8aab2-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="8aab2-107">Zobacz [Informacje o programie .NET Core](about.md) , aby dowiedzieć się więcej na temat platformy .NET Core, w tym jej cech, obsługiwanych języków i struktur oraz kluczowych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="8aab2-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="8aab2-108">Zapoznaj się z [samouczkami dotyczącymi platformy .NET Core](tutorials/index.md) , aby dowiedzieć się, jak utworzyć prostą aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8aab2-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="8aab2-109">Rozpoczęcie pracy z pierwszą aplikacją może zająć zaledwie kilka minut.</span><span class="sxs-lookup"><span data-stu-id="8aab2-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="8aab2-110">Jeśli chcesz wypróbować platformę .NET Core w przeglądarce, poszukaj [cyfr w C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) samouczku online.</span><span class="sxs-lookup"><span data-stu-id="8aab2-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="8aab2-111">Pobierz program .NET Core</span><span class="sxs-lookup"><span data-stu-id="8aab2-111">Download .NET Core</span></span>

<span data-ttu-id="8aab2-112">Pobierz [zestaw .NET Core SDK](https://www.microsoft.com/net/download) , aby wypróbować platformę .NET Core na komputerze z systemem Windows, MacOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="8aab2-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="8aab2-113">Jeśli wolisz używać kontenerów platformy Docker, odwiedź stronę programu [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="8aab2-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="8aab2-114">Wszystkie wersje programu .NET Core są dostępne w [programie .NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core) , jeśli szukasz innej wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8aab2-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="8aab2-115">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="8aab2-115">.NET Core 3.1</span></span>

<span data-ttu-id="8aab2-116">Najnowsza wersja to .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="8aab2-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="8aab2-117">3,1 zawiera drobne ulepszenia w porównaniu z platformą .NET Core 3,0, jednak .NET Core 3,1 jest [długoterminową obsługiwaną wersją](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="8aab2-117">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="8aab2-118">Aby uzyskać więcej informacji o wersji programu .NET Core 3,1, zobacz [co nowego w programie .net core 3,1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="8aab2-118">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="8aab2-119">Utwórz swoją pierwszą aplikację</span><span class="sxs-lookup"><span data-stu-id="8aab2-119">Create your first application</span></span>

<span data-ttu-id="8aab2-120">Po zainstalowaniu zestaw .NET Core SDK Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="8aab2-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="8aab2-121">Wprowadź następujące polecenia `dotnet`, aby utworzyć i uruchomić C# aplikację:</span><span class="sxs-lookup"><span data-stu-id="8aab2-121">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="8aab2-122">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8aab2-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="8aab2-123">Obsługa</span><span class="sxs-lookup"><span data-stu-id="8aab2-123">Support</span></span>

<span data-ttu-id="8aab2-124">Platforma .NET Core jest [obsługiwana przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy), w systemach Windows, MacOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="8aab2-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="8aab2-125">Jest ona aktualizowana pod kątem bezpieczeństwa i jakości kilka razy w roku, zazwyczaj co miesiąc.</span><span class="sxs-lookup"><span data-stu-id="8aab2-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="8aab2-126">Dystrybucje binarne programu .NET Core są kompilowane i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i są obsługiwane w taki sam sposób jak każdy produkt firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8aab2-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="8aab2-127">[Red Hat obsługuje platformę .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="8aab2-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="8aab2-128">Red Hat kompiluje platformę .NET Core ze źródła i udostępnia je w [kolekcjach oprogramowania Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="8aab2-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="8aab2-129">Red Hat i Microsoft Współpracuj, aby upewnić się, że .NET Core działa dobrze na RHEL.</span><span class="sxs-lookup"><span data-stu-id="8aab2-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
