---
title: Przewodnik platformy .NET Core
description: .NET Core to modularna, wielowydajna implementacja platformy .NET do tworzenia aplikacji dla systemów Windows, Linux i Mac. Dowiedz się więcej o programie .NET Core, aby rozpocząć pracę.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: a6112851a3d9b46f02c26313e6537170786df10b
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117073"
---
# <a name="net-core-guide"></a><span data-ttu-id="efcb2-104">Przewodnik platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="efcb2-104">.NET Core Guide</span></span>

<span data-ttu-id="efcb2-105">[.NET Core](about.md) to platforma programistyczna ["Open Source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)", która jest obsługiwana przez firmę Microsoft i społeczność programu .NET w serwisie [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="efcb2-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="efcb2-106">Jest to międzyplatformowe (pomocnicze systemy Windows, macOS i Linux) i mogą być używane do tworzenia aplikacji dla urządzeń, usług w chmurze i IoT.</span><span class="sxs-lookup"><span data-stu-id="efcb2-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="efcb2-107">Zobacz [Informacje o programie .NET Core](about.md) , aby dowiedzieć się więcej na temat platformy .NET Core, w tym jej cech, obsługiwanych języków i struktur oraz kluczowych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="efcb2-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="efcb2-108">Zapoznaj się z [samouczkami dotyczącymi platformy .NET Core](tutorials/index.md) , aby dowiedzieć się, jak utworzyć prostą aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="efcb2-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="efcb2-109">Rozpoczęcie pracy z pierwszą aplikacją może zająć zaledwie kilka minut.</span><span class="sxs-lookup"><span data-stu-id="efcb2-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="efcb2-110">Jeśli chcesz wypróbować platformę .NET Core w przeglądarce, poszukaj [cyfr w C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) samouczku online.</span><span class="sxs-lookup"><span data-stu-id="efcb2-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core-22"></a><span data-ttu-id="efcb2-111">Pobierz program .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="efcb2-111">Download .NET Core 2.2</span></span>

<span data-ttu-id="efcb2-112">Pobierz [zestaw .net core 2,2 SDK](https://dotnet.microsoft.com/download) , aby wypróbować platformę .NET Core na komputerze z systemem Windows, MacOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="efcb2-112">Download the [.NET Core  2.2 SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="efcb2-113">Jeśli wolisz używać kontenerów platformy Docker, odwiedź stronę [dotnet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) .</span><span class="sxs-lookup"><span data-stu-id="efcb2-113">Visit [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="efcb2-114">Wszystkie wersje programu .NET Core są dostępne w [programie .NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core) , jeśli szukasz innej wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="efcb2-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-22"></a><span data-ttu-id="efcb2-115">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="efcb2-115">.NET Core 2.2</span></span>

<span data-ttu-id="efcb2-116">Najnowsza wersja to [.NET Core 2,2](whats-new/dotnet-core-2-2.md).</span><span class="sxs-lookup"><span data-stu-id="efcb2-116">The latest version is [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span></span> <span data-ttu-id="efcb2-117">Nowe funkcje obejmują: wdrożenia zależne od platformy, punkty uruchomienia, uwierzytelnianie w usłudze AAD z użyciem usługi Azure SQL i obsługę systemu Windows ARM32.</span><span class="sxs-lookup"><span data-stu-id="efcb2-117">New features include: framework-dependent deployments, startup hooks, AAD authentication with Azure SQL, and support for Windows ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="efcb2-118">Tworzenie pierwszej aplikacji</span><span class="sxs-lookup"><span data-stu-id="efcb2-118">Create your first application</span></span>

<span data-ttu-id="efcb2-119">Po zainstalowaniu zestaw .NET Core SDK Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="efcb2-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="efcb2-120">Wpisz następujące `dotnet` polecenia, aby utworzyć i uruchomić C# aplikację.</span><span class="sxs-lookup"><span data-stu-id="efcb2-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="efcb2-121">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="efcb2-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="efcb2-122">Pomoc techniczna</span><span class="sxs-lookup"><span data-stu-id="efcb2-122">Support</span></span>

<span data-ttu-id="efcb2-123">Platforma .NET Core jest [obsługiwana przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy), w systemach Windows, MacOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="efcb2-123">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="efcb2-124">Jest ona aktualizowana pod kątem bezpieczeństwa i jakości kilka razy w roku, zazwyczaj co miesiąc.</span><span class="sxs-lookup"><span data-stu-id="efcb2-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="efcb2-125">Dystrybucje binarne programu .NET Core są kompilowane i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i są obsługiwane w taki sam sposób jak każdy produkt firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="efcb2-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="efcb2-126">[Red Hat obsługuje platformę .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="efcb2-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="efcb2-127">Red Hat kompiluje platformę .NET Core ze źródła i udostępnia je w [kolekcjach oprogramowania Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="efcb2-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="efcb2-128">Red Hat i Microsoft Współpracuj, aby upewnić się, że .NET Core działa dobrze na RHEL.</span><span class="sxs-lookup"><span data-stu-id="efcb2-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
