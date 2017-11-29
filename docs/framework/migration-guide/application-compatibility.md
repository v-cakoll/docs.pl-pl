---
title: "Zgodność aplikacji w programie .NET Framework"
ms.custom: 
ms.date: 05/19/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
- app-compat
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
caps.latest.revision: "19"
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e67fff19c4b187010b35519081f46e11effbad6c
ms.sourcegitcommit: d0f7646d67db5809cf43ff1d27b399a4020e8ee2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2017
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="39583-102">Zgodność aplikacji w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="39583-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="39583-103">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="39583-103">Introduction</span></span>
<span data-ttu-id="39583-104">Zgodność jest bardzo ważne celem każdej wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="39583-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="39583-105">Zgodności zapewni, że każda wersja dodatku, więc poprzedniej wersji będą nadal działać.</span><span class="sxs-lookup"><span data-stu-id="39583-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="39583-106">Z drugiej strony zmiany w funkcjonalności poprzedniego (w celu zwiększenia wydajności i rozwiązać problemy zabezpieczeń, lub błędów) może spowodować problemy ze zgodnością w istniejący kod lub istniejące aplikacje uruchamiane w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="39583-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="39583-107">.NET Framework rozpoznaje zmiany retargetingu i środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="39583-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="39583-108">Zmiany retargetingu wpływ na aplikacje docelowe określonej wersji programu .NET Framework, ale są uruchomione w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="39583-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="39583-109">Zmiany środowiska uruchomieniowego wpływają na wszystkie aplikacje uruchomione na określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="39583-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="39583-110">Każda aplikacja jest przeznaczony dla określonej wersji programu .NET Framework, który może zostać określony przez:</span><span class="sxs-lookup"><span data-stu-id="39583-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

* <span data-ttu-id="39583-111">Definiowanie platformy docelowej w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="39583-111">Defining a target framework in Visual Studio.</span></span>
* <span data-ttu-id="39583-112">Określenie platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="39583-112">Specifying the target framework in a project file.</span></span>
* <span data-ttu-id="39583-113">Stosowanie <xref:System.Runtime.Versioning.TargetFrameworkAttribute> do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="39583-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="39583-114">Uruchomionej na nowszą wersję niż co był przeznaczony quirked zachowanie programu .NET Framework będą używane do naśladować starszą wersję docelową.</span><span class="sxs-lookup"><span data-stu-id="39583-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="39583-115">Innymi słowy aplikacja będzie uruchomić na nowszą wersję Framework, ale działa tak, jakby działa w starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="39583-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="39583-116">Wiele problemów ze zgodnością między wersjami programu .NET Framework, zostały skorygowane przez ten model quirking.</span><span class="sxs-lookup"><span data-stu-id="39583-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="39583-117">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="39583-117">Runtime changes</span></span>

<span data-ttu-id="39583-118">Problemy dotyczące środowiska uruchomieniowego to wystąpić, gdy nowe środowisko uruchomieniowe znajduje się na komputerze i są uruchamiane w tej samej plików binarnych, ale pojawia się inaczej.</span><span class="sxs-lookup"><span data-stu-id="39583-118">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="39583-119">Jeśli dane binarne został skompilowany dla platformy .NET Framework 4.0, zostanie uruchomiony w trybie zgodności programu .NET Framework 4.0, 4.5 lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="39583-119">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="39583-120">Wiele zmian, które mają wpływ na 4.5 nie dotyczy pliku binarnego skompilowana dla wersji 4.0.</span><span class="sxs-lookup"><span data-stu-id="39583-120">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="39583-121">To jest specyficzne dla domeny aplikacji i zależy od ustawień zestawu wpisu.</span><span class="sxs-lookup"><span data-stu-id="39583-121">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="39583-122">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="39583-122">Retargeting changes</span></span>

<span data-ttu-id="39583-123">Problemy przekierowania to wystąpić, gdy zestaw, który był celem 4.0 jest teraz skonfigurowana do docelowego 4.5.</span><span class="sxs-lookup"><span data-stu-id="39583-123">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="39583-124">Zestaw zdecyduje się teraz do nowych funkcji, a także potencjalnych problemów ze zgodnością ze starego funkcji.</span><span class="sxs-lookup"><span data-stu-id="39583-124">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="39583-125">Ponownie, to jest zależna zestawu wpisu, więc aplikacji konsoli, która używa zestawu lub witryny sieci Web, który odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="39583-125">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="39583-126">Diagnostyka zgodności platformy .NET</span><span class="sxs-lookup"><span data-stu-id="39583-126">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="39583-127">Diagnostyka zgodności .NET są zasilane Roslyn analizatorów, które pomagają zidentyfikować problemy ze zgodnością aplikacji między wersjami programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39583-127">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="39583-128">Ta lista zawiera wszystkie analizatory dostępne, mimo że tylko podzestaw będą stosowane do dowolnego migracji.</span><span class="sxs-lookup"><span data-stu-id="39583-128">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="39583-129">Analizatory określają problemy, które mają zastosowanie w przypadku planowanej migracji i tylko powierzchni te.</span><span class="sxs-lookup"><span data-stu-id="39583-129">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="39583-130">Każde wydanie obejmuje następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="39583-130">Each issue includes the following information:</span></span>

-   <span data-ttu-id="39583-131">Opis zmiany z poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="39583-131">The description of what has changed from a previous version.</span></span>

-   <span data-ttu-id="39583-132">Jak zmiana wpływa na klientów oraz czy wszystkie obejścia są dostępne w celu zachowania zgodności między wersjami.</span><span class="sxs-lookup"><span data-stu-id="39583-132">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

-   <span data-ttu-id="39583-133">Ocena jak ważna jest zmiana.</span><span class="sxs-lookup"><span data-stu-id="39583-133">An assessment of how important the change is.</span></span> <span data-ttu-id="39583-134">Problem ze zgodnością aplikacji są podzielone na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="39583-134">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="39583-135">Główne</span><span class="sxs-lookup"><span data-stu-id="39583-135">Major</span></span>|<span data-ttu-id="39583-136">Znaczące zmiany, która ma wpływ na wiele aplikacji lub wymaga znacznej modyfikacji kodu.</span><span class="sxs-lookup"><span data-stu-id="39583-136">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="39583-137">Pomocnicza</span><span class="sxs-lookup"><span data-stu-id="39583-137">Minor</span></span>|<span data-ttu-id="39583-138">Zmiana, który wpływa na małej liczby aplikacji lub wymagają drobne zmiany kodu.</span><span class="sxs-lookup"><span data-stu-id="39583-138">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="39583-139">Przypadek krawędzi</span><span class="sxs-lookup"><span data-stu-id="39583-139">Edge case</span></span>|<span data-ttu-id="39583-140">Zmiana wpływa na aplikacje w scenariuszach bardzo określone, rzadko.</span><span class="sxs-lookup"><span data-stu-id="39583-140">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="39583-141">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="39583-141">Transparent</span></span>|<span data-ttu-id="39583-142">Zmiana nie wpływa na deweloperem aplikacji lub użytkownika.</span><span class="sxs-lookup"><span data-stu-id="39583-142">A change with no noticeable effect on the application's developer or user.</span></span>|

-   <span data-ttu-id="39583-143">Wersja wskazuje, kiedy zmiany najpierw zostanie wyświetlony w ramach.</span><span class="sxs-lookup"><span data-stu-id="39583-143">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="39583-144">Niektóre zmiany są wprowadzane w przypadku konkretnej wersji i przywrócone w nowszej wersji; który wskazane jest także.</span><span class="sxs-lookup"><span data-stu-id="39583-144">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

-   <span data-ttu-id="39583-145">Typ zmiany:</span><span class="sxs-lookup"><span data-stu-id="39583-145">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="39583-146">Przekierowania</span><span class="sxs-lookup"><span data-stu-id="39583-146">Retargeting</span></span>|<span data-ttu-id="39583-147">Zmiana wpływa na aplikacje, które są ponownie skompilowana do nowej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39583-147">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="39583-148">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="39583-148">Runtime</span></span>|<span data-ttu-id="39583-149">Zmiana wpływa na istniejących aplikacji, która jest przeznaczony dla poprzedniej wersji programu .NET Framework, ale działa w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="39583-149">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

-   <span data-ttu-id="39583-150">Dotyczy interfejsy API, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="39583-150">The affected APIS, if any.</span></span>

-   <span data-ttu-id="39583-151">Identyfikatory dostępne diagnostyki</span><span class="sxs-lookup"><span data-stu-id="39583-151">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="39583-152">Użycie</span><span class="sxs-lookup"><span data-stu-id="39583-152">Usage</span></span>
<span data-ttu-id="39583-153">Aby rozpocząć, wybierz typ zmiany zgodności poniżej:</span><span class="sxs-lookup"><span data-stu-id="39583-153">To begin, select the type of compatibility change below:</span></span>

* [<span data-ttu-id="39583-154">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="39583-154">Retargeting Changes</span></span>](./retargeting/index.md)
* [<span data-ttu-id="39583-155">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="39583-155">Runtime Changes</span></span>](./runtime/index.md)


## <a name="see-also"></a><span data-ttu-id="39583-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39583-156">See Also</span></span>

* [<span data-ttu-id="39583-157">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="39583-157">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [<span data-ttu-id="39583-158">Nowości</span><span class="sxs-lookup"><span data-stu-id="39583-158">What's New</span></span>](../../../docs/framework/whats-new/index.md)
* [<span data-ttu-id="39583-159">Co to jest przestarzałe w bibliotece klas</span><span class="sxs-lookup"><span data-stu-id="39583-159">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)
