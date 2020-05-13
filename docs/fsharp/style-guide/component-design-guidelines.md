---
title: F# — wytyczne dotyczące projektowania składników
description: 'Zapoznaj się z wytycznymi dotyczącymi pisania składników języka F # przeznaczonych do użycia przez innych wywołujących.'
ms.date: 05/14/2018
ms.openlocfilehash: 590bda0660d54ea73c590d31e694f3d499e0fd9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209139"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="e04e3-103">F# — wytyczne dotyczące projektowania składników</span><span class="sxs-lookup"><span data-stu-id="e04e3-103">F# component design guidelines</span></span>

<span data-ttu-id="e04e3-104">Ten dokument stanowi zestaw wytycznych dotyczących projektowania składników języka F # opartych na wytycznych dotyczących projektowania składnika F #, wersja 14, Microsoft Research i wersji, która była pierwotnie nadzorowana i obsługiwana przez program F # Software Foundation.</span><span class="sxs-lookup"><span data-stu-id="e04e3-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and a version that was originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="e04e3-105">W tym dokumencie założono, że znasz programowanie w języku F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="e04e3-106">Wiele poprowadzi Cię przez społeczność F # do swoich potrzeb i pomocnych informacji o różnych wersjach tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="e04e3-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="e04e3-107">Omówienie</span><span class="sxs-lookup"><span data-stu-id="e04e3-107">Overview</span></span>

<span data-ttu-id="e04e3-108">W tym dokumencie przedstawiono niektóre problemy związane z projektowaniem i kodowaniem składników w języku F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="e04e3-109">Składnik może oznaczać jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="e04e3-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="e04e3-110">Warstwa w projekcie języka F #, która ma zewnętrznych odbiorców w tym projekcie.</span><span class="sxs-lookup"><span data-stu-id="e04e3-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="e04e3-111">Biblioteka przeznaczona do użycia przez kod F # między granicami zestawu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="e04e3-112">Biblioteka przeznaczona do użycia przez dowolny język .NET między granicami zestawu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="e04e3-113">Biblioteka przeznaczona do dystrybucji za pośrednictwem repozytorium pakietów, takich jak [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="e04e3-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="e04e3-114">Techniki opisane w tym artykule mają zastosowanie do [pięciu zasad dobrego kodu języka F #](index.md#five-principles-of-good-f-code)i w ten sposób wykorzystują zarówno programowanie funkcjonalne, jak i obiektów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="e04e3-115">Bez względu na metodologię, składnik i Projektant biblioteki mogą napotkać wiele praktycznych i prosaicych problemów podczas tworzenia interfejsu API, który jest najłatwiej do użycia przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="e04e3-116">Conscientious z zastosowaniem [wytycznych dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md) będzie można utworzyć spójny zestaw interfejsów API, które są przyjemne do użycia.</span><span class="sxs-lookup"><span data-stu-id="e04e3-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="e04e3-117">Ogólne wskazówki</span><span class="sxs-lookup"><span data-stu-id="e04e3-117">General guidelines</span></span>

<span data-ttu-id="e04e3-118">Istnieje kilka uniwersalnych wytycznych dotyczących bibliotek języka F #, niezależnie od zamierzonych odbiorców biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e04e3-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="e04e3-119">Poznaj wskazówki dotyczące projektowania biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="e04e3-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="e04e3-120">Bez względu na rodzaj kodowania języka F # jest to cenna znajomość [wytycznych dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="e04e3-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="e04e3-121">Większość innych programistów F # i .NET zna te wytyczne i oczekuje, że kod .NET będzie zgodny z nimi.</span><span class="sxs-lookup"><span data-stu-id="e04e3-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="e04e3-122">Wskazówki dotyczące projektowania biblioteki .NET zapewniają ogólne wskazówki dotyczące nazewnictwa, projektowania klas i interfejsów, projektowania elementów członkowskich (właściwości, metod, zdarzeń itp.) i innych, a które są użytecznym pierwszym punktem odniesienia dla różnych wytycznych projektowych.</span><span class="sxs-lookup"><span data-stu-id="e04e3-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="e04e3-123">Dodawanie komentarzy do dokumentacji XML do kodu</span><span class="sxs-lookup"><span data-stu-id="e04e3-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="e04e3-124">Dokumentacja XML w publicznych interfejsach API zapewnia, że użytkownicy mogą uzyskać wspaniałe funkcje IntelliSense i sekcji szybkich informacji podczas korzystania z tych typów i członków, a także włączyć tworzenie plików dokumentacji dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e04e3-124">XML documentation on public APIs ensures that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="e04e3-125">Zapoznaj się z [dokumentacją XML](../language-reference/xml-documentation.md) dotyczącą różnych tagów XML, które mogą być używane do dodatkowego adiustacji w komentarzach XMLDOC.</span><span class="sxs-lookup"><span data-stu-id="e04e3-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="e04e3-126">Możesz użyć krótkich komentarzy XML ( `/// comment` ) lub standardowych komentarzy XML ( `///<summary>comment</summary>` ).</span><span class="sxs-lookup"><span data-stu-id="e04e3-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="e04e3-127">Rozważ użycie jawnych plików sygnatur (. FSI) dla stabilnych interfejsów API biblioteki i składników</span><span class="sxs-lookup"><span data-stu-id="e04e3-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="e04e3-128">Używanie jawnych plików sygnatur w bibliotece języka F # zawiera zwięzłe podsumowanie publicznego interfejsu API, co pomaga zapewnić pełną publiczną powierzchnię biblioteki i zapewnia czyste rozdzielenie między dokumentacją publiczną i wewnętrznymi szczegółami implementacji.</span><span class="sxs-lookup"><span data-stu-id="e04e3-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which helps to ensure that you know the full public surface of your library, and provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="e04e3-129">Pliki sygnatur dodają tarcie do zmiany publicznego interfejsu API, co wymaga wprowadzenia zmian w plikach implementacji i sygnatur.</span><span class="sxs-lookup"><span data-stu-id="e04e3-129">Signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="e04e3-130">W związku z tym pliki sygnatur powinny być zwykle wprowadzane tylko wtedy, gdy interfejs API stał się solidified i nie jest już zmieniany znacząco.</span><span class="sxs-lookup"><span data-stu-id="e04e3-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="e04e3-131">Zawsze należy stosować najlepsze rozwiązania dotyczące używania ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="e04e3-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="e04e3-132">Postępuj zgodnie z [najlepszymi rozwiązaniami dotyczącymi używania ciągów w wskazówkach platformy .NET](../../standard/base-types/best-practices-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="e04e3-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="e04e3-133">W szczególności zawsze jawnie *zamiarem kultury* w konwersji i porównywania ciągów (jeśli ma to zastosowanie).</span><span class="sxs-lookup"><span data-stu-id="e04e3-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="e04e3-134">Wskazówki dotyczące bibliotek przeznaczonych dla języka F #</span><span class="sxs-lookup"><span data-stu-id="e04e3-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="e04e3-135">W tej sekcji przedstawiono zalecenia dotyczące projektowania publicznych bibliotek języka F #. oznacza to, że biblioteki uwidaczniające publiczne interfejsy API przeznaczone do użycia przez deweloperów języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="e04e3-136">Istnieją różne zalecenia dotyczące projektowania bibliotek mające zastosowanie w odróżnieniu od języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="e04e3-137">W przypadku braku konkretnych zaleceń, które obserwują, wskazówki dotyczące projektowania biblioteki .NET są wskazówkami powrotu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="e04e3-138">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="e04e3-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="e04e3-139">Korzystanie z nazw platformy .NET i Konwencji kapitalizacji</span><span class="sxs-lookup"><span data-stu-id="e04e3-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="e04e3-140">W poniższej tabeli przedstawiono konwencje nazewnictwa i Konwencji kapitalizacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="e04e3-141">Istnieją małe dodatki, które zawierają również konstrukcje języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="e04e3-142">Konstrukcja</span><span class="sxs-lookup"><span data-stu-id="e04e3-142">Construct</span></span> | <span data-ttu-id="e04e3-143">Sprawa</span><span class="sxs-lookup"><span data-stu-id="e04e3-143">Case</span></span> | <span data-ttu-id="e04e3-144">Część</span><span class="sxs-lookup"><span data-stu-id="e04e3-144">Part</span></span> | <span data-ttu-id="e04e3-145">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e04e3-145">Examples</span></span> | <span data-ttu-id="e04e3-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e04e3-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="e04e3-147">Typy konkretne</span><span class="sxs-lookup"><span data-stu-id="e04e3-147">Concrete types</span></span> | <span data-ttu-id="e04e3-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-148">PascalCase</span></span> | <span data-ttu-id="e04e3-149">Rzeczownik/przymiotnik</span><span class="sxs-lookup"><span data-stu-id="e04e3-149">Noun/ adjective</span></span> | <span data-ttu-id="e04e3-150">Lista, podwójna, złożona</span><span class="sxs-lookup"><span data-stu-id="e04e3-150">List, Double, Complex</span></span> | <span data-ttu-id="e04e3-151">Konkretne typy to struktury, klasy, wyliczenia, Delegaty, rekordy i złożenia.</span><span class="sxs-lookup"><span data-stu-id="e04e3-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="e04e3-152">Chociaż nazwy typów są tradycyjnie małe litery w OCaml, język F # przyjął schemat nazewnictwa platformy .NET dla typów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="e04e3-153">biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="e04e3-153">DLLs</span></span>           | <span data-ttu-id="e04e3-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-154">PascalCase</span></span> |                 | <span data-ttu-id="e04e3-155">Fabrikam. Core. dll</span><span class="sxs-lookup"><span data-stu-id="e04e3-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="e04e3-156">Złożenie tagów</span><span class="sxs-lookup"><span data-stu-id="e04e3-156">Union tags</span></span>     | <span data-ttu-id="e04e3-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-157">PascalCase</span></span> | <span data-ttu-id="e04e3-158">Rzeczownik</span><span class="sxs-lookup"><span data-stu-id="e04e3-158">Noun</span></span> | <span data-ttu-id="e04e3-159">Niektóre, Dodaj, sukces</span><span class="sxs-lookup"><span data-stu-id="e04e3-159">Some, Add, Success</span></span> | <span data-ttu-id="e04e3-160">Nie należy używać prefiksu w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="e04e3-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="e04e3-161">Opcjonalnie użyj prefiksu w przypadku wewnętrznego, takiego jak`type Teams = TAlpha | TBeta | TDelta.`</span><span class="sxs-lookup"><span data-stu-id="e04e3-161">Optionally use a prefix when internal, such as `type Teams = TAlpha | TBeta | TDelta.`</span></span> |
| <span data-ttu-id="e04e3-162">Wydarzenie</span><span class="sxs-lookup"><span data-stu-id="e04e3-162">Event</span></span>          | <span data-ttu-id="e04e3-163">PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-163">PascalCase</span></span> | <span data-ttu-id="e04e3-164">Czasownik</span><span class="sxs-lookup"><span data-stu-id="e04e3-164">Verb</span></span> | <span data-ttu-id="e04e3-165">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="e04e3-165">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="e04e3-166">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="e04e3-166">Exceptions</span></span>     | <span data-ttu-id="e04e3-167">PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-167">PascalCase</span></span> |      | <span data-ttu-id="e04e3-168">WebException</span><span class="sxs-lookup"><span data-stu-id="e04e3-168">WebException</span></span> | <span data-ttu-id="e04e3-169">Nazwa powinna kończyć się znakiem "Exception".</span><span class="sxs-lookup"><span data-stu-id="e04e3-169">Name should end with "Exception".</span></span> |
| <span data-ttu-id="e04e3-170">Pole</span><span class="sxs-lookup"><span data-stu-id="e04e3-170">Field</span></span>          | <span data-ttu-id="e04e3-171">PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-171">PascalCase</span></span> | <span data-ttu-id="e04e3-172">Rzeczownik</span><span class="sxs-lookup"><span data-stu-id="e04e3-172">Noun</span></span> | <span data-ttu-id="e04e3-173">Bieżącaname</span><span class="sxs-lookup"><span data-stu-id="e04e3-173">CurrentName</span></span>  | |
| <span data-ttu-id="e04e3-174">Typy interfejsów</span><span class="sxs-lookup"><span data-stu-id="e04e3-174">Interface types</span></span> |  <span data-ttu-id="e04e3-175">PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-175">PascalCase</span></span> | <span data-ttu-id="e04e3-176">Rzeczownik/przymiotnik</span><span class="sxs-lookup"><span data-stu-id="e04e3-176">Noun/ adjective</span></span> | <span data-ttu-id="e04e3-177">IDisposable</span><span class="sxs-lookup"><span data-stu-id="e04e3-177">IDisposable</span></span> | <span data-ttu-id="e04e3-178">Nazwa powinna zaczynać się od "I".</span><span class="sxs-lookup"><span data-stu-id="e04e3-178">Name should start with "I".</span></span> |
| <span data-ttu-id="e04e3-179">Metoda</span><span class="sxs-lookup"><span data-stu-id="e04e3-179">Method</span></span> |  <span data-ttu-id="e04e3-180">PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-180">PascalCase</span></span> |  <span data-ttu-id="e04e3-181">Czasownik</span><span class="sxs-lookup"><span data-stu-id="e04e3-181">Verb</span></span> | <span data-ttu-id="e04e3-182">ToString</span><span class="sxs-lookup"><span data-stu-id="e04e3-182">ToString</span></span> | |
| <span data-ttu-id="e04e3-183">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e04e3-183">Namespace</span></span> | <span data-ttu-id="e04e3-184">PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-184">PascalCase</span></span> | | <span data-ttu-id="e04e3-185">Microsoft. FSharp. Core</span><span class="sxs-lookup"><span data-stu-id="e04e3-185">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="e04e3-186">Zwykle używaj `<Organization>.<Technology>[.<Subnamespace>]` , chociaż Porzuć organizację, jeśli technologia jest niezależna od organizacji.</span><span class="sxs-lookup"><span data-stu-id="e04e3-186">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="e04e3-187">Parametry</span><span class="sxs-lookup"><span data-stu-id="e04e3-187">Parameters</span></span> | <span data-ttu-id="e04e3-188">camelCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-188">camelCase</span></span> | <span data-ttu-id="e04e3-189">Rzeczownik</span><span class="sxs-lookup"><span data-stu-id="e04e3-189">Noun</span></span> |  <span data-ttu-id="e04e3-190">typeName, Transform, Range</span><span class="sxs-lookup"><span data-stu-id="e04e3-190">typeName, transform, range</span></span> | |
| <span data-ttu-id="e04e3-191">Zezwalaj na wartości (wewnętrzne)</span><span class="sxs-lookup"><span data-stu-id="e04e3-191">let values (internal)</span></span> | <span data-ttu-id="e04e3-192">camelCase lub PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-192">camelCase or PascalCase</span></span> | <span data-ttu-id="e04e3-193">Rzeczownik/czasownik</span><span class="sxs-lookup"><span data-stu-id="e04e3-193">Noun/ verb</span></span> |  <span data-ttu-id="e04e3-194">GetValue, myTable</span><span class="sxs-lookup"><span data-stu-id="e04e3-194">getValue, myTable</span></span> |
| <span data-ttu-id="e04e3-195">Zezwalaj na wartości (zewnętrzne)</span><span class="sxs-lookup"><span data-stu-id="e04e3-195">let values (external)</span></span> | <span data-ttu-id="e04e3-196">camelCase lub PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-196">camelCase or PascalCase</span></span> | <span data-ttu-id="e04e3-197">Rzeczownik/czasownik</span><span class="sxs-lookup"><span data-stu-id="e04e3-197">Noun/verb</span></span>  | <span data-ttu-id="e04e3-198">List. map, daty. dzisiaj</span><span class="sxs-lookup"><span data-stu-id="e04e3-198">List.map, Dates.Today</span></span> | <span data-ttu-id="e04e3-199">wartości, które są powiązane, często są publiczne, gdy obowiązują tradycyjne funkcjonalne wzorce projektowe.</span><span class="sxs-lookup"><span data-stu-id="e04e3-199">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="e04e3-200">Jednak zazwyczaj należy używać PascalCase, gdy identyfikator może być używany z innych języków .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-200">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="e04e3-201">Właściwość</span><span class="sxs-lookup"><span data-stu-id="e04e3-201">Property</span></span>  | <span data-ttu-id="e04e3-202">PascalCase</span><span class="sxs-lookup"><span data-stu-id="e04e3-202">PascalCase</span></span>  | <span data-ttu-id="e04e3-203">Rzeczownik/przymiotnik</span><span class="sxs-lookup"><span data-stu-id="e04e3-203">Noun/ adjective</span></span>  | <span data-ttu-id="e04e3-204">IsEndOfFile, BackColor</span><span class="sxs-lookup"><span data-stu-id="e04e3-204">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="e04e3-205">Ogólnie używane właściwości logiczne to i mogą być pozytywne, podobnie jak w IsEndOfFile, a nie IsNotEndOfFile.</span><span class="sxs-lookup"><span data-stu-id="e04e3-205">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="e04e3-206">Unikaj skrótów</span><span class="sxs-lookup"><span data-stu-id="e04e3-206">Avoid abbreviations</span></span>

<span data-ttu-id="e04e3-207">Wskazówki dotyczące platformy .NET uniemożliwiają korzystanie z skrótów (na przykład "Użyj `OnButtonClick` zamiast `OnBtnClick` ").</span><span class="sxs-lookup"><span data-stu-id="e04e3-207">The .NET guidelines discourage the use of abbreviations (for example, "use `OnButtonClick` rather than `OnBtnClick`").</span></span> <span data-ttu-id="e04e3-208">Standardowe skróty, takie jak `Async` dla "asynchroniczne", są dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="e04e3-208">Common abbreviations, such as `Async` for "Asynchronous", are tolerated.</span></span> <span data-ttu-id="e04e3-209">Te wytyczne są czasami ignorowane w programowaniu funkcjonalnym; na przykład `List.iter` używa skrótu do iteracji.</span><span class="sxs-lookup"><span data-stu-id="e04e3-209">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for "iterate".</span></span> <span data-ttu-id="e04e3-210">Z tego powodu skróty do programowania w języku F #-do-F # mają być ograniczone, ale mimo to nadal powinny być stosowane w projekcie składnika publicznego.</span><span class="sxs-lookup"><span data-stu-id="e04e3-210">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="e04e3-211">Unikaj kolizji nazw</span><span class="sxs-lookup"><span data-stu-id="e04e3-211">Avoid casing name collisions</span></span>

<span data-ttu-id="e04e3-212">Wskazówki dotyczące platformy .NET mówią, że nie można użyć samej obudowy, aby odróżnić kolizje nazw, ponieważ niektóre języki klienta (na przykład Visual Basic) nie uwzględniają wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="e04e3-212">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="e04e3-213">Używaj akronimów, tam gdzie to konieczne</span><span class="sxs-lookup"><span data-stu-id="e04e3-213">Use acronyms where appropriate</span></span>

<span data-ttu-id="e04e3-214">Akronimy, takie jak XML, nie są skrótami i są szeroko stosowane w bibliotekach platformy .NET w postaci niewielkiej (XML).</span><span class="sxs-lookup"><span data-stu-id="e04e3-214">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="e04e3-215">Należy używać tylko dobrze znanych, powszechnie rozpoznanych akronimów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-215">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="e04e3-216">Użyj PascalCase dla ogólnych nazw parametrów</span><span class="sxs-lookup"><span data-stu-id="e04e3-216">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="e04e3-217">Użyj PascalCase dla ogólnych nazw parametrów w publicznych interfejsach API, w tym dla bibliotek przeznaczonych dla języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-217">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="e04e3-218">W szczególności należy używać nazw, takich jak,, `T` `U` `T1` , `T2` dla dowolnych parametrów ogólnych, a kiedy konkretne nazwy mają sens, a następnie dla bibliotek przeznaczonych dla języka F # używają nazw takich jak `Key` , `Value` , `Arg` (ale nie na przykład `TKey` ).</span><span class="sxs-lookup"><span data-stu-id="e04e3-218">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="e04e3-219">Użyj PascalCase lub camelCase do publicznych funkcji i wartości w modułach języka F #</span><span class="sxs-lookup"><span data-stu-id="e04e3-219">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="e04e3-220">camelCase jest używany do funkcji publicznych, które są przeznaczone do użycia niekwalifikowanych (na przykład `invalidArg` ) i dla "standardowych funkcji kolekcji" (na przykład list. map).</span><span class="sxs-lookup"><span data-stu-id="e04e3-220">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the "standard collection functions" (for example, List.map).</span></span> <span data-ttu-id="e04e3-221">W obu tych przypadkach nazwy funkcji działają podobnie jak słowa kluczowe w języku.</span><span class="sxs-lookup"><span data-stu-id="e04e3-221">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="e04e3-222">Obiekt, typ i projekt modułu</span><span class="sxs-lookup"><span data-stu-id="e04e3-222">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="e04e3-223">Używanie obszarów nazw lub modułów do przechowywania typów i modułów</span><span class="sxs-lookup"><span data-stu-id="e04e3-223">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="e04e3-224">Każdy plik F # w składniku powinien rozpoczynać się od deklaracji przestrzeni nazw lub deklaracji modułu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-224">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="e04e3-225">lub</span><span class="sxs-lookup"><span data-stu-id="e04e3-225">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="e04e3-226">Różnice między używaniem modułów i przestrzeni nazw do organizowania kodu na najwyższym poziomie są następujące:</span><span class="sxs-lookup"><span data-stu-id="e04e3-226">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="e04e3-227">Przestrzenie nazw mogą obejmować wiele plików</span><span class="sxs-lookup"><span data-stu-id="e04e3-227">Namespaces can span multiple files</span></span>
* <span data-ttu-id="e04e3-228">Przestrzenie nazw nie mogą zawierać funkcji języka F #, chyba że znajdują się w module wewnętrznym</span><span class="sxs-lookup"><span data-stu-id="e04e3-228">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="e04e3-229">Kod dla danego modułu musi być zawarty w pojedynczym pliku</span><span class="sxs-lookup"><span data-stu-id="e04e3-229">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="e04e3-230">Moduły najwyższego poziomu mogą zawierać funkcje języka F # bez potrzeby wewnętrznego modułu</span><span class="sxs-lookup"><span data-stu-id="e04e3-230">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="e04e3-231">Wybór między przestrzenią nazw najwyższego poziomu lub modułem ma wpływ na skompilowaną postać kodu i w efekcie będzie miał wpływ na widok z innych języków .NET, jeśli interfejs API zostanie ostatecznie użyty poza kodem F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-231">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="e04e3-232">Użyj metod i właściwości dla operacji wewnętrznych dla typów obiektów</span><span class="sxs-lookup"><span data-stu-id="e04e3-232">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="e04e3-233">Podczas pracy z obiektami najlepiej jest upewnić się, że funkcje możliwe do użycia są implementowane jako metody i właściwości tego typu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-233">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="e04e3-234">Większość funkcjonalności dla danego elementu członkowskiego nie musi być koniecznie zaimplementowana w tym elemencie członkowskim, ale może to być użyteczna część tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e04e3-234">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="e04e3-235">Użyj klas do hermetyzacji stanu modyfikowalnego</span><span class="sxs-lookup"><span data-stu-id="e04e3-235">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="e04e3-236">W języku F #, należy to zrobić tylko wtedy, gdy ten stan nie jest już hermetyzowany przez inną konstrukcję języka, taką jak zamknięcie, wyrażenie sekwencji lub asynchroniczne obliczanie.</span><span class="sxs-lookup"><span data-stu-id="e04e3-236">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="e04e3-237">Używanie interfejsów do grupowania powiązanych operacji</span><span class="sxs-lookup"><span data-stu-id="e04e3-237">Use interfaces to group related operations</span></span>

<span data-ttu-id="e04e3-238">Użyj typów interfejsów do reprezentowania zestawu operacji.</span><span class="sxs-lookup"><span data-stu-id="e04e3-238">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="e04e3-239">Jest to preferowane w przypadku innych opcji, takich jak krotki funkcji lub rekordów funkcji.</span><span class="sxs-lookup"><span data-stu-id="e04e3-239">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="e04e3-240">W preferencjach:</span><span class="sxs-lookup"><span data-stu-id="e04e3-240">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="e04e3-241">Interfejsy są pojęciami pierwszej klasy w programie .NET, których można użyć do osiągnięcia tego, co funktory zwykle.</span><span class="sxs-lookup"><span data-stu-id="e04e3-241">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="e04e3-242">Ponadto mogą być używane do kodowania typów egzystencjalna w programie, które nie mogą być rejestrowane w programie.</span><span class="sxs-lookup"><span data-stu-id="e04e3-242">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a><span data-ttu-id="e04e3-243">Używanie modułu do grupowania funkcji, które działają na kolekcjach</span><span class="sxs-lookup"><span data-stu-id="e04e3-243">Use a module to group functions that act on collections</span></span>

<span data-ttu-id="e04e3-244">Podczas definiowania typu kolekcji należy rozważyć dostarczenie standardowego zestawu operacji takich jak `CollectionType.map` i `CollectionType.iter` ) dla nowych typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e04e3-244">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="e04e3-245">Jeśli dołączysz taki moduł, postępuj zgodnie ze standardowymi konwencjami nazewnictwa dla funkcji znalezionych w FSharp. Core.</span><span class="sxs-lookup"><span data-stu-id="e04e3-245">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="e04e3-246">Używanie modułu do grupowania funkcji dla wspólnych, kanonicznych funkcji, szczególnie w bibliotekach matematycznych i DSL</span><span class="sxs-lookup"><span data-stu-id="e04e3-246">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="e04e3-247">Na przykład `Microsoft.FSharp.Core.Operators` jest automatycznie otwierana kolekcja funkcji najwyższego poziomu (takich jak `abs` i `sin` ) dostarczonych przez FSharp. Core. dll.</span><span class="sxs-lookup"><span data-stu-id="e04e3-247">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="e04e3-248">Podobnie Biblioteka statystyk może zawierać moduł z funkcjami `erf` i `erfc` , w których ten moduł został zaprojektowany do jawnego lub automatycznego otwierania.</span><span class="sxs-lookup"><span data-stu-id="e04e3-248">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="e04e3-249">Rozważ użycie RequireQualifiedAccess i starannie Zastosuj atrybuty AutoOpen</span><span class="sxs-lookup"><span data-stu-id="e04e3-249">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="e04e3-250">Dodanie `[<RequireQualifiedAccess>]` atrybutu do modułu wskazuje, że moduł nie może być otwarty i że odwołania do elementów modułu wymagają jawnego kwalifikowanego dostępu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-250">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="e04e3-251">Na przykład `Microsoft.FSharp.Collections.List` moduł ma ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="e04e3-251">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="e04e3-252">Jest to przydatne, gdy funkcje i wartości w module mają nazwy, które mogą powodować konflikt z nazwami w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="e04e3-252">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="e04e3-253">Wymaganie dostępu kwalifikowanego może znacznie zwiększyć długoterminową konserwację i możliwość rozwijania biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e04e3-253">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="e04e3-254">Dodanie `[<AutoOpen>]` atrybutu do modułu oznacza, że moduł zostanie otwarty po otwarciu zawierającego ją przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e04e3-254">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="e04e3-255">Ten `[<AutoOpen>]` atrybut może być również stosowany do zestawu, aby wskazać moduł, który jest automatycznie otwierany, gdy następuje odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-255">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="e04e3-256">Na przykład biblioteka statystyk **MathsHeaven. statystyki** mogą zawierać `module MathsHeaven.Statistics.Operators` funkcje zawierające `erf` i `erfc` .</span><span class="sxs-lookup"><span data-stu-id="e04e3-256">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="e04e3-257">Należy oznaczyć ten moduł jako `[<AutoOpen>]` .</span><span class="sxs-lookup"><span data-stu-id="e04e3-257">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="e04e3-258">Oznacza to `open MathsHeaven.Statistics` również otwarcie tego modułu i przeniesienie nazw `erf` oraz `erfc` zakresu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-258">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="e04e3-259">Innym dobrym zastosowaniem `[<AutoOpen>]` jest dla modułów zawierających metody rozszerzające.</span><span class="sxs-lookup"><span data-stu-id="e04e3-259">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="e04e3-260">Nadmierne użycie `[<AutoOpen>]` potencjalnych klientów w zanieczyszczonych przestrzeniach nazw i atrybut powinien być używany z opieką.</span><span class="sxs-lookup"><span data-stu-id="e04e3-260">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="e04e3-261">W przypadku określonych bibliotek w określonych domenach rozsądne użycie `[<AutoOpen>]` może prowadzić do lepszej użyteczności.</span><span class="sxs-lookup"><span data-stu-id="e04e3-261">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="e04e3-262">Należy rozważyć Definiowanie elementów członkowskich operatora w klasach, w których używane są dobrze znane operatory</span><span class="sxs-lookup"><span data-stu-id="e04e3-262">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="e04e3-263">Czasami klasy są używane do modelowania konstrukcji matematycznych, takich jak Vectors.</span><span class="sxs-lookup"><span data-stu-id="e04e3-263">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="e04e3-264">W przypadku modelowania domeny ma dobrze znane operatory, Definiowanie ich jako elementów członkowskich wewnętrznych dla klasy jest pomocne.</span><span class="sxs-lookup"><span data-stu-id="e04e3-264">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="e04e3-265">Te wskazówki odnoszą się do ogólnych wskazówek dotyczących platformy .NET dla tych typów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-265">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="e04e3-266">Jednak może być dodatkowo ważne w języku F #, ponieważ pozwala to na używanie tych typów w połączeniu z funkcjami i metodami języka F # z ograniczeniami elementu członkowskiego, takimi jak list. sumBy —.</span><span class="sxs-lookup"><span data-stu-id="e04e3-266">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="e04e3-267">Rozważ użycie Skompilowanname, aby podać. Przyjazna dla sieci nazwa dla innych użytkowników języka .NET</span><span class="sxs-lookup"><span data-stu-id="e04e3-267">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="e04e3-268">Czasami warto nazwać coś w jednym stylu dla odbiorców F # (takich jak statyczna składowa w małych przypadkach, tak jakby była funkcją powiązaną z modułem), ale mieć inny styl dla nazwy, gdy jest kompilowany do zestawu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-268">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="e04e3-269">Możesz użyć atrybutu, `[<CompiledName>]` Aby podać inny styl dla kodu języka F #, który korzysta z zestawu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-269">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="e04e3-270">Korzystając z programu `[<CompiledName>]` , można używać konwencji nazewnictwa platformy .NET dla odbiorców nie należących do zestawu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-270">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="e04e3-271">Użycie przeciążania metod dla funkcji Członkowskich, jeśli tak, zapewnia łatwiejszy interfejs API</span><span class="sxs-lookup"><span data-stu-id="e04e3-271">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="e04e3-272">Przeciążanie metod jest zaawansowanym narzędziem do uproszczenia interfejsu API, który może wymagać wykonania podobnej funkcjonalności, ale z różnymi opcjami lub argumentami.</span><span class="sxs-lookup"><span data-stu-id="e04e3-272">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="e04e3-273">W języku F # jest to bardziej powszechne, aby przeciążać liczbę argumentów zamiast typów argumentów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-273">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="e04e3-274">Ukryj reprezentacje typów rekordów i Unii, jeśli projekt tych typów prawdopodobnie zostanie rozbudowany</span><span class="sxs-lookup"><span data-stu-id="e04e3-274">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="e04e3-275">Unikaj ujawniania konkretnych reprezentacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-275">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="e04e3-276">Na przykład konkretna reprezentacja <xref:System.DateTime> wartości nie jest ujawniana przez zewnętrzny, publiczny interfejs API projektu biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-276">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="e04e3-277">W czasie wykonywania środowisko uruchomieniowe języka wspólnego zna zatwierdzoną implementację, która będzie używana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e04e3-277">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="e04e3-278">Jednak skompilowany kod nie sam wybiera zależności w konkretną reprezentację.</span><span class="sxs-lookup"><span data-stu-id="e04e3-278">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="e04e3-279">Unikaj stosowania dziedziczenia implementacji dla rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="e04e3-279">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="e04e3-280">W języku F #, dziedziczenie implementacji jest rzadko używane.</span><span class="sxs-lookup"><span data-stu-id="e04e3-280">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="e04e3-281">Ponadto hierarchie dziedziczenia są często skomplikowane i trudne do zmiany po nadejściu nowych wymagań.</span><span class="sxs-lookup"><span data-stu-id="e04e3-281">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="e04e3-282">Implementacja dziedziczenia nadal istnieje w języku F # w celu zapewnienia zgodności i rzadkich przypadków, gdy jest to najlepsze rozwiązanie problemu, ale w programach F # należy odszukać alternatywne techniki w przypadku projektowania pod kątem polimorfizmu, takiego jak implementacja interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-282">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="e04e3-283">Sygnatury funkcji i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="e04e3-283">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="e04e3-284">Użyj krotek dla zwracanych wartości podczas zwracania niewielkiej liczby niepowiązanych wartości</span><span class="sxs-lookup"><span data-stu-id="e04e3-284">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="e04e3-285">Oto dobry przykład użycia krotki w zwracanym typie:</span><span class="sxs-lookup"><span data-stu-id="e04e3-285">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="e04e3-286">Dla zwracanych typów zawierających wiele składników lub, gdy składniki są powiązane z pojedynczą identyfikowaną jednostką, należy rozważyć użycie nazwanego typu zamiast spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e04e3-286">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="e04e3-287">Używanie `Async<T>` do programowania asynchronicznego w granicach interfejsu API języka F #</span><span class="sxs-lookup"><span data-stu-id="e04e3-287">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="e04e3-288">Jeśli istnieje odpowiadająca operacja synchroniczna o nazwie, `Operation` która zwraca obiekt `T` , operacja asynchroniczna powinna mieć nazwę, `AsyncOperation` jeśli zwraca `Async<T>` lub `OperationAsync` zwraca `Task<T>` .</span><span class="sxs-lookup"><span data-stu-id="e04e3-288">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="e04e3-289">W przypadku często używanych typów platformy .NET, które uwidaczniają metody Begin/End, należy rozważyć użycie `Async.FromBeginEnd` programu w celu zapisania metod rozszerzających jako elewacji, aby zapewnić asynchroniczny model programowania F # dla tych interfejsów API platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-289">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="e04e3-290">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="e04e3-290">Exceptions</span></span>

<span data-ttu-id="e04e3-291">Zobacz [zarządzanie błędami](conventions.md#error-management) , aby dowiedzieć się, jak korzystać z wyjątków, wyników i opcji.</span><span class="sxs-lookup"><span data-stu-id="e04e3-291">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="e04e3-292">Elementy członkowskie rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="e04e3-292">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="e04e3-293">Starannie stosuj elementy członkowskie rozszerzenia F # w składnikach języka F # do-F #</span><span class="sxs-lookup"><span data-stu-id="e04e3-293">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="e04e3-294">Elementy członkowskie rozszerzeń języka F # powinny być zwykle używane tylko w przypadku operacji, które są w zamknięciu operacji wewnętrznych skojarzonych z typem w większości trybów użytkowania.</span><span class="sxs-lookup"><span data-stu-id="e04e3-294">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="e04e3-295">Typowym zastosowaniem jest zapewnienie interfejsów API, które są bardziej idiomatyczne do F # dla różnych typów .NET:</span><span class="sxs-lookup"><span data-stu-id="e04e3-295">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="e04e3-296">Typy Unii</span><span class="sxs-lookup"><span data-stu-id="e04e3-296">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="e04e3-297">Używaj Unii rozłącznych zamiast hierarchii klas dla danych o strukturze drzewa</span><span class="sxs-lookup"><span data-stu-id="e04e3-297">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="e04e3-298">Struktury podobne do drzewa są zdefiniowane cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="e04e3-298">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="e04e3-299">Jest to niewygodna z dziedziczeniem, ale elegancki z związkami rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="e04e3-299">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="e04e3-300">Przedstawianie danych o podobnej do drzewa z związkami rozłącznych pozwala również uzyskać wyczerpujące korzyści ze dopasowania wzorców.</span><span class="sxs-lookup"><span data-stu-id="e04e3-300">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="e04e3-301">Użycie `[<RequireQualifiedAccess>]` na typach Unii, których nazwy przypadków nie są wystarczająco unikatowe</span><span class="sxs-lookup"><span data-stu-id="e04e3-301">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="e04e3-302">Możesz się odszukać w domenie, w której ta sama nazwa jest najlepszą nazwą dla różnych rzeczy, takich jak przypadki Unii rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="e04e3-302">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="e04e3-303">Można użyć `[<RequireQualifiedAccess>]` , aby rozróżnić nazwy przypadków, aby uniknąć wyzwalania błędów spowodowanych przez zapełnienie w zależności od kolejności `open` instrukcji</span><span class="sxs-lookup"><span data-stu-id="e04e3-303">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="e04e3-304">Ukryj reprezentacje związków rozłącznych dla zgodnych z binarnych interfejsów API, jeśli projekt tych typów prawdopodobnie zostanie rozbudowany</span><span class="sxs-lookup"><span data-stu-id="e04e3-304">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="e04e3-305">Typy Unii polegają na formularzach dopasowania wzorców języka F #, aby uzyskać zwięzły model programowania.</span><span class="sxs-lookup"><span data-stu-id="e04e3-305">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="e04e3-306">Jak wspomniano wcześniej, należy unikać ujawniania konkretnych reprezentacji danych, jeśli projekt tych typów prawdopodobnie zostanie rozbudowany.</span><span class="sxs-lookup"><span data-stu-id="e04e3-306">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="e04e3-307">Na przykład reprezentacja związku rozłącznych może być ukryta przy użyciu prywatnej lub wewnętrznej deklaracji lub przy użyciu pliku sygnatury.</span><span class="sxs-lookup"><span data-stu-id="e04e3-307">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="e04e3-308">Jeśli ujawniane są odróżnienia związków rozłącznych, może się okazać, że trudno jest wersja biblioteki bez przerywania kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e04e3-308">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="e04e3-309">Zamiast tego należy rozważyć ujawnienie jednego lub kilku aktywnych wzorców, aby umożliwić Dopasowywanie wzorców do wartości typu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-309">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="e04e3-310">Aktywne wzorce oferują alternatywny sposób udostępniania konsumentom F # z dopasowywaniem do wzorców, jednocześnie unikając bezpośredniego udostępniania typów Unii języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-310">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="e04e3-311">Funkcje wbudowane i ograniczenia elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="e04e3-311">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="e04e3-312">Definiowanie ogólnych algorytmów liczbowych przy użyciu funkcji wbudowanych z implikowanymi ograniczeniami składowych i statycznie rozwiązanymi typami ogólnymi</span><span class="sxs-lookup"><span data-stu-id="e04e3-312">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="e04e3-313">Ograniczenia arytmetyczne elementu członkowskiego i ograniczenia języka F # są standardowym programowaniem w języku F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-313">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="e04e3-314">Rozważmy na przykład następujący kod:</span><span class="sxs-lookup"><span data-stu-id="e04e3-314">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="e04e3-315">Typ tej funkcji jest następujący:</span><span class="sxs-lookup"><span data-stu-id="e04e3-315">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="e04e3-316">Jest to odpowiednia funkcja dla publicznego interfejsu API w bibliotece matematycznej.</span><span class="sxs-lookup"><span data-stu-id="e04e3-316">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="e04e3-317">Unikaj używania ograniczeń składowych, aby symulować klasy typów i nazwy kaczki</span><span class="sxs-lookup"><span data-stu-id="e04e3-317">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="e04e3-318">Istnieje możliwość symulowania "kaczania tekstu" przy użyciu ograniczenia elementu członkowskiego F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-318">It is possible to simulate "duck typing" using F# member constraints.</span></span> <span data-ttu-id="e04e3-319">Jednakże elementy członkowskie, które korzystają z tego nie powinny być ogólnie używane w projektach bibliotek języka F #-to-F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-319">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="e04e3-320">Wynika to z faktu, że projekty biblioteki oparte na nieznanym lub niestandardowym ograniczeniu niejawnym powodują, że kod użytkownika staje się nieelastyczny i powiązany z jednym określonym wzorcem struktury.</span><span class="sxs-lookup"><span data-stu-id="e04e3-320">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="e04e3-321">Ponadto istnieje dobry szansa, że w ten sposób duże użycie ograniczeń składowych może skutkować bardzo długim czasem kompilowania.</span><span class="sxs-lookup"><span data-stu-id="e04e3-321">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="e04e3-322">Definicje operatorów</span><span class="sxs-lookup"><span data-stu-id="e04e3-322">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="e04e3-323">Unikaj definiowania niestandardowych operatorów symbolicznych</span><span class="sxs-lookup"><span data-stu-id="e04e3-323">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="e04e3-324">Operatory niestandardowe są niezbędne w niektórych sytuacjach i są wysoce przydatnymi urządzeniami do zapisu w dużej treści kodu implementacji.</span><span class="sxs-lookup"><span data-stu-id="e04e3-324">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="e04e3-325">W przypadku nowych użytkowników biblioteki nazwane funkcje są często łatwiejsze w użyciu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-325">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="e04e3-326">Ponadto niestandardowe operatory symboliczne mogą być trudne do udokumentowania, a użytkownicy są trudniejsze do wyszukania pomocy dotyczącej operatorów, ze względu na istniejące ograniczenia dotyczące środowiska IDE i aparatów wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="e04e3-326">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="e04e3-327">W związku z tym najlepszym rozwiązaniem jest opublikowanie funkcji jako nazwanych funkcji i członków, a dodatkowo uwidocznienie operatorów dla tej funkcji tylko wtedy, gdy korzyści z notacji są większe niż dokumentację i koszty poznawcze.</span><span class="sxs-lookup"><span data-stu-id="e04e3-327">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="e04e3-328">Jednostki miary</span><span class="sxs-lookup"><span data-stu-id="e04e3-328">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="e04e3-329">Starannie korzystaj z jednostek miary, aby zwiększyć bezpieczeństwo typu w kodzie języka F #</span><span class="sxs-lookup"><span data-stu-id="e04e3-329">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="e04e3-330">Dodatkowe informacje o wpisywaniu jednostek miary są wymazywane podczas wyświetlania przez inne języki .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-330">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="e04e3-331">Należy pamiętać, że składniki, narzędzia i odbicie w programie .NET zobaczą typy-San-Units.</span><span class="sxs-lookup"><span data-stu-id="e04e3-331">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="e04e3-332">Na przykład użytkownicy w języku C# będą widzieć `float` zamiast `float<kg>` .</span><span class="sxs-lookup"><span data-stu-id="e04e3-332">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="e04e3-333">Skróty typów</span><span class="sxs-lookup"><span data-stu-id="e04e3-333">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="e04e3-334">Starannie używaj skrótów typów do uproszczenia kodu F #</span><span class="sxs-lookup"><span data-stu-id="e04e3-334">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="e04e3-335">Składniki programu .NET, narzędzia i odbicie nie będą widziały skróconych nazw typów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-335">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="e04e3-336">Znaczące użycie skrótów typu może sprawiać, że domena jest bardziej złożona niż rzeczywiście, co może mylić konsumentów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-336">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="e04e3-337">Należy unikać skrótów typów dla publicznych typów, których elementy członkowskie i właściwości powinny być w sposób niezależny od tych, które są dostępne w skrócie typu</span><span class="sxs-lookup"><span data-stu-id="e04e3-337">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="e04e3-338">W takim przypadku skrócony typ ujawnia zbyt dużo informacji o reprezentowaniu określonego typu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-338">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="e04e3-339">Zamiast tego Rozważ zapakowanie skrótu w typie klasy lub Unii rozłącznej o pojedynczej wielkości liter (lub, jeśli wydajność jest istotna, rozważ użycie typu struktury do zawijania skrótu).</span><span class="sxs-lookup"><span data-stu-id="e04e3-339">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="e04e3-340">Na przykład jest to skłonność do definiowania wielomap jako specjalnego przypadku mapy języka F #, na przykład:</span><span class="sxs-lookup"><span data-stu-id="e04e3-340">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="e04e3-341">Jednak logiczne operacje notacji kropek na tym typie nie są takie same jak operacje na mapie — na przykład jest to uzasadnione, aby mapowanie operatora wyszukiwania było możliwe. [Key] Zwróć pustą listę, jeśli klucz nie znajduje się w słowniku, zamiast podnieść wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e04e3-341">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="e04e3-342">Wskazówki dotyczące bibliotek do użycia w innych językach .NET</span><span class="sxs-lookup"><span data-stu-id="e04e3-342">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="e04e3-343">Podczas projektowania bibliotek do użycia w innych językach .NET ważne jest, aby przestrzegać [wytycznych dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="e04e3-343">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="e04e3-344">W tym dokumencie te biblioteki są oznaczone jako biblioteka platformy .NET w formacie Wanili, w przeciwieństwie do bibliotek języka F #, które korzystają z konstrukcji F # bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="e04e3-344">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="e04e3-345">Projektowanie bibliotek programu .NET w postaci wanilii oznacza zapewnienie przyjaznych i idiomatyczne interfejsów API spójnych z pozostałą częścią .NET Framework przez zminimalizowanie użycia konstrukcji specyficznych dla języka F # w publicznym interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="e04e3-345">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="e04e3-346">Zasady są wyjaśnione w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="e04e3-346">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="e04e3-347">Przestrzeń nazw i projekt typu (dla bibliotek używanych w innych językach .NET)</span><span class="sxs-lookup"><span data-stu-id="e04e3-347">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="e04e3-348">Stosowanie konwencji nazewnictwa platformy .NET do publicznego interfejsu API składników</span><span class="sxs-lookup"><span data-stu-id="e04e3-348">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="e04e3-349">Należy zwrócić szczególną uwagę na używanie skróconych nazw oraz wytycznych dotyczących wielkości liter w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-349">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="e04e3-350">Używanie przestrzeni nazw, typów i elementów członkowskich jako podstawowej struktury organizacyjnej składników</span><span class="sxs-lookup"><span data-stu-id="e04e3-350">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="e04e3-351">Wszystkie pliki zawierające funkcje publiczne powinny rozpoczynać się od `namespace` deklaracji, a jedyne publiczne jednostki w przestrzeniach nazw powinny być typami.</span><span class="sxs-lookup"><span data-stu-id="e04e3-351">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="e04e3-352">Nie używaj modułów języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-352">Do not use F# modules.</span></span>

<span data-ttu-id="e04e3-353">Używanie modułów niepublicznych do przechowywania kodu implementacji, typów narzędzi i funkcji narzędziowych.</span><span class="sxs-lookup"><span data-stu-id="e04e3-353">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="e04e3-354">Typy statyczne powinny być preferowane dla modułów, ponieważ umożliwiają przyszłe ewolucję interfejsu API w celu korzystania z przeciążeń i innych koncepcji projektowania interfejsów API platformy .NET, które nie mogą być używane w modułach języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-354">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="e04e3-355">Na przykład zamiast następującego publicznego interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="e04e3-355">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="e04e3-356">Zamiast tego Rozważ:</span><span class="sxs-lookup"><span data-stu-id="e04e3-356">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="e04e3-357">Użyj typów rekordów języka F # w interfejsie API .NET w usłudze Wanili, jeśli projekt typów nie zostanie rozbudowany</span><span class="sxs-lookup"><span data-stu-id="e04e3-357">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="e04e3-358">Typy rekordów języka F # kompilują się do prostej klasy .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-358">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="e04e3-359">Są one odpowiednie dla niektórych prostych, stabilnych typów w interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="e04e3-359">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="e04e3-360">Rozważ użycie `[<NoEquality>]` atrybutów i, `[<NoComparison>]` Aby pominąć automatyczne generowanie interfejsów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-360">Consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="e04e3-361">Unikaj również używania modyfikowalnych pól rekordów w interfejsie API .NET w formacie Wanili, ponieważ uwidaczniają one pole publiczne.</span><span class="sxs-lookup"><span data-stu-id="e04e3-361">Also avoid using mutable record fields in vanilla .NET APIs as these expose a public field.</span></span> <span data-ttu-id="e04e3-362">Należy zawsze rozważyć, czy Klasa zapewni bardziej elastyczną opcję dla przyszłego rozwoju interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="e04e3-362">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="e04e3-363">Na przykład poniższy kod F # ujawnia publiczny interfejs API dla użytkownika w języku C#:</span><span class="sxs-lookup"><span data-stu-id="e04e3-363">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="e04e3-364">F#:</span><span class="sxs-lookup"><span data-stu-id="e04e3-364">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="e04e3-365">C#:</span><span class="sxs-lookup"><span data-stu-id="e04e3-365">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="e04e3-366">Ukryj reprezentację typów Unii języka F # w interfejsach API platformy .NET w usłudze Wanili</span><span class="sxs-lookup"><span data-stu-id="e04e3-366">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="e04e3-367">Typy Unii języka f # nie są często używane między granicami składników, nawet w przypadku kodowania F #-to-F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-367">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="e04e3-368">Są one doskonałym urządzeniem implementacji używanym wewnętrznie w ramach składników i bibliotek.</span><span class="sxs-lookup"><span data-stu-id="e04e3-368">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="e04e3-369">Podczas projektowania interfejsu API .NET w sieci Wanili, rozważ ukrycie reprezentacji typu złożenia przy użyciu prywatnej deklaracji lub pliku sygnatury.</span><span class="sxs-lookup"><span data-stu-id="e04e3-369">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="e04e3-370">Można również rozszerzyć typy, które używają reprezentacji Union wewnętrznie z elementami członkowskimi, aby zapewnić odpowiednie. Interfejs API w sieci.</span><span class="sxs-lookup"><span data-stu-id="e04e3-370">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="e04e3-371">Projektowanie graficznego interfejsu użytkownika i innych składników przy użyciu wzorców projektu struktury</span><span class="sxs-lookup"><span data-stu-id="e04e3-371">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="e04e3-372">Istnieje wiele różnych struktur dostępnych w ramach platformy .NET, takich jak WinForms, WPF i ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-372">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="e04e3-373">Nazwy i konwencje projektowania dla każdego z nich powinny być używane, jeśli projektujesz składniki do użycia w tych strukturach.</span><span class="sxs-lookup"><span data-stu-id="e04e3-373">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="e04e3-374">Na przykład w przypadku programowania WPF należy przyjąć wzorce projektowania WPF dla projektowanych klas.</span><span class="sxs-lookup"><span data-stu-id="e04e3-374">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="e04e3-375">W przypadku modeli w programowaniu interfejsu użytkownika Użyj wzorców projektowych, takich jak zdarzenia i kolekcje oparte na powiadomieniach, takie jak te, które znajdują się w <xref:System.Collections.ObjectModel> .</span><span class="sxs-lookup"><span data-stu-id="e04e3-375">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="e04e3-376">Projekt obiektu i elementu członkowskiego (dla bibliotek używanych z innych języków .NET)</span><span class="sxs-lookup"><span data-stu-id="e04e3-376">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="e04e3-377">Korzystanie z atrybutu CLIEvent w celu udostępnienia zdarzeń platformy .NET</span><span class="sxs-lookup"><span data-stu-id="e04e3-377">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="e04e3-378">Konstrukcja a `DelegateEvent` z określonym typem delegata platformy .NET, który przyjmuje obiekt i `EventArgs` (zamiast `Event` , który właśnie używa `FSharpHandler` typu domyślnie), aby zdarzenia były publikowane w znany sposób w innych językach .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-378">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a><span data-ttu-id="e04e3-379">Uwidacznianie operacji asynchronicznych jako metod, które zwracają zadania .NET</span><span class="sxs-lookup"><span data-stu-id="e04e3-379">Expose asynchronous operations as methods that return .NET tasks</span></span>

<span data-ttu-id="e04e3-380">Zadania są używane w programie .NET do reprezentowania aktywnych asynchronicznych obliczeń.</span><span class="sxs-lookup"><span data-stu-id="e04e3-380">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="e04e3-381">Zadania są generalnie mniejsze niż obiekty języka F # `Async<T>` , ponieważ reprezentują "już wykonywane" zadania i nie mogą być tworzone razem w sposób, który wykonuje równoległą kompozycję lub które ukrywają propagacje sygnałów anulowania i innych parametrów kontekstowych.</span><span class="sxs-lookup"><span data-stu-id="e04e3-381">Tasks are in general less compositional than F# `Async<T>` objects, since they represent "already executing" tasks and can't be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="e04e3-382">Jednak pomimo tego, metody zwracające zadania są standardową reprezentacją programowania asynchronicznego w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-382">However, despite this, methods that return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="e04e3-383">Często trzeba również zaakceptować jawny token anulowania:</span><span class="sxs-lookup"><span data-stu-id="e04e3-383">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="e04e3-384">Użyj typów delegatów platformy .NET zamiast typów funkcji języka F #</span><span class="sxs-lookup"><span data-stu-id="e04e3-384">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="e04e3-385">W tym miejscu "typy funkcji języka F #" oznaczają ", takie jak `int -> int` .</span><span class="sxs-lookup"><span data-stu-id="e04e3-385">Here "F# function types" mean "arrow" types like `int -> int`.</span></span>

<span data-ttu-id="e04e3-386">Zamiast tego:</span><span class="sxs-lookup"><span data-stu-id="e04e3-386">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="e04e3-387">Wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e04e3-387">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="e04e3-388">Typ funkcji języka F # jest wyświetlany w `class FSharpFunc<T,U>` innych językach .NET i jest mniej odpowiedni dla funkcji języka i narzędzi, które są zrozumiałe dla typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-388">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understands delegate types.</span></span> <span data-ttu-id="e04e3-389">Podczas tworzenia metody wyższej kolejności docelowej .NET Framework 3,5 lub nowszej, `System.Func` `System.Action` Delegaty i są odpowiednie interfejsy API do opublikowania, aby umożliwić deweloperom platformy .NET korzystanie z tych interfejsów API w sposób słaby.</span><span class="sxs-lookup"><span data-stu-id="e04e3-389">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="e04e3-390">(W przypadku określania wartości docelowej .NET Framework 2,0 typy delegatów zdefiniowane przez system są bardziej ograniczone; Rozważ użycie wstępnie zdefiniowanych typów delegatów, takich jak `System.Converter<T,U>` lub Definiowanie określonego typu delegata).</span><span class="sxs-lookup"><span data-stu-id="e04e3-390">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="e04e3-391">Na stronie Przerzucanie delegatów platformy .NET nie są naturalne dla bibliotek mających dostęp do języka F # (zobacz następną sekcję w bibliotekach przeznaczonych dla języka F #).</span><span class="sxs-lookup"><span data-stu-id="e04e3-391">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="e04e3-392">W związku z tym typową strategią implementacji podczas opracowywania metod wyższego rzędu dla bibliotek .NET w formacie Wanili jest utworzenie całej implementacji przy użyciu typów funkcji języka F #, a następnie Tworzenie publicznego interfejsu API za pomocą delegatów jako wąskie fasada korzystającego rzeczywistą implementację języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-392">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="e04e3-393">Użyj wzorca TryGetValue zamiast zwracać wartości opcji F # i Preferuj przeciążanie metody w celu pobierania wartości opcji F # jako argumentów</span><span class="sxs-lookup"><span data-stu-id="e04e3-393">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="e04e3-394">Typowe wzorce użycia dla typu opcji języka F # w interfejsach API są lepiej zaimplementowane w interfejsie API platformy .NET w usłudze Wanili przy użyciu standardowych technik projektowania platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-394">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="e04e3-395">Zamiast zwracać wartość opcji F #, rozważ użycie typu zwracanego bool oraz parametru out, jak w wzorcu "TryGetValue".</span><span class="sxs-lookup"><span data-stu-id="e04e3-395">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="e04e3-396">Zamiast przyjmować wartości opcji F # jako parametry, należy rozważyć użycie przeciążania metod lub opcjonalnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-396">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="e04e3-397">Użyj typów interfejsu kolekcji platformy .NET IEnumerable \< T \> i IDictionary \< , wartość \> parametrów i zwracanych wartości</span><span class="sxs-lookup"><span data-stu-id="e04e3-397">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="e04e3-398">Unikaj używania konkretnych typów kolekcji, takich jak tablice .NET `T[]` , typy języka F # `list<T>` , `Map<Key,Value>` oraz `Set<T>` typy kolekcji konkretnych dla platformy .NET, takich jak `Dictionary<Key,Value>` .</span><span class="sxs-lookup"><span data-stu-id="e04e3-398">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="e04e3-399">Wskazówki dotyczące projektowania biblioteki .NET mają dobre porady dotyczące sytuacji, w których należy używać różnych typów kolekcji, takich jak `IEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="e04e3-399">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="e04e3-400">Niektóre zastosowania tablic ( `T[]` ) są dopuszczalne w pewnych okolicznościach, z przyczyn związanych z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="e04e3-400">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="e04e3-401">Należy zwrócić uwagę `seq<T>` na to, że jest to tylko alias F # dla `IEnumerable<T>` , i w ten sposób sekwencja jest często odpowiednim typem dla interfejsu API .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-401">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="e04e3-402">Zamiast list języka F #:</span><span class="sxs-lookup"><span data-stu-id="e04e3-402">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="e04e3-403">Użyj sekwencji języka F #:</span><span class="sxs-lookup"><span data-stu-id="e04e3-403">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="e04e3-404">Użyj typu jednostki jako jedynego typu danych wejściowych metody do zdefiniowania metody zero lub jako jedynego zwracanego typu, aby zdefiniować metodę void-Return</span><span class="sxs-lookup"><span data-stu-id="e04e3-404">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="e04e3-405">Unikaj innych użycia typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="e04e3-405">Avoid other uses of the unit type.</span></span> <span data-ttu-id="e04e3-406">Są one dobre:</span><span class="sxs-lookup"><span data-stu-id="e04e3-406">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="e04e3-407">To nie jest właściwe:</span><span class="sxs-lookup"><span data-stu-id="e04e3-407">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="e04e3-408">Sprawdź pod kątem wartości null w granicach interfejsu API .NET Wanili</span><span class="sxs-lookup"><span data-stu-id="e04e3-408">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="e04e3-409">Kod implementacji języka F # ma mniejszą liczbę wartości null, ze względu na niezmienne wzorce projektowe i ograniczenia dotyczące używania literałów o wartości null dla typów języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-409">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="e04e3-410">Inne języki .NET często używają wartości null, co jest znacznie częściej.</span><span class="sxs-lookup"><span data-stu-id="e04e3-410">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="e04e3-411">Z tego względu kod języka F #, który uwidacznia interfejs API platformy .NET, powinien sprawdzać parametry dla wartości null na granicy interfejsu API i uniemożliwiać przepływanie tych wartości do kodu implementacji języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-411">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="e04e3-412">`isNull`Można użyć funkcji lub dopasowania do wzorca na `null` wzorcu.</span><span class="sxs-lookup"><span data-stu-id="e04e3-412">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="e04e3-413">Unikaj używania krotek jako wartości zwracanych</span><span class="sxs-lookup"><span data-stu-id="e04e3-413">Avoid using tuples as return values</span></span>

<span data-ttu-id="e04e3-414">Zamiast tego, Preferuj zwraca nazwany typ przechowujący zagregowane dane lub korzystając z parametrów out, aby zwracać wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="e04e3-414">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="e04e3-415">Chociaż krotki i krotek struktury istnieją w programie .NET (łącznie z obsługą języka C# dla krotek struktury), najczęściej nie zapewniają idealnego i oczekiwanego interfejsu API dla deweloperów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-415">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="e04e3-416">Unikaj używania currying parametrów</span><span class="sxs-lookup"><span data-stu-id="e04e3-416">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="e04e3-417">Zamiast tego należy używać konwencji wywoływania platformy .NET `Method(arg1,arg2,…,argN)` .</span><span class="sxs-lookup"><span data-stu-id="e04e3-417">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="e04e3-418">Porada: Jeśli projektujesz biblioteki do użytku z dowolnego języka .NET, nie ma znaczenia dla faktycznego wykonywania niektórych eksperymentalnych języków C# i Visual Basic, aby upewnić się, że biblioteki "działają bezpośrednio" w tych językach.</span><span class="sxs-lookup"><span data-stu-id="e04e3-418">Tip: If you're designing libraries for use from any .NET language, then there's no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="e04e3-419">Możesz również użyć narzędzi takich jak reflektor .NET i program Visual Studio Przeglądarka obiektów, aby upewnić się, że biblioteki i ich dokumentacja będą wyglądały zgodnie z oczekiwaniami dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="e04e3-419">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="e04e3-420">Dodatek</span><span class="sxs-lookup"><span data-stu-id="e04e3-420">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="e04e3-421">Kompleksowy przykład projektowania kodu języka F # do użycia przez inne języki .NET</span><span class="sxs-lookup"><span data-stu-id="e04e3-421">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="e04e3-422">Rozważmy następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="e04e3-422">Consider the following class:</span></span>

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

<span data-ttu-id="e04e3-423">Wywnioskowany typ F # tej klasy jest następujący:</span><span class="sxs-lookup"><span data-stu-id="e04e3-423">The inferred F# type of this class is as follows:</span></span>

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

<span data-ttu-id="e04e3-424">Przyjrzyjmy się, jak ten typ języka F # jest widoczny dla programisty przy użyciu innego języka platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e04e3-424">Let's take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="e04e3-425">Na przykład przybliżona "sygnatura" w języku C# jest następująca:</span><span class="sxs-lookup"><span data-stu-id="e04e3-425">For example, the approximate C# "signature" is as follows:</span></span>

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="e04e3-426">Istnieją pewne ważne punkty, które należy zwrócić uwagę na to, w jaki sposób F # reprezentuje konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="e04e3-426">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="e04e3-427">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e04e3-427">For example:</span></span>

* <span data-ttu-id="e04e3-428">Metadane, takie jak nazwy argumentów, zostały zachowane.</span><span class="sxs-lookup"><span data-stu-id="e04e3-428">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="e04e3-429">Metody języka F #, które przyjmują dwa argumenty, stają się metodami języka C#, które przyjmują dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="e04e3-429">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="e04e3-430">Funkcje i listy stają się odwołaniami do odpowiednich typów w bibliotece języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-430">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="e04e3-431">Poniższy kod pokazuje, jak dostosować ten kod, aby wziąć pod uwagę te zagadnienia.</span><span class="sxs-lookup"><span data-stu-id="e04e3-431">The following code shows how to adjust this code to take these things into account.</span></span>

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

<span data-ttu-id="e04e3-432">Wywnioskowany typ F # jest następujący:</span><span class="sxs-lookup"><span data-stu-id="e04e3-432">The inferred F# type of the code is as follows:</span></span>

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

<span data-ttu-id="e04e3-433">Sygnatura języka C# jest teraz następująca:</span><span class="sxs-lookup"><span data-stu-id="e04e3-433">The C# signature is now as follows:</span></span>

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="e04e3-434">Poprawki wykonane w celu przygotowania tego typu do użycia w ramach biblioteki programu .NET w formacie Wanili są następujące:</span><span class="sxs-lookup"><span data-stu-id="e04e3-434">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="e04e3-435">Zmieniono kilka nazw: `Point1` , `n` ,, `l` i `f` stała `RadialPoint` się, `count` , `factor` , i `transform` , odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="e04e3-435">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="e04e3-436">Użyto typu zwracanego `seq<RadialPoint>` zamiast `RadialPoint list` przez zmianę konstrukcji listy przy użyciu `[ ... ]` do konstrukcji sekwencji przy użyciu `IEnumerable<RadialPoint>` .</span><span class="sxs-lookup"><span data-stu-id="e04e3-436">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="e04e3-437">Użyto typu delegata platformy .NET `System.Func` zamiast typu funkcji języka F #.</span><span class="sxs-lookup"><span data-stu-id="e04e3-437">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="e04e3-438">Pozwala to na korzystanie z kodu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="e04e3-438">This makes it far nicer to consume in C# code.</span></span>
