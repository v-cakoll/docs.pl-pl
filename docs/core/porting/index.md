---
title: Port z .NET Framework do platformy .NET Core
description: Poznaj proces przenoszenia i odnajdywanie narzędzi, które mogą okazać się przydatne podczas przenoszenia projektu .NET Framework do programu .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: b5b010acbccf134afe800aa5bb98a0ae6e9ffa25
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777359"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a><span data-ttu-id="bda41-103">Przegląd portów z .NET Framework do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="bda41-103">Overview of porting from .NET Framework to .NET Core</span></span>

<span data-ttu-id="bda41-104">Być może masz kod, który jest obecnie uruchomiony na .NET Framework, które interesują się portem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda41-104">You might have code that currently runs on the .NET Framework that you're interested in porting to .NET Core.</span></span> <span data-ttu-id="bda41-105">Ten artykuł zawiera:</span><span class="sxs-lookup"><span data-stu-id="bda41-105">This article provides:</span></span>

* <span data-ttu-id="bda41-106">Przegląd procesu przenoszenia.</span><span class="sxs-lookup"><span data-stu-id="bda41-106">An overview of the porting process.</span></span>
* <span data-ttu-id="bda41-107">Lista narzędzi, które mogą być przydatne podczas przenoszenia kodu do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda41-107">A list of tools that you may find helpful when you're porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="bda41-108">Przegląd procesu przenoszenia</span><span class="sxs-lookup"><span data-stu-id="bda41-108">Overview of the porting process</span></span>

<span data-ttu-id="bda41-109">Zalecamy użycie następującego procesu podczas przenoszenia projektu do programu .NET Core:</span><span class="sxs-lookup"><span data-stu-id="bda41-109">We recommend you use the following process when porting your project to .NET Core:</span></span>

1. <span data-ttu-id="bda41-110">Przekieruj wszystkie projekty, które chcesz przenieść do elementu docelowego .NET Framework 4.7.2 lub wyższy.</span><span class="sxs-lookup"><span data-stu-id="bda41-110">Retarget all projects you wish to port to target .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="bda41-111">Ten krok zapewnia, że można użyć alternatywnych interfejsów API dla konkretnych .NET Framework docelowych, gdy platforma .NET Core nie obsługuje określonego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="bda41-111">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

2. <span data-ttu-id="bda41-112">Użyj [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) do analizowania zestawów i sprawdź, czy są one przenośne do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda41-112">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and see if they're portable to .NET Core.</span></span>

   <span data-ttu-id="bda41-113">Narzędzie analizatora przenośności API analizuje skompilowane zestawy i generuje raport.</span><span class="sxs-lookup"><span data-stu-id="bda41-113">The API Portability Analyzer tool analyzes your compiled assemblies and generates a report.</span></span> <span data-ttu-id="bda41-114">Ten raport przedstawia podsumowanie wysokiego poziomu dotyczące przenoszenia i podział wszystkich używanych interfejsów API, które nie są dostępne w systemie NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda41-114">This report shows a high-level portability summary and a breakdown of each API you're using that isn't available on NET Core.</span></span>

3. <span data-ttu-id="bda41-115">Zainstaluj [Analizator interfejsów API platformy .NET](../../standard/analyzers/api-analyzer.md) w swoich projektach, aby identyfikować interfejsy API zgłaszające <xref:System.PlatformNotSupportedException> na niektórych platformach oraz inne potencjalne problemy ze zgodnością.</span><span class="sxs-lookup"><span data-stu-id="bda41-115">Install the [.NET API analyzer](../../standard/analyzers/api-analyzer.md) into your projects to identify APIs throwing <xref:System.PlatformNotSupportedException> on some platforms and some other potential compatibility issues.</span></span>

   <span data-ttu-id="bda41-116">To narzędzie jest podobne do analizatora przenośności, ale zamiast analizowania, jeśli elementy mogą być kompilowane na platformie .NET Core, są analizowane, jeśli używasz interfejsu API w sposób, który będzie generować <xref:System.PlatformNotSupportedException> w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bda41-116">This tool is similar to the portability analyzer, but instead of analyzing if things can build on .NET Core, it analyzes if you're using an API in a way that will throw the <xref:System.PlatformNotSupportedException> at run time.</span></span> <span data-ttu-id="bda41-117">Chociaż nie jest to typowe w przypadku przechodzenia z .NET Framework 4.7.2 lub wyższym, warto sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="bda41-117">Although this isn't common if you're moving from .NET Framework 4.7.2 or higher, it's good to check.</span></span>

4. <span data-ttu-id="bda41-118">Przekonwertuj wszystkie zależności `packages.config` na format [PackageReference](/nuget/consume-packages/package-references-in-project-files) za pomocą [narzędzia konwersji w programie Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="bda41-118">Convert all of your `packages.config` dependencies to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format with the [conversion tool in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span>

   <span data-ttu-id="bda41-119">Ten krok obejmuje przekonwertowanie zależności ze starszego formatu `packages.config`.</span><span class="sxs-lookup"><span data-stu-id="bda41-119">This step involves converting your dependencies from the legacy `packages.config` format.</span></span> <span data-ttu-id="bda41-120">`packages.config` nie działa w oprogramowaniu .NET Core, dlatego ta konwersja jest wymagana, jeśli istnieją zależności pakietów.</span><span class="sxs-lookup"><span data-stu-id="bda41-120">`packages.config` doesn't work on .NET Core, so this conversion is required if you have package dependencies.</span></span>

5. <span data-ttu-id="bda41-121">Utwórz nowe projekty dla platformy .NET Core i skopiuj pliki źródłowe lub spróbuj skonwertować istniejący plik projektu za pomocą narzędzia.</span><span class="sxs-lookup"><span data-stu-id="bda41-121">Create new projects for .NET Core and copy over source files, or attempt to convert your existing project file with a tool.</span></span>

   <span data-ttu-id="bda41-122">W przypadku programu .NET Core jest stosowany uproszczony (i różny) [Format pliku projektu](../tools/csproj.md) niż .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bda41-122">.NET Core uses a simplified (and different) [project file format](../tools/csproj.md) than .NET Framework.</span></span> <span data-ttu-id="bda41-123">Aby kontynuować, musisz przekonwertować pliki projektu w ten format.</span><span class="sxs-lookup"><span data-stu-id="bda41-123">You'll need to convert your project files into this format to continue.</span></span>

6. <span data-ttu-id="bda41-124">Port kodu testu.</span><span class="sxs-lookup"><span data-stu-id="bda41-124">Port your test code.</span></span>

   <span data-ttu-id="bda41-125">Ponieważ przenoszenie do programu .NET Core to znacząca zmiana w bazie kodu, zdecydowanie zaleca się, aby przenieść projekty testowe, aby można było uruchamiać testy podczas przenoszenia kodu do trybu.</span><span class="sxs-lookup"><span data-stu-id="bda41-125">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to port your test projects so that you can run tests as you port your code over.</span></span> <span data-ttu-id="bda41-126">MSTest, xUnit i NUnit działają na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda41-126">MSTest, xUnit, and NUnit all work on .NET Core.</span></span>

<span data-ttu-id="bda41-127">Ponadto możesz próbować przenieść mniejsze rozwiązania lub pojedyncze projekty w jednej operacji do formatu pliku projektu .NET Core za pomocą narzędzia [dotnet try-Convert](https://github.com/dotnet/try-convert) .</span><span class="sxs-lookup"><span data-stu-id="bda41-127">Additionally, you can attempt to port smaller solutions or individual projects in one operation to the .NET Core project file format with the [dotnet try-convert](https://github.com/dotnet/try-convert) tool.</span></span> <span data-ttu-id="bda41-128">`dotnet try-convert` nie ma gwarancji dla wszystkich projektów i może spowodować drobne zmiany w zachowaniu, od którego zależy.</span><span class="sxs-lookup"><span data-stu-id="bda41-128">`dotnet try-convert` is not guaranteed to work for all your projects, and it may cause subtle changes in behavior that you depended on.</span></span> <span data-ttu-id="bda41-129">Użyj jej jako _punktu wyjścia_ , który automatyzuje podstawowe elementy, które mogą być zautomatyzowane.</span><span class="sxs-lookup"><span data-stu-id="bda41-129">Use it as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="bda41-130">Nie jest to gwarantowane rozwiązanie do migracji projektu.</span><span class="sxs-lookup"><span data-stu-id="bda41-130">It isn't a guaranteed solution to migrating a project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bda41-131">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="bda41-131">Next steps</span></span>

>[!div class="nextstepaction"]
>[<span data-ttu-id="bda41-132">Niedostępne technologie w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="bda41-132">Unavailable technologies on .NET Core</span></span>](net-framework-tech-unavailable.md)
