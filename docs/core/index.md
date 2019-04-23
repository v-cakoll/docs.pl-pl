---
title: Przewodnik platformy .NET Core
description: Platforma .NET core to moduły, wysokowydajnych implementacji .NET do tworzenia aplikacji Windows, Linux i Mac. Dowiedz się więcej na temat platformy .NET Core, aby rozpocząć pracę.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 79a0c09074159160dd01b0c7970612f7058cc3fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974360"
---
# <a name="net-core-guide"></a><span data-ttu-id="ab9d2-104">Przewodnik platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab9d2-104">.NET Core Guide</span></span>

<span data-ttu-id="ab9d2-105">[.NET core](about.md) jest [typu open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), platforma deweloperska ogólnego przeznaczenia, obsługiwane przez firmę Microsoft i społeczności platformy .NET w [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="ab9d2-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="ab9d2-106">Jest wiele platform (Obsługa Windows, macOS i Linux) i może służyć do tworzenia urządzeń, chmury i aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="ab9d2-107">Zobacz [platformy .NET Core](about.md) Aby dowiedzieć się więcej na temat platformy .NET Core, w tym właściwości, języków i struktur i klucza API.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="ab9d2-108">Zapoznaj się z [Samouczki programu .NET Core](tutorials/index.md) dowiesz się, jak utworzyć prostą aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="ab9d2-109">Trwa tylko kilka minut, aby uzyskać swoją pierwszą aplikację, działanie.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="ab9d2-110">Jeśli chcesz wypróbować platformy .NET Core w przeglądarce, Przyjrzyj się [liczby w elemencie C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) samouczek online.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core-22"></a><span data-ttu-id="ab9d2-111">Pobierz program .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ab9d2-111">Download .NET Core 2.2</span></span>

<span data-ttu-id="ab9d2-112">Pobierz [zestawu .NET Core 2.2 SDK](https://www.microsoft.com/net/download) próby platformy .NET Core na komputerze Windows, macOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-112">Download the [.NET Core  2.2 SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="ab9d2-113">Odwiedź stronę [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) Jeśli wolisz używać kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-113">Visit [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="ab9d2-114">Wszystkie wersje platformy .NET Core są dostępne pod adresem [pobierania programu .NET Core](https://www.microsoft.com/net/download/archives) interesuje Cię bliższa dla innej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-114">All .NET Core versions are available at [.NET Core Downloads](https://www.microsoft.com/net/download/archives) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-22"></a><span data-ttu-id="ab9d2-115">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ab9d2-115">.NET Core 2.2</span></span>

<span data-ttu-id="ab9d2-116">Najnowsza wersja to [platformy .NET Core 2.2](whats-new/dotnet-core-2-2.md).</span><span class="sxs-lookup"><span data-stu-id="ab9d2-116">The latest version is [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span></span> <span data-ttu-id="ab9d2-117">Nowe funkcje obejmują: wdrożeń zależny od struktury, punkty zaczepienia uruchamiania, uwierzytelnianie w usłudze AAD przy użyciu usługi Azure SQL i pomoc techniczna dla Windows ARM32.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-117">New features include: framework-dependent deployments, startup hooks, AAD authentication with Azure SQL, and support for Windows ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="ab9d2-118">Tworzenie pierwszej aplikacji</span><span class="sxs-lookup"><span data-stu-id="ab9d2-118">Create your first application</span></span>

<span data-ttu-id="ab9d2-119">Po zainstalowaniu programu .NET Core SDK, otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="ab9d2-120">Wpisz następujące polecenie `dotnet` polecenia, aby utworzyć i uruchomić aplikację w języku C#.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="ab9d2-121">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ab9d2-121">You should see the following output:</span></span>

```console
Hello World!
```

## <a name="support"></a><span data-ttu-id="ab9d2-122">Pomoc techniczna</span><span class="sxs-lookup"><span data-stu-id="ab9d2-122">Support</span></span>

<span data-ttu-id="ab9d2-123">Platforma .NET core to [obsługiwane przez firmę Microsoft](https://www.microsoft.com/net/support/policy)na Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-123">.NET Core is [supported by Microsoft](https://www.microsoft.com/net/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="ab9d2-124">Bezpieczeństwo i jakości jest aktualizowany kilka razy w roku, zazwyczaj co miesiąc.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="ab9d2-125">Dystrybucje binarny platformy .NET core tworzone i testowane na serwerach utrzymywane przez Microsoft na platformie Azure i obsługiwane podobnie jak każdego produktu firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="ab9d2-126">[Red Hat obsługuje platformy .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="ab9d2-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="ab9d2-127">Red Hat kompilacji platformy .NET Core ze źródła i udostępnia je w [Red Hat oprogramowania kolekcje](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="ab9d2-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="ab9d2-128">Red Hat i Microsoft współpracują, aby upewnić się, że platformy .NET Core działa dobrze w systemie RHEL.</span><span class="sxs-lookup"><span data-stu-id="ab9d2-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
