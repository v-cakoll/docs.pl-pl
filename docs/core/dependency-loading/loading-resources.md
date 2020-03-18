---
title: Algorytm ładowania zestawu satelitarnego - .NET Core
description: Opis szczegółów algorytmu ładowania zestawu satelitarnego w .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70105315"
---
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="cc4ab-103">Algorytm ładowania zestawu satelitarnego</span><span class="sxs-lookup"><span data-stu-id="cc4ab-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="cc4ab-104">Zestawy satelickie są używane do przechowywania zlokalizowanych zasobów dostosowanych do języka i kultury.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="cc4ab-105">Zestawy satelickie używają innego algorytmu ładowania niż ogólne zestawy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="cc4ab-106">Kiedy są ładowane zespoły satelickie?</span><span class="sxs-lookup"><span data-stu-id="cc4ab-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="cc4ab-107">Zestawy satelickie są ładowane podczas ładowania zlokalizowanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="cc4ab-108">Podstawowy interfejs API do ładowania <xref:System.Resources.ResourceManager?displayProperty=fullName> zlokalizowanych zasobów jest klasą.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="cc4ab-109">Ostatecznie <xref:System.Resources.ResourceManager> klasa wywoła <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> metodę dla <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>każdego .</span><span class="sxs-lookup"><span data-stu-id="cc4ab-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="cc4ab-110">Interfejsy API wyższego poziomu mogą abstrakcyjne interfejsu API niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="cc4ab-111">Algorytm</span><span class="sxs-lookup"><span data-stu-id="cc4ab-111">Algorithm</span></span>

<span data-ttu-id="cc4ab-112">Proces rezerwowy zasobu .NET Core obejmuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cc4ab-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="cc4ab-113">`active` <xref:System.Runtime.Loader.AssemblyLoadContext> Określ wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="cc4ab-114">We wszystkich przypadkach `active` wystąpienie jest zestawu wykonującego <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="cc4ab-115">Wystąpienie `active` próbuje załadować zestaw satelicki dla żądanej kultury w kolejności priorytetowej przez:</span><span class="sxs-lookup"><span data-stu-id="cc4ab-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="cc4ab-116">Sprawdzanie jego pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-116">Checking its cache.</span></span>
    - <span data-ttu-id="cc4ab-117">Sprawdzanie katalogu aktualnie wykonywanego zestawu dla podkatalogu <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> zgodnego `es-MX`z żądanym (na przykład).</span><span class="sxs-lookup"><span data-stu-id="cc4ab-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="cc4ab-118">Ta funkcja nie została zaimplementowana w .NET Core przed 3.0.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="cc4ab-119">W systemie Linux i macOS podkatalog jest rozróżniany i musi:</span><span class="sxs-lookup"><span data-stu-id="cc4ab-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        > - <span data-ttu-id="cc4ab-120">Dokładnie pasuje do przypadku.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-120">Exactly match case.</span></span>
        > - <span data-ttu-id="cc4ab-121">Bądź w małych liter.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-121">Be in lower case.</span></span>

    - <span data-ttu-id="cc4ab-122">Jeśli `active` jest <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> wystąpieniem, uruchamiając domyślną logikę [sondowania zestawu satelity (zasobu).](default-probing.md#satellite-resource-assembly-probing)</span><span class="sxs-lookup"><span data-stu-id="cc4ab-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="cc4ab-123">Wywołanie <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> funkcji.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="cc4ab-124">Podnoszenie <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="cc4ab-125">Podnoszenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="cc4ab-126">Jeśli zespół satelitarny jest załadowany:</span><span class="sxs-lookup"><span data-stu-id="cc4ab-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="cc4ab-127">Zdarzenie <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="cc4ab-128">Zestaw jest przeszukiwany w poszukiwaniu żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="cc4ab-129">Jeśli czas wykonywania znajdzie zasób w zestawie, używa go.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="cc4ab-130">Jeśli nie znajdzie zasobu, kontynuuje wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cc4ab-131">Aby znaleźć zasób w zestawie satelickim, czas <xref:System.Resources.ResourceManager> uruchomieniwy wyszukuje plik zasobu wymagany przez bieżącego <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>pliku .</span><span class="sxs-lookup"><span data-stu-id="cc4ab-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cc4ab-132">W pliku zasobu wyszukuje żądana nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="cc4ab-133">Jeśli którykolwiek z nich nie zostanie znaleziony, zasób jest traktowany jako nieznaleziony.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="cc4ab-134">W czasie wykonywania obok przeszukuje zestawy kultury nadrzędnej za pośrednictwem wielu potencjalnych poziomów, za każdym razem powtarzając kroki 2 & 3.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="cc4ab-135">Każda kultura ma tylko jeden element nadrzędny, który jest zdefiniowany przez <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> właściwość.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="cc4ab-136">Wyszukiwanie kultur nadrzędnych zatrzymuje się, <xref:System.Globalization.CultureInfo.Parent%2A> gdy <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>właściwość kultury jest .</span><span class="sxs-lookup"><span data-stu-id="cc4ab-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="cc4ab-137">Dla <xref:System.Globalization.CultureInfo.InvariantCulture>, nie wracamy do kroków 2 & 3, ale raczej kontynuować krok 5.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="cc4ab-138">Jeśli zasób nadal nie zostanie znaleziony, używany jest zasób dla domyślnej (rezerwowej) kultury.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="cc4ab-139">Zazwyczaj zasoby dla kultury domyślnej są uwzględniane w głównym zestawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="cc4ab-140">Można jednak określić <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> dla <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="cc4ab-141">Ta wartość wskazuje, że ostateczna lokalizacja rezerwowa dla zasobów jest zestawem satelickim, a nie głównym.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cc4ab-142">Domyślna kultura jest ostatecznym rezerwowym.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="cc4ab-143">W związku z tym zaleca się, aby zawsze uwzględnić wyczerpujący zestaw zasobów w domyślnym pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="cc4ab-144">Pomaga to zapobiec zgłaszaniu wyjątków.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="cc4ab-145">Mając wyczerpujący zestaw, należy podać rezerwowy dla wszystkich zasobów i upewnij się, że co najmniej jeden zasób jest zawsze obecny dla użytkownika, nawet jeśli nie jest specyficzne dla kultury.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="cc4ab-146">Wreszcie</span><span class="sxs-lookup"><span data-stu-id="cc4ab-146">Finally,</span></span>
   - <span data-ttu-id="cc4ab-147">Jeśli czas wykonywania nie znajdzie pliku zasobów dla domyślnej (rezerwowej) kultury, zgłaszany jest wyjątek <xref:System.Resources.MissingManifestResourceException> lub <xref:System.Resources.MissingSatelliteAssemblyException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="cc4ab-148">Jeśli plik zasobu zostanie znaleziony, ale żądany zasób nie jest obecny, żądanie zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="cc4ab-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>
