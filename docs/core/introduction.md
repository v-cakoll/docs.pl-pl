---
title: Wprowadzenie i omówienie .NET Core
description: .NET Core to modułowa, wydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o .NET Core, aby rozpocząć.
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351702"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="bb6a4-104">Wprowadzenie do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="bb6a4-104">Introduction to .NET Core</span></span>

<span data-ttu-id="bb6a4-105">[.NET Core](about.md) jest platformą programową [typu open source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)ogólnego przeznaczenia prowadzoną przez firmę Microsoft i społeczność .NET w [witrynie GitHub.](https://github.com/dotnet/core)</span><span class="sxs-lookup"><span data-stu-id="bb6a4-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="bb6a4-106">Jest wieloplatformowy (obsługujący systemy Windows, macOS i Linux) i może być używany do tworzenia urządzeń, chmury i aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="bb6a4-107">Pobierz .NET Core</span><span class="sxs-lookup"><span data-stu-id="bb6a4-107">Download .NET Core</span></span>

<span data-ttu-id="bb6a4-108">Pobierz [podstawowy sdk .NET,](https://dotnet.microsoft.com/download) aby wypróbować program .NET Core na komputerze z systemem Windows, macOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-108">Download the [.NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="bb6a4-109">Jeśli wolisz używać kontenerów platformy Docker, odwiedź [centrum platformy .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="bb6a4-109">If you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

## <a name="net-core-31"></a><span data-ttu-id="bb6a4-110">.NET Rdzeń 3.1</span><span class="sxs-lookup"><span data-stu-id="bb6a4-110">.NET Core 3.1</span></span>

<span data-ttu-id="bb6a4-111">Najnowsza wersja to .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-111">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="bb6a4-112">3.1 zawiera drobne ulepszenia w stosunku do .NET Core 3.0, jednak .NET Core 3.1 jest [długoterminową wersją obsługiwaną.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="bb6a4-112">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="bb6a4-113">Aby uzyskać więcej informacji na temat wersji .NET Core 3.1, zobacz [Co nowego w .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="bb6a4-113">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

<span data-ttu-id="bb6a4-114">Jeśli szukasz innej wersji programu .NET Core, wszystkie wersje są dostępne w [plikach do pobrania .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="bb6a4-114">If you're looking for another version of .NET Core, all the versions are available at [.NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="bb6a4-115">Tworzenie pierwszej aplikacji</span><span class="sxs-lookup"><span data-stu-id="bb6a4-115">Create your first application</span></span>

<span data-ttu-id="bb6a4-116">Po zainstalowaniu zestawu .NET Core SDK otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-116">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="bb6a4-117">Wprowadź następujące `dotnet` polecenia, aby utworzyć i uruchomić aplikację języka C#:</span><span class="sxs-lookup"><span data-stu-id="bb6a4-117">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="bb6a4-118">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="bb6a4-118">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="bb6a4-119">Pomoc techniczna</span><span class="sxs-lookup"><span data-stu-id="bb6a4-119">Support</span></span>

<span data-ttu-id="bb6a4-120">Program .NET Core jest [obsługiwany przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy) w systemach Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-120">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy) on Windows, macOS, and Linux.</span></span> <span data-ttu-id="bb6a4-121">Jest aktualizowany pod kątem bezpieczeństwa i jakości kilka razy w roku, zazwyczaj co miesiąc.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-121">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="bb6a4-122">Dystrybucje binarne .NET Core są tworzone i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i obsługiwane tak jak każdy produkt firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-122">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="bb6a4-123">[Red Hat obsługuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="bb6a4-123">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="bb6a4-124">Red Hat buduje .NET Core ze źródła i udostępnia go w [red hat software collections](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="bb6a4-124">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="bb6a4-125">Red Hat i Microsoft współpracują, aby zapewnić, że program .NET Core działa dobrze na RHEL.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-125">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bb6a4-126">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="bb6a4-126">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bb6a4-127">Samouczki .NET Core</span><span class="sxs-lookup"><span data-stu-id="bb6a4-127">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="bb6a4-128">Wypróbuj program .NET Core w przeglądarce</span><span class="sxs-lookup"><span data-stu-id="bb6a4-128">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
