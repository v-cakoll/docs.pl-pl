---
title: Przewodnik platformy .NET Core
description: Platforma .NET core to moduły, wysokowydajnych implementacji .NET do tworzenia aplikacji Windows, Linux i Mac. Dowiedz się więcej na temat platformy .NET Core, aby rozpocząć pracę.
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: cfa7c27871204b808c9d753a970d5abb907a183e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512844"
---
# <a name="net-core-guide"></a><span data-ttu-id="78021-104">Przewodnik platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="78021-104">.NET Core Guide</span></span>

<span data-ttu-id="78021-105">[.NET core](about.md) jest [typu open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) platforma deweloperska ogólnego przeznaczenia, obsługiwane przez firmę Microsoft i społeczności platformy .NET w [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="78021-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="78021-106">Jest dla wielu platform, obsługi Windows, macOS i Linux i mogą być używane w urządzeń, chmury i aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="78021-106">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and IoT applications.</span></span>

<span data-ttu-id="78021-107">Zobacz [platformy .NET Core](about.md) Aby dowiedzieć się więcej na temat platformy .NET Core, w tym właściwości, języków i struktur i klucza API.</span><span class="sxs-lookup"><span data-stu-id="78021-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="78021-108">Zapoznaj się z [Samouczki programu .NET Core](tutorials/index.md) dowiesz się, jak utworzyć prostą aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="78021-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="78021-109">Trwa tylko kilka minut, aby uzyskać swoją pierwszą aplikację, działanie.</span><span class="sxs-lookup"><span data-stu-id="78021-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="78021-110">Jeśli chcesz wypróbować platformy .NET Core w przeglądarce zostanie, Przyjrzyj się [liczb w języku C#](https://docs.microsoft.com/dotnet/csharp/quick-starts/hello-world) Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="78021-110">If you want to try .NET Core in you browser, look at the [Numbers in C#](https://docs.microsoft.com/dotnet/csharp/quick-starts/hello-world) quickstart.</span></span>

## <a name="download-net-core-21"></a><span data-ttu-id="78021-111">Pobierz program .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="78021-111">Download .NET Core 2.1</span></span>

<span data-ttu-id="78021-112">Pobierz [zestawu SDK programu .NET Core 2.1](https://www.microsoft.com/net/download) próby platformy .NET Core na komputerze Windows, macOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="78021-112">Download the [.NET Core  2.1 SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="78021-113">Odwiedź stronę [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) Jeśli wolisz używać kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="78021-113">Visit [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="78021-114">Wszystkie wersje platformy .NET Core są dostępne pod adresem [pobierania programu .NET Core](https://www.microsoft.com/net/download/archives) interesuje Cię bliższa dla innej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="78021-114">All .NET Core versions are available at [.NET Core Downloads](https://www.microsoft.com/net/download/archives) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="78021-115">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="78021-115">.NET Core 2.1</span></span>

<span data-ttu-id="78021-116">Najnowsza wersja to [platformy .NET Core 2.1](whats-new/dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="78021-116">The latest version is [.NET Core 2.1](whats-new/dotnet-core-2-1.md).</span></span> <span data-ttu-id="78021-117">Nowe funkcje obejmują: globalny narzędzi, interfejsów API o wysokiej wydajności (takie jak <xref:System.Span%601?displayProperty=nameWithType>), warstwy kompilacja JIT [kompilacji](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) i [ulepszenia wydajności w czasie wykonywania](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/)oraz obsługę Alpine i ARM32.</span><span class="sxs-lookup"><span data-stu-id="78021-117">New features include: global tools, high-performance APIs (such as <xref:System.Span%601?displayProperty=nameWithType>), tiered JIT compilation, [build](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) and [runtime performance improvements](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/), and support for Alpine and ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="78021-118">Tworzenie pierwszej aplikacji</span><span class="sxs-lookup"><span data-stu-id="78021-118">Create your first application</span></span>

<span data-ttu-id="78021-119">Po zainstalowaniu programu .NET Core SDK, otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="78021-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="78021-120">Wpisz następujące polecenie `dotnet` polecenia, aby utworzyć i uruchomić aplikację w języku C#.</span><span class="sxs-lookup"><span data-stu-id="78021-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="78021-121">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="78021-121">You should see the following output:</span></span>

```console
Hello World!
```

## <a name="support"></a><span data-ttu-id="78021-122">Obsługa</span><span class="sxs-lookup"><span data-stu-id="78021-122">Support</span></span>

<span data-ttu-id="78021-123">Platforma .NET core to [obsługiwane przez firmę Microsoft](https://www.microsoft.com/net/support/policy)na Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="78021-123">.NET Core is [supported by Microsoft](https://www.microsoft.com/net/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="78021-124">Bezpieczeństwo i jakości jest aktualizowany kilka razy w roku, zazwyczaj co miesiąc.</span><span class="sxs-lookup"><span data-stu-id="78021-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="78021-125">Dystrybucje binarny platformy .NET core tworzone i testowane na serwerach utrzymywane przez Microsoft na platformie Azure i obsługiwane podobnie jak każdego produktu firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="78021-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="78021-126">[Red Hat obsługuje platformy .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="78021-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="78021-127">Red Hat kompilacji platformy .NET Core ze źródła i udostępnia je w [Red Hat oprogramowania kolekcje](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="78021-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="78021-128">Red Hat i Microsoft współpracują, aby upewnić się, że platformy .NET Core działa dobrze w systemie RHEL.</span><span class="sxs-lookup"><span data-stu-id="78021-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>