---
title: Zgodność aplikacji w programie .NET Framework
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b75429d0de69c60e7c24551bf1d9218e74d0c5ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="9c23c-102">Zgodność aplikacji w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9c23c-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="9c23c-103">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="9c23c-103">Introduction</span></span>
<span data-ttu-id="9c23c-104">Zgodność jest bardzo ważne celem każdej wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="9c23c-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="9c23c-105">Zgodności zapewni, że każda wersja dodatku, więc poprzedniej wersji będą nadal działać.</span><span class="sxs-lookup"><span data-stu-id="9c23c-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="9c23c-106">Z drugiej strony zmiany w funkcjonalności poprzedniego (w celu zwiększenia wydajności i rozwiązać problemy zabezpieczeń, lub błędów) może spowodować problemy ze zgodnością w istniejący kod lub istniejące aplikacje uruchamiane w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="9c23c-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="9c23c-107">.NET Framework rozpoznaje zmiany retargetingu i środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="9c23c-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="9c23c-108">Zmiany retargetingu wpływ na aplikacje docelowe określonej wersji programu .NET Framework, ale są uruchomione w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="9c23c-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="9c23c-109">Zmiany środowiska uruchomieniowego wpływają na wszystkie aplikacje uruchomione na określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="9c23c-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="9c23c-110">Każda aplikacja jest przeznaczony dla określonej wersji programu .NET Framework, który może zostać określony przez:</span><span class="sxs-lookup"><span data-stu-id="9c23c-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

* <span data-ttu-id="9c23c-111">Definiowanie platformy docelowej w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c23c-111">Defining a target framework in Visual Studio.</span></span>
* <span data-ttu-id="9c23c-112">Określenie platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9c23c-112">Specifying the target framework in a project file.</span></span>
* <span data-ttu-id="9c23c-113">Stosowanie <xref:System.Runtime.Versioning.TargetFrameworkAttribute> do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="9c23c-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="9c23c-114">Uruchomionej na nowszą wersję niż co był przeznaczony quirked zachowanie programu .NET Framework będą używane do naśladować starszą wersję docelową.</span><span class="sxs-lookup"><span data-stu-id="9c23c-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="9c23c-115">Innymi słowy aplikacja będzie uruchomić na nowszą wersję Framework, ale działa tak, jakby działa w starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="9c23c-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="9c23c-116">Wiele problemów ze zgodnością między wersjami programu .NET Framework, zostały skorygowane przez ten model quirking.</span><span class="sxs-lookup"><span data-stu-id="9c23c-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="9c23c-117">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9c23c-117">Runtime changes</span></span>

<span data-ttu-id="9c23c-118">Problemy dotyczące środowiska uruchomieniowego to wystąpić, gdy nowe środowisko uruchomieniowe znajduje się na komputerze i są uruchamiane w tej samej plików binarnych, ale pojawia się inaczej.</span><span class="sxs-lookup"><span data-stu-id="9c23c-118">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="9c23c-119">Jeśli dane binarne został skompilowany dla platformy .NET Framework 4.0, zostanie uruchomiony w trybie zgodności programu .NET Framework 4.0, 4.5 lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="9c23c-119">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="9c23c-120">Wiele zmian, które mają wpływ na 4.5 nie dotyczy pliku binarnego skompilowana dla wersji 4.0.</span><span class="sxs-lookup"><span data-stu-id="9c23c-120">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="9c23c-121">To jest specyficzne dla domeny aplikacji i zależy od ustawień zestawu wpisu.</span><span class="sxs-lookup"><span data-stu-id="9c23c-121">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="9c23c-122">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="9c23c-122">Retargeting changes</span></span>

<span data-ttu-id="9c23c-123">Problemy przekierowania to wystąpić, gdy zestaw, który był celem 4.0 jest teraz skonfigurowana do docelowego 4.5.</span><span class="sxs-lookup"><span data-stu-id="9c23c-123">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="9c23c-124">Zestaw zdecyduje się teraz do nowych funkcji, a także potencjalnych problemów ze zgodnością ze starego funkcji.</span><span class="sxs-lookup"><span data-stu-id="9c23c-124">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="9c23c-125">Ponownie, to jest zależna zestawu wpisu, więc aplikacji konsoli, która używa zestawu lub witryny sieci Web, który odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c23c-125">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="9c23c-126">Diagnostyka zgodności platformy .NET</span><span class="sxs-lookup"><span data-stu-id="9c23c-126">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="9c23c-127">Diagnostyka zgodności .NET są zasilane Roslyn analizatorów, które pomagają zidentyfikować problemy ze zgodnością aplikacji między wersjami programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c23c-127">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="9c23c-128">Ta lista zawiera wszystkie analizatory dostępne, mimo że tylko podzestaw będą stosowane do dowolnego migracji.</span><span class="sxs-lookup"><span data-stu-id="9c23c-128">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="9c23c-129">Analizatory określają problemy, które mają zastosowanie w przypadku planowanej migracji i tylko powierzchni te.</span><span class="sxs-lookup"><span data-stu-id="9c23c-129">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="9c23c-130">Każde wydanie obejmuje następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="9c23c-130">Each issue includes the following information:</span></span>

-   <span data-ttu-id="9c23c-131">Opis zmiany z poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="9c23c-131">The description of what has changed from a previous version.</span></span>

-   <span data-ttu-id="9c23c-132">Jak zmiana wpływa na klientów oraz czy wszystkie obejścia są dostępne w celu zachowania zgodności między wersjami.</span><span class="sxs-lookup"><span data-stu-id="9c23c-132">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

-   <span data-ttu-id="9c23c-133">Ocena jak ważna jest zmiana.</span><span class="sxs-lookup"><span data-stu-id="9c23c-133">An assessment of how important the change is.</span></span> <span data-ttu-id="9c23c-134">Problem ze zgodnością aplikacji są podzielone na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="9c23c-134">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="9c23c-135">Główne</span><span class="sxs-lookup"><span data-stu-id="9c23c-135">Major</span></span>|<span data-ttu-id="9c23c-136">Znaczące zmiany, która ma wpływ na wiele aplikacji lub wymaga znacznej modyfikacji kodu.</span><span class="sxs-lookup"><span data-stu-id="9c23c-136">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="9c23c-137">Pomocnicza</span><span class="sxs-lookup"><span data-stu-id="9c23c-137">Minor</span></span>|<span data-ttu-id="9c23c-138">Zmiana, który wpływa na małej liczby aplikacji lub wymagają drobne zmiany kodu.</span><span class="sxs-lookup"><span data-stu-id="9c23c-138">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="9c23c-139">Przypadek krawędzi</span><span class="sxs-lookup"><span data-stu-id="9c23c-139">Edge case</span></span>|<span data-ttu-id="9c23c-140">Zmiana wpływa na aplikacje w scenariuszach bardzo określone, rzadko.</span><span class="sxs-lookup"><span data-stu-id="9c23c-140">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="9c23c-141">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="9c23c-141">Transparent</span></span>|<span data-ttu-id="9c23c-142">Zmiana nie wpływa na deweloperem aplikacji lub użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9c23c-142">A change with no noticeable effect on the application's developer or user.</span></span>|

-   <span data-ttu-id="9c23c-143">Wersja wskazuje, kiedy zmiany najpierw zostanie wyświetlony w ramach.</span><span class="sxs-lookup"><span data-stu-id="9c23c-143">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="9c23c-144">Niektóre zmiany są wprowadzane w przypadku konkretnej wersji i przywrócone w nowszej wersji; który wskazane jest także.</span><span class="sxs-lookup"><span data-stu-id="9c23c-144">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

-   <span data-ttu-id="9c23c-145">Typ zmiany:</span><span class="sxs-lookup"><span data-stu-id="9c23c-145">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="9c23c-146">Przekierowania</span><span class="sxs-lookup"><span data-stu-id="9c23c-146">Retargeting</span></span>|<span data-ttu-id="9c23c-147">Zmiana wpływa na aplikacje, które są ponownie skompilowana do nowej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c23c-147">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="9c23c-148">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9c23c-148">Runtime</span></span>|<span data-ttu-id="9c23c-149">Zmiana wpływa na istniejących aplikacji, która jest przeznaczony dla poprzedniej wersji programu .NET Framework, ale działa w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="9c23c-149">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

-   <span data-ttu-id="9c23c-150">Dotyczy interfejsy API, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="9c23c-150">The affected APIS, if any.</span></span>

-   <span data-ttu-id="9c23c-151">Identyfikatory dostępne diagnostyki</span><span class="sxs-lookup"><span data-stu-id="9c23c-151">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="9c23c-152">Użycie</span><span class="sxs-lookup"><span data-stu-id="9c23c-152">Usage</span></span>
<span data-ttu-id="9c23c-153">Aby rozpocząć, wybierz typ zmiany zgodności poniżej:</span><span class="sxs-lookup"><span data-stu-id="9c23c-153">To begin, select the type of compatibility change below:</span></span>

* [<span data-ttu-id="9c23c-154">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="9c23c-154">Retargeting Changes</span></span>](./retargeting/index.md)
* [<span data-ttu-id="9c23c-155">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9c23c-155">Runtime Changes</span></span>](./runtime/index.md)


## <a name="see-also"></a><span data-ttu-id="9c23c-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c23c-156">See Also</span></span>

* [<span data-ttu-id="9c23c-157">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="9c23c-157">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [<span data-ttu-id="9c23c-158">Co nowego</span><span class="sxs-lookup"><span data-stu-id="9c23c-158">What's New</span></span>](../../../docs/framework/whats-new/index.md)
* [<span data-ttu-id="9c23c-159">Przestarzałe elementy w ułatwieniach dostępu</span><span class="sxs-lookup"><span data-stu-id="9c23c-159">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)
