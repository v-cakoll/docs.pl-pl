---
title: Zmiany w czasie wykonywania i retargetingu — .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196699"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="e46a7-102">Zgodność aplikacji w ramach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e46a7-102">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="e46a7-103">Zgodność jest ważnym celem każdej wersji .NET.</span><span class="sxs-lookup"><span data-stu-id="e46a7-103">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="e46a7-104">Zgodność zapewnia, że każda wersja jest dodatek, więc poprzednie wersje będą nadal działać.</span><span class="sxs-lookup"><span data-stu-id="e46a7-104">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="e46a7-105">Z drugiej strony zmiany w poprzedniej funkcjonalności (na przykład w celu zwiększenia wydajności, rozwiązania problemów z zabezpieczeniami lub naprawienia błędów) mogą powodować problemy ze zgodnością w istniejącym kodzie lub istniejących aplikacjach uruchamianych w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="e46a7-105">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="e46a7-106">Każda aplikacja jest przeznaczona dla określonej wersji programu .NET Framework według:</span><span class="sxs-lookup"><span data-stu-id="e46a7-106">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="e46a7-107">Definiowanie struktury docelowej w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e46a7-107">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="e46a7-108">Określanie struktury docelowej w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e46a7-108">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="e46a7-109">Stosowanie a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e46a7-109">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="e46a7-110">Podczas migracji z jednej wersji programu .NET Framework do innej istnieją dwa typy zmian, które należy wziąć pod uwagę:</span><span class="sxs-lookup"><span data-stu-id="e46a7-110">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="e46a7-111">Zmiany w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="e46a7-111">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="e46a7-112">Zmiana celu</span><span class="sxs-lookup"><span data-stu-id="e46a7-112">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="e46a7-113">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e46a7-113">Runtime changes</span></span>

<span data-ttu-id="e46a7-114">Problemy ze środowiska wykonawczego są te, które pojawiają się, gdy nowy środowisko uruchomieniowe jest umieszczany na komputerze i zmiany zachowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e46a7-114">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="e46a7-115">Podczas uruchamiania w nowszej wersji niż to, co było ukierunkowane, .NET Framework używa *dziwaczne* zachowanie naśladować starszą wersję docelową.</span><span class="sxs-lookup"><span data-stu-id="e46a7-115">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="e46a7-116">Aplikacja działa w nowszej wersji, ale działa tak, jakby była uruchomiona w starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="e46a7-116">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="e46a7-117">Wiele problemów ze zgodnością między wersjami programu .NET Framework są złagodzone za pośrednictwem tego modelu dziwactwa.</span><span class="sxs-lookup"><span data-stu-id="e46a7-117">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="e46a7-118">Na przykład jeśli plik binarny został skompilowany dla programu .NET Framework 4.0, ale działa na komputerze z programem .NET Framework 4.5 lub nowszym, działa w trybie zgodności programu .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="e46a7-118">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="e46a7-119">Oznacza to, że wiele zmian w nowszej wersji nie wpływa na binarne.</span><span class="sxs-lookup"><span data-stu-id="e46a7-119">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="e46a7-120">Wersja programu .NET Framework, która jest przeznaczona dla aplikacji, jest określana przez docelową wersję zestawu wpisu dla domeny aplikacji, w których uruchamia się kod.</span><span class="sxs-lookup"><span data-stu-id="e46a7-120">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="e46a7-121">Wszystkie dodatkowe zestawy załadowane w tej domenie aplikacji docelowej tej wersji.</span><span class="sxs-lookup"><span data-stu-id="e46a7-121">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="e46a7-122">Na przykład w przypadku pliku wykonywalnego wersja, w którą obiekty docelowe wykonywalne jest trybem zgodności, w których działają wszystkie zestawy w tej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e46a7-122">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="e46a7-123">Aby wyświetlić listę zmian w środowisku uruchomieniowym, które mają zastosowanie do twojego środowiska, wybierz aktualnie kierowaną wersję programu .NET Framework, a następnie wersję, do której chcesz przeprowadzić migrację:</span><span class="sxs-lookup"><span data-stu-id="e46a7-123">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="e46a7-124">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="e46a7-124">Retargeting changes</span></span>

<span data-ttu-id="e46a7-125">Zmiany retargetingu są te, które powstają, gdy zestaw jest ponownie skompilowany do docelowej nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="e46a7-125">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="e46a7-126">Kierowanie na nowszą wersję oznacza, że zestaw wybiera nowe funkcje, a także potencjalne problemy ze zgodnością starych funkcji.</span><span class="sxs-lookup"><span data-stu-id="e46a7-126">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="e46a7-127">Aby wyświetlić listę zmian retargetingu, które mają zastosowanie do twojego środowiska, wybierz wersję programu .NET Framework, na którą aktualnie kierujesz reklamy, a następnie wersję, do której chcesz przeprowadzić migrację:</span><span class="sxs-lookup"><span data-stu-id="e46a7-127">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="e46a7-128">Klasyfikacja wpływu</span><span class="sxs-lookup"><span data-stu-id="e46a7-128">Impact classification</span></span>

<span data-ttu-id="e46a7-129">W tematach opisujących zmiany środowiska uruchomieniowego i retargetingu, na przykład [zmiany retargetingu w celu migracji z 4.7.2 do 4.8,](retargeting/4.7.2-4.8.md)poszczególne elementy są klasyfikowane według ich oczekiwanego wpływu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e46a7-129">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="e46a7-130">**Głównych**</span><span class="sxs-lookup"><span data-stu-id="e46a7-130">**Major**</span></span>\
<span data-ttu-id="e46a7-131">Istotna zmiana, która wpływa na dużą liczbę aplikacji lub która wymaga znacznej modyfikacji kodu.</span><span class="sxs-lookup"><span data-stu-id="e46a7-131">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="e46a7-132">**Drobne**</span><span class="sxs-lookup"><span data-stu-id="e46a7-132">**Minor**</span></span>\
<span data-ttu-id="e46a7-133">Zmiana, która wpływa na niewielką liczbę aplikacji lub która wymaga niewielkiej modyfikacji kodu.</span><span class="sxs-lookup"><span data-stu-id="e46a7-133">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="e46a7-134">**Obudowa krawędzi**</span><span class="sxs-lookup"><span data-stu-id="e46a7-134">**Edge case**</span></span>\
<span data-ttu-id="e46a7-135">Zmiana, która wpływa na aplikacje w bardzo konkretnych scenariuszach, które nie są powszechne.</span><span class="sxs-lookup"><span data-stu-id="e46a7-135">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="e46a7-136">**Przezroczyste**</span><span class="sxs-lookup"><span data-stu-id="e46a7-136">**Transparent**</span></span>\
<span data-ttu-id="e46a7-137">Zmiana, która nie ma zauważalnego wpływu na dewelopera lub użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e46a7-137">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="e46a7-138">Aplikacja nie powinna wymagać modyfikacji z powodu tej zmiany.</span><span class="sxs-lookup"><span data-stu-id="e46a7-138">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="e46a7-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e46a7-139">See also</span></span>

- [<span data-ttu-id="e46a7-140">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="e46a7-140">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="e46a7-141">Co nowego</span><span class="sxs-lookup"><span data-stu-id="e46a7-141">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="e46a7-142">Co jest przestarzałe</span><span class="sxs-lookup"><span data-stu-id="e46a7-142">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
