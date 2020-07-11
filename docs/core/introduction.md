---
title: Wprowadzenie do platformy .NET Core i Omówienie
description: .NET Core to modularna, wielowydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i macOS. Dowiedz się więcej o programie .NET Core, aby rozpocząć pracę.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: b28ad965e54680e2e1134c389266741ade28084f
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226585"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="75054-104">Wprowadzenie do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="75054-104">Introduction to .NET Core</span></span>

<span data-ttu-id="75054-105">[.NET Core](about.md) to platforma programistyczna [Open Source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT).</span><span class="sxs-lookup"><span data-stu-id="75054-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="75054-106">Możesz tworzyć aplikacje .NET Core dla systemów Windows, macOS i Linux dla procesorów x64, x86, ARM32 i ARM64 przy użyciu wielu języków programowania.</span><span class="sxs-lookup"><span data-stu-id="75054-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="75054-107">Platformy i interfejsy API są udostępniane dla [chmur](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [interfejsu użytkownika klienta](../desktop-wpf/overview/index.md)i [uczenia maszynowego](/dotnet/machine-learning/).</span><span class="sxs-lookup"><span data-stu-id="75054-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="75054-108">[Pobierz zestaw .NET Core SDK,](https://dotnet.microsoft.com/download) aby wypróbować platformę .NET Core na swojej maszynie.</span><span class="sxs-lookup"><span data-stu-id="75054-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="75054-109">Najnowsza wersja to [.NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="75054-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="75054-110">Pobierz program .NET Core</span><span class="sxs-lookup"><span data-stu-id="75054-110">Download .NET Core</span></span>

<span data-ttu-id="75054-111">Platformę .NET Core można uzyskać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="75054-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="75054-112">Instalatory dla systemu Windows i macOS</span><span class="sxs-lookup"><span data-stu-id="75054-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="75054-113">Pakiety systemu Linux</span><span class="sxs-lookup"><span data-stu-id="75054-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="75054-114">Kontenery platformy Docker</span><span class="sxs-lookup"><span data-stu-id="75054-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="75054-115">Zips i tarballs</span><span class="sxs-lookup"><span data-stu-id="75054-115">Zips and tarballs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="75054-116">Zainstaluj skrypty</span><span class="sxs-lookup"><span data-stu-id="75054-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="75054-117">Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="75054-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="75054-118">Tworzenie pierwszej aplikacji</span><span class="sxs-lookup"><span data-stu-id="75054-118">Create your first application</span></span>

<span data-ttu-id="75054-119">Po zainstalowaniu zestaw .NET Core SDK Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="75054-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="75054-120">Użyj następujących poleceń, aby utworzyć i uruchomić aplikację:</span><span class="sxs-lookup"><span data-stu-id="75054-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="75054-121">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="75054-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="75054-122">Współtworzenie</span><span class="sxs-lookup"><span data-stu-id="75054-122">Contribute</span></span>

<span data-ttu-id="75054-123">.NET Core to otwarta platforma.</span><span class="sxs-lookup"><span data-stu-id="75054-123">.NET Core is an open platform.</span></span> <span data-ttu-id="75054-124">Wszyscy to zapraszamy do wzięcia udziału.</span><span class="sxs-lookup"><span data-stu-id="75054-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="75054-125">Problemy związane z produktem i pytania w [społeczności deweloperów](https://developercommunity.visualstudio.com/spaces/61/index.html).</span><span class="sxs-lookup"><span data-stu-id="75054-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="75054-126">Udziały produktów należy wprowadzać na jednym z repozytoriów projektu, takich jak [dotnet/Runtime](https://github.com/dotnet/runtime), [dotnet/SDK](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn)lub [aspnetcore](https://github.com/dotnet/aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="75054-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="75054-127">Aby uzyskać więcej informacji, zobacz temat [repozytoria .NET Core](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span><span class="sxs-lookup"><span data-stu-id="75054-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="75054-128">Pomoc techniczna</span><span class="sxs-lookup"><span data-stu-id="75054-128">Support</span></span>

<span data-ttu-id="75054-129">Platforma .NET Core jest obsługiwana przez firmę Microsoft w systemach Windows, macOS i Linux oraz w systemie Red Hat na Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="75054-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="75054-130">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="75054-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="75054-131">Samouczki dotyczące platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="75054-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="75054-132">Wypróbuj platformę .NET Core w przeglądarce</span><span class="sxs-lookup"><span data-stu-id="75054-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
