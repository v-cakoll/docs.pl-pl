---
title: Zmiany środowiska uruchomieniowego i przekierowania — .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196699"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="5245b-102">Zgodność aplikacji w .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5245b-102">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="5245b-103">Zgodność jest ważnym celem każdej wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="5245b-103">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="5245b-104">Zgodność gwarantuje, że każda wersja jest dodatkiem, dlatego poprzednie wersje będą nadal działały.</span><span class="sxs-lookup"><span data-stu-id="5245b-104">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="5245b-105">Z drugiej strony zmiany poprzedniej funkcjonalności (na przykład w celu zwiększenia wydajności, rozwiązywania problemów z zabezpieczeniami lub rozwiązywania usterek) mogą spowodować problemy ze zgodnością w istniejącym kodzie lub istniejące aplikacje, które działają w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="5245b-105">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="5245b-106">Każda aplikacja odwołuje się do określonej wersji .NET Framework przez:</span><span class="sxs-lookup"><span data-stu-id="5245b-106">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="5245b-107">Definiowanie platformy docelowej w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5245b-107">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="5245b-108">Określanie platformy docelowej w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="5245b-108">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="5245b-109">Zastosowanie <xref:System.Runtime.Versioning.TargetFrameworkAttribute> do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5245b-109">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="5245b-110">W przypadku migrowania z jednej wersji .NET Framework do innej, istnieją dwa typy zmian do uwzględnienia:</span><span class="sxs-lookup"><span data-stu-id="5245b-110">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="5245b-111">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5245b-111">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="5245b-112">Przekierowywanie zmian</span><span class="sxs-lookup"><span data-stu-id="5245b-112">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="5245b-113">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5245b-113">Runtime changes</span></span>

<span data-ttu-id="5245b-114">Problemy dotyczące środowiska uruchomieniowego to te, które powstają, gdy nowe środowisko uruchomieniowe jest umieszczane na komputerze i zmiany zachowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5245b-114">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="5245b-115">W przypadku uruchamiania w nowszej wersji niż domowa, .NET Framework używa zachowania *quirked* do naśladowania starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="5245b-115">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="5245b-116">Aplikacja działa w nowszej wersji, ale działa tak, jakby była uruchomiona w starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="5245b-116">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="5245b-117">Wiele problemów ze zgodnością między wersjami .NET Framework jest korygowanych przez ten model quirking.</span><span class="sxs-lookup"><span data-stu-id="5245b-117">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="5245b-118">Na przykład, jeśli plik binarny został skompilowany dla .NET Framework 4,0, ale jest uruchamiany na komputerze z .NET Framework 4,5 lub nowszym, działa on w .NET Framework 4,0 tryb zgodności.</span><span class="sxs-lookup"><span data-stu-id="5245b-118">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="5245b-119">Oznacza to, że wiele zmian w nowszej wersji nie ma wpływu na dane binarne.</span><span class="sxs-lookup"><span data-stu-id="5245b-119">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="5245b-120">Wersja .NET Framework, do której odwołuje się aplikacja, jest określana przez docelową wersję zestawu wejścia dla domeny aplikacji, w której działa kod.</span><span class="sxs-lookup"><span data-stu-id="5245b-120">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="5245b-121">Wszystkie dodatkowe zestawy ładowane w tej domenie aplikacji są przeznaczone dla tej wersji.</span><span class="sxs-lookup"><span data-stu-id="5245b-121">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="5245b-122">Na przykład, w przypadku pliku wykonywalnego, wersja, do której należy wykonywalny, jest tryb zgodności wszystkie zestawy w tej domenie aplikacji działają w ramach programu.</span><span class="sxs-lookup"><span data-stu-id="5245b-122">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="5245b-123">Aby wyświetlić listę zmian w czasie wykonywania, które są stosowane w danym środowisku, wybierz aktualnie docelową wersję .NET Framework, a następnie wersję, do której chcesz przeprowadzić migrację:</span><span class="sxs-lookup"><span data-stu-id="5245b-123">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="5245b-124">Przekierowywanie zmian</span><span class="sxs-lookup"><span data-stu-id="5245b-124">Retargeting changes</span></span>

<span data-ttu-id="5245b-125">Zmiany przekierowania są tymi, które powstają, gdy zestaw jest ponownie kompilowany w celu przekierowania do nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="5245b-125">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="5245b-126">Przeznaczenie do nowszej wersji oznacza, że zestaw jest zachodzi na nowe funkcje, a także potencjalne problemy ze zgodnością dla starych funkcji.</span><span class="sxs-lookup"><span data-stu-id="5245b-126">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="5245b-127">Aby wyświetlić listę zmian docelowych, które są stosowane do danego środowiska, wybierz aktualnie używaną wersję .NET Framework, a następnie wersję, do której chcesz przeprowadzić migrację:</span><span class="sxs-lookup"><span data-stu-id="5245b-127">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="5245b-128">Klasyfikacja wpływu</span><span class="sxs-lookup"><span data-stu-id="5245b-128">Impact classification</span></span>

<span data-ttu-id="5245b-129">W temacie opisującym środowisko uruchomieniowe i przekierowywanie zmian, na przykład [zmiany ukierunkowania migracji z 4.7.2 do 4,8](retargeting/4.7.2-4.8.md), poszczególne elementy są klasyfikowane według ich oczekiwanego wpływu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5245b-129">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="5245b-130">\ **Główne**</span><span class="sxs-lookup"><span data-stu-id="5245b-130">**Major**\</span></span>
<span data-ttu-id="5245b-131">Znacząca zmiana wpływająca na dużą liczbę aplikacji lub wymagająca istotnej modyfikacji kodu.</span><span class="sxs-lookup"><span data-stu-id="5245b-131">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="5245b-132">\ **pomocnicze**</span><span class="sxs-lookup"><span data-stu-id="5245b-132">**Minor**\</span></span>
<span data-ttu-id="5245b-133">Zmiana wpływająca na niewielką liczbę aplikacji lub wymagająca drobnej modyfikacji kodu.</span><span class="sxs-lookup"><span data-stu-id="5245b-133">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="5245b-134">\ **przypadku krawędzi**</span><span class="sxs-lookup"><span data-stu-id="5245b-134">**Edge case**\</span></span>
<span data-ttu-id="5245b-135">Zmiana wpływająca na aplikacje w ramach bardzo konkretnych scenariuszy, które nie są wspólne.</span><span class="sxs-lookup"><span data-stu-id="5245b-135">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="5245b-136">\ **przezroczyste**</span><span class="sxs-lookup"><span data-stu-id="5245b-136">**Transparent**\</span></span>
<span data-ttu-id="5245b-137">Zmiana, która nie ma zauważalnego wpływu na deweloperów lub użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5245b-137">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="5245b-138">Aplikacja nie powinna wymagać modyfikacji ze względu na tę zmianę.</span><span class="sxs-lookup"><span data-stu-id="5245b-138">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="5245b-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5245b-139">See also</span></span>

- [<span data-ttu-id="5245b-140">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="5245b-140">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="5245b-141">Co nowego</span><span class="sxs-lookup"><span data-stu-id="5245b-141">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="5245b-142">Co jest przestarzałe</span><span class="sxs-lookup"><span data-stu-id="5245b-142">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
