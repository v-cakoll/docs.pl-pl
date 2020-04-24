---
title: Wprowadzenie i omówienie .NET Core
description: .NET Core to modułowa, wydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o .NET Core, aby rozpocząć.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: f99b446bbd38b2b814c13afa13ab34cd5c9aa086
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645525"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="87dd2-104">Wprowadzenie do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="87dd2-104">Introduction to .NET Core</span></span>

<span data-ttu-id="87dd2-105">[.NET Core](about.md) jest platformą programową [typu open source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)i ogólnego przeznaczenia.</span><span class="sxs-lookup"><span data-stu-id="87dd2-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="87dd2-106">Aplikacje .NET Core dla systemów Windows, macOS i Linux można tworzyć dla procesorów x64, x86, ARM32 i ARM64 w wielu językach programowania.</span><span class="sxs-lookup"><span data-stu-id="87dd2-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="87dd2-107">Struktury i interfejsy API są dostarczane dla [chmury,](/aspnet/core/) [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [interfejsu użytkownika klienta](../desktop-wpf/overview/index.md)i uczenia [maszynowego.](/dotnet/machine-learning/)</span><span class="sxs-lookup"><span data-stu-id="87dd2-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="87dd2-108">[Pobierz podstawowy sdk .NET,](https://dotnet.microsoft.com/download) aby wypróbować program .NET Core na swoim komputerze.</span><span class="sxs-lookup"><span data-stu-id="87dd2-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="87dd2-109">Najnowsza wersja to [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="87dd2-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="87dd2-110">Pobierz .NET Core</span><span class="sxs-lookup"><span data-stu-id="87dd2-110">Download .NET Core</span></span>

<span data-ttu-id="87dd2-111">Program .NET Core można uzyskać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="87dd2-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="87dd2-112">Instalatorzy systemów Windows i macOS</span><span class="sxs-lookup"><span data-stu-id="87dd2-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="87dd2-113">Pakiety Linuksa</span><span class="sxs-lookup"><span data-stu-id="87dd2-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="87dd2-114">Kontenerów Docker</span><span class="sxs-lookup"><span data-stu-id="87dd2-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="87dd2-115">Zamki błyskawiczne i kulki smoły</span><span class="sxs-lookup"><span data-stu-id="87dd2-115">Zips and tar balls</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="87dd2-116">Instalowanie skryptów</span><span class="sxs-lookup"><span data-stu-id="87dd2-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="87dd2-117">Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="87dd2-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="87dd2-118">Tworzenie pierwszej aplikacji</span><span class="sxs-lookup"><span data-stu-id="87dd2-118">Create your first application</span></span>

<span data-ttu-id="87dd2-119">Po zainstalowaniu zestawu .NET Core SDK otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="87dd2-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="87dd2-120">Aby utworzyć i uruchomić aplikację, użyj następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="87dd2-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="87dd2-121">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="87dd2-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="87dd2-122">Współtworzenie</span><span class="sxs-lookup"><span data-stu-id="87dd2-122">Contribute</span></span>

<span data-ttu-id="87dd2-123">.NET Core jest otwartą platformą.</span><span class="sxs-lookup"><span data-stu-id="87dd2-123">.NET Core is an open platform.</span></span> <span data-ttu-id="87dd2-124">Każdy jest mile widziany.</span><span class="sxs-lookup"><span data-stu-id="87dd2-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="87dd2-125">Problemy z produktem i pytania dotyczące produktów w [witrynie Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span><span class="sxs-lookup"><span data-stu-id="87dd2-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="87dd2-126">Wkład produktu powinien być dokonywany w jednym z repozytoriów projektu, takich jak [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk,](https://github.com/dotnet/sdk) [dotnet/rosyln](https://github.com/dotnet/roslyn)lub [aspnetcore](https://github.com/dotnet/aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="87dd2-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="87dd2-127">Aby uzyskać więcej informacji, zobacz [.NET Core repo](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span><span class="sxs-lookup"><span data-stu-id="87dd2-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="87dd2-128">Pomoc techniczna</span><span class="sxs-lookup"><span data-stu-id="87dd2-128">Support</span></span>

<span data-ttu-id="87dd2-129">.NET Core jest obsługiwany przez firmę Microsoft w systemach Windows, macOS i Linux oraz przez Red Hat na Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="87dd2-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="87dd2-130">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="87dd2-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="87dd2-131">Samouczki .NET Core</span><span class="sxs-lookup"><span data-stu-id="87dd2-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="87dd2-132">Wypróbuj program .NET Core w przeglądarce</span><span class="sxs-lookup"><span data-stu-id="87dd2-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
