---
title: Eksportowanie do platformy .NET Core z .NET Framework
description: Opis procesu przenoszenia i odnajdywanie narzędzia, które mogą być przydatne podczas przenoszenia projekt .NET Framework .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 2f943caff23ddbfcd5c845c9f517d24aea089850
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="porting-to-net-core-from-net-framework"></a><span data-ttu-id="ccb44-103">Eksportowanie do platformy .NET Core z .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ccb44-103">Porting to .NET Core from .NET Framework</span></span>

<span data-ttu-id="ccb44-104">Jeśli masz kodu uruchomionego w programie .NET Framework może Cię zainteresować systemem kodu .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="ccb44-104">If you've got code running on the .NET Framework, you may be interested in running your code on .NET Core 1.0.</span></span>  <span data-ttu-id="ccb44-105">Ten artykuł zawiera omówienie procesu przenoszenia listę narzędzi, które mogą być przydatne przy eksportowaniu na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ccb44-105">This article covers an overview of the porting process and a list of the tools you may find helpful when porting to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="ccb44-106">Omówienie procesu przenoszenia</span><span class="sxs-lookup"><span data-stu-id="ccb44-106">Overview of the Porting Process</span></span>

<span data-ttu-id="ccb44-107">Zalecany proces przy eksportowaniu obejmuje następujące serie kroków.</span><span class="sxs-lookup"><span data-stu-id="ccb44-107">The recommended process for porting follows the following series of steps.</span></span>  <span data-ttu-id="ccb44-108">Każdy z tych elementów procesu są opisane bardziej szczegółowo w dalszej artykułach.</span><span class="sxs-lookup"><span data-stu-id="ccb44-108">Each of these parts of the process are covered in more detail in further articles.</span></span>

1. <span data-ttu-id="ccb44-109">Identyfikowanie i konta dla zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="ccb44-109">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="ccb44-110">Obejmuje understanding jakie zależności innych firm są, jak zależeć na ich sposób, aby sprawdzić, czy są one również uruchomić na oprogramowanie .NET Core i kroki można wykonać, jeśli tak nie jest.</span><span class="sxs-lookup"><span data-stu-id="ccb44-110">This will involve understanding what your third-party dependencies are, how you depend on them, how to see if they also run on .NET Core, and steps you can take if they don't.</span></span>
   
2. <span data-ttu-id="ccb44-111">Przekieruj wszystkie projekty, które chcesz dodać port do docelowej platformy .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="ccb44-111">Retarget all projects you wish to port to target .NET Framework 4.6.2.</span></span>

   <span data-ttu-id="ccb44-112">Dzięki temu, że można użyć interfejsu API alternatyw dla celów specyficzne dla platformy .NET Framework w przypadkach, gdy oprogramowanie .NET Core nie obsługuje określonego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="ccb44-112">This ensures that you can use API alternatives for .NET Framework-specific targets in the cases where .NET Core can't support a particular API.</span></span>
   
3. <span data-ttu-id="ccb44-113">Użyj [narzędzia Analizator przenośność interfejsu API](https://github.com/Microsoft/dotnet-apiport/) do analizowania ponownie zestawy i opracowanie planu portu, na podstawie jej wyników.</span><span class="sxs-lookup"><span data-stu-id="ccb44-113">Use the [API Portability Analyzer tool](https://github.com/Microsoft/dotnet-apiport/) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="ccb44-114">Narzędzie Analizator przenośność interfejsu API analizowanie ponownie skompilowane zestawy i Generowanie raportu, który znajduje się podsumowanie wysokiego poziomu przenośność i podział każdego interfejsu API używasz niedostępny na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ccb44-114">The API Portability Analyzer tool will analyze your compiled assemblies and generate a report which shows a high-level portability summary and a breakdown of each API you're using that isn't available on .NET Core.</span></span>  <span data-ttu-id="ccb44-115">Ten raport z analizy można użyć programu codebase aby opracować plan dla jak będzie port kodu za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="ccb44-115">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>
   
4. <span data-ttu-id="ccb44-116">Port kodu testy.</span><span class="sxs-lookup"><span data-stu-id="ccb44-116">Port your tests code.</span></span>

   <span data-ttu-id="ccb44-117">Eksportowanie do platformy .NET Core jest duży zmiany do baza kodu, ma zalecane uzyskanie przenoszone, aby uruchomić testy zgodnie z portu kodu w testach.</span><span class="sxs-lookup"><span data-stu-id="ccb44-117">Because porting to .NET Core is such a big change to your codebase, it's highly recommended to get your tests ported so that you can run tests as you port code over.</span></span>  <span data-ttu-id="ccb44-118">MSTest, xUnit i NUnit obsługuje obecnie .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="ccb44-118">MSTest, xUnit, and NUnit all support .NET Core 1.0 today.</span></span>
   
6. <span data-ttu-id="ccb44-119">Wykonanie planu przy eksportowaniu!</span><span class="sxs-lookup"><span data-stu-id="ccb44-119">Execute your plan for porting!</span></span>

## <a name="tools-to-help"></a><span data-ttu-id="ccb44-120">Narzędzia ułatwiające</span><span class="sxs-lookup"><span data-stu-id="ccb44-120">Tools to help</span></span>

<span data-ttu-id="ccb44-121">Poniżej przedstawiono krótką listę narzędzi, które znajdują się pomocne:</span><span class="sxs-lookup"><span data-stu-id="ccb44-121">Here's a short list of the tools you'll find helpful:</span></span>

* <span data-ttu-id="ccb44-122">NuGet - [klienta Nuget](https://dist.nuget.org/index.html) lub [Explorer pakietu NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Menedżer pakietów firmy Microsoft dla implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="ccb44-122">NuGet - [Nuget Client](https://dist.nuget.org/index.html) or [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft's package manager for .NET implementations.</span></span>
* <span data-ttu-id="ccb44-123">Analizator przenośność interfejsu API - [narzędzia wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases) lub [rozszerzenie programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), łańcuch narzędzi, które można wygenerować raport jak przenośnego kodu jest między .NET Framework i .NET Core z Podział zestawu przez zestaw problemów.</span><span class="sxs-lookup"><span data-stu-id="ccb44-123">Api Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core, with an assembly-by-assembly breakdown of issues.</span></span>  <span data-ttu-id="ccb44-124">Zobacz [narzędzi, aby ułatwić proces](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="ccb44-124">See [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) for more information.</span></span>
* <span data-ttu-id="ccb44-125">Wstecznego wyszukiwania pakietu - A [usługi sieci web przydatne](https://packagesearch.azurewebsites.net) który służy do wyszukiwania typów i Znajdź pakiety zawierające tego typu.</span><span class="sxs-lookup"><span data-stu-id="ccb44-125">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ccb44-126">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ccb44-126">Next steps</span></span>

[<span data-ttu-id="ccb44-127">Analizowanie zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="ccb44-127">Analyzing your third-party dependencies.</span></span>](third-party-deps.md)
   
