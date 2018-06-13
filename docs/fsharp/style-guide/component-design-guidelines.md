---
title: 'F # składnika zaleceń dotyczących projektowania'
description: 'Dowiedz się wskazówki dotyczące pisania F # składniki przeznaczone do użytku przez inne obiekty wywołujące.'
ms.date: 05/14/2018
ms.openlocfilehash: 7e71710b1bc2fe3e8d7a5a091513a1432650dc04
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34458089"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="ee822-103">F # składnika zaleceń dotyczących projektowania</span><span class="sxs-lookup"><span data-stu-id="ee822-103">F# component design guidelines</span></span>

<span data-ttu-id="ee822-104">Ten dokument jest zestaw zaleceń dotyczących projektowania składnika w F # programowania, na podstawie F # składnika projektu wytycznych, wersja 14, Microsoft Research i [inna wersja](https://fsharp.org/specs/component-design-guidelines/) pierwotnie wyselekcjonowanych i obsługiwanego przez Foundation oprogramowania F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and [another version](https://fsharp.org/specs/component-design-guidelines/) originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="ee822-105">Tym dokumencie przyjęto założenie, że znasz programowania w języku F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="ee822-106">Wiele dzięki użyciu społeczności F # dla ich wkład i opinie pomocne w różnych wersjach tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="ee822-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="ee822-107">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ee822-107">Overview</span></span>

<span data-ttu-id="ee822-108">Ten dokument wygląda na kilka zagadnień dotyczących projektowania składnika F # i kodowania.</span><span class="sxs-lookup"><span data-stu-id="ee822-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="ee822-109">Składnik może oznaczać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ee822-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="ee822-110">Warstwa w projekcie F # z zewnętrznego konsumentów w ramach tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ee822-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="ee822-111">Biblioteka przeznaczonych do użycia w kodzie języka F # poza granicami zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee822-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="ee822-112">Biblioteka przeznaczonych do użycia za pomocą dowolnego języka .NET poza granicami zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee822-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="ee822-113">Biblioteki przeznaczone do dystrybucji za pośrednictwem z repozytorium pakietów, takie jak [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="ee822-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="ee822-114">Postępuj zgodnie z metod opisanych w tym artykule [pięć zasadami dobrej kodzie języka F #](index.md#five-principles-of-good-f-code)i w związku z tym korzystania zarówno funkcjonalności i obiekt programowania zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="ee822-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="ee822-115">Niezależnie od metody Projektant składnika i biblioteki skierowany liczba praktycznych i prosaic problemy podczas próby jednostki interfejsu API, który jest łatwo używany przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="ee822-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="ee822-116">Stosowanie sumienia [zaleceń dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md) kierowania kierunku tworzenia spójny zestaw interfejsów API, które są przyjemne korzystać.</span><span class="sxs-lookup"><span data-stu-id="ee822-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="ee822-117">Ogólne wskazówki</span><span class="sxs-lookup"><span data-stu-id="ee822-117">General guidelines</span></span>

<span data-ttu-id="ee822-118">Istnieje kilka uniwersalnych wskazówki, które dotyczą F # bibliotek, niezależnie od określonej grupy odbiorców w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="ee822-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="ee822-119">Dowiedz się więcej zaleceń dotyczących projektowania biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="ee822-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="ee822-120">Niezależnie od rodzaju F # kodowania operacji jest przydatna dla mieć praktyczną wiedzę o [zaleceń dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee822-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="ee822-121">Większość innych F # programistów platformy .NET zostanie należy zapoznać się z tymi wytycznymi i oczekują kodu platformy .NET, które są zgodne z nich.</span><span class="sxs-lookup"><span data-stu-id="ee822-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="ee822-122">Wytyczne dotyczące projektowania biblioteki .NET zawierają ogólne wskazówki dotyczące nazewnictwa, projektowanie klasy i interfejsy, elementu członkowskiego projektu (właściwości, metody, zdarzenia, itp.) i inne, a są przydatne, pierwszy punkt odniesienia dla różnych wskazówki dotyczące projektowania.</span><span class="sxs-lookup"><span data-stu-id="ee822-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="ee822-123">Dodaj komentarze dokumentacji XML w kodzie</span><span class="sxs-lookup"><span data-stu-id="ee822-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="ee822-124">Plik dokumentacji XML w publicznych interfejsach API upewnij się, że użytkownicy mogą uzyskać doskonałe Intellisense i skrócone informacje podczas plików przy użyciu tych typów i członków i Włącz tworzenie dokumentacji dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ee822-124">XML documentation on public APIs ensure that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="ee822-125">Zobacz [dokumentacji XML](../language-reference/xml-documentation.md) o różnych tagi xml, które mogą być używane dla dodatkowych znacznika w xmldoc komentarze.</span><span class="sxs-lookup"><span data-stu-id="ee822-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

<span data-ttu-id="ee822-126">Można użyć albo komentarze XML Krótka forma (`/// comment`), lub standardowy komentarze XML (`///<summary>comment</summary>`).</span><span class="sxs-lookup"><span data-stu-id="ee822-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="ee822-127">Rozważ użycie jawnego podpisów (.fsi) bibliotekę stabilny i składników interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ee822-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="ee822-128">Przy użyciu jawnych podpisów plików w bibliotece języka F # zawiera zwięzły podsumowanie publiczny interfejs API, których można mieć pewność, że należy znać publicznej powierzchni biblioteki, a także zapewnia czyste rozdzielenie między dokumentacji publicznych oraz wewnętrznych Szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="ee822-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which both helps to ensure that you know the full public surface of your library, as well as provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="ee822-129">Należy pamiętać, że pliki sygnatur dodać tarcia na zmieniające się publiczny interfejs API, wymagając od zmian wprowadzanych w plikach wykonania i podpis.</span><span class="sxs-lookup"><span data-stu-id="ee822-129">Note that signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="ee822-130">W związku z tym pliki sygnatur zwykle tylko należy wprowadzić po interfejs API stają się zestalone i nie powinien zmienić znacznie.</span><span class="sxs-lookup"><span data-stu-id="ee822-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="ee822-131">Zawsze należy stosować najlepsze rozwiązania dotyczące używania ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="ee822-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="ee822-132">Postępuj zgodnie z [najlepsze rozwiązania dotyczące przy użyciu ciągów w .NET](../../standard/base-types/best-practices-strings.md) wskazówki.</span><span class="sxs-lookup"><span data-stu-id="ee822-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="ee822-133">W szczególności zawsze jawnie określać *kultury zamiar* konwersji i porównywania ciągów (jeśli dotyczy).</span><span class="sxs-lookup"><span data-stu-id="ee822-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="ee822-134">Wytyczne dotyczące F #-ukierunkowane bibliotek</span><span class="sxs-lookup"><span data-stu-id="ee822-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="ee822-135">W tej sekcji przedstawiono zalecenia dotyczące tworzenia publicznego F #-ukierunkowane biblioteki; oznacza to, bibliotek udostępnia publiczne interfejsy API, które mają być używane przez deweloperów w F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="ee822-136">Istnieją różne projektu biblioteki zaleceń dotyczy w szczególności F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="ee822-137">W przypadku braku konkretnych zaleceń, które należy wykonać zaleceń dotyczących projektowania biblioteki .NET są wskazówki rezerwowego.</span><span class="sxs-lookup"><span data-stu-id="ee822-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="ee822-138">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="ee822-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="ee822-139">Użyj .NET konwencji nazewnictwa i wielkości liter</span><span class="sxs-lookup"><span data-stu-id="ee822-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="ee822-140">Poniższa tabela jest zgodna z konwencjami .NET nazewnictwa i wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="ee822-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="ee822-141">Brak małych dodatki do również obejmować konstrukcje F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="ee822-142">Konstrukcja</span><span class="sxs-lookup"><span data-stu-id="ee822-142">Construct</span></span> | <span data-ttu-id="ee822-143">Case</span><span class="sxs-lookup"><span data-stu-id="ee822-143">Case</span></span> | <span data-ttu-id="ee822-144">Część</span><span class="sxs-lookup"><span data-stu-id="ee822-144">Part</span></span> | <span data-ttu-id="ee822-145">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ee822-145">Examples</span></span> | <span data-ttu-id="ee822-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee822-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="ee822-147">Typów konkretnych</span><span class="sxs-lookup"><span data-stu-id="ee822-147">Concrete types</span></span> | <span data-ttu-id="ee822-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-148">PascalCase</span></span> | <span data-ttu-id="ee822-149">Rzeczownik / przymiotników</span><span class="sxs-lookup"><span data-stu-id="ee822-149">Noun/ adjective</span></span> | <span data-ttu-id="ee822-150">Lista, Double, złożone</span><span class="sxs-lookup"><span data-stu-id="ee822-150">List, Double, Complex</span></span> | <span data-ttu-id="ee822-151">Konkretne typy są struktury, klas, wyliczeń, delegatów, rekordów i Unii.</span><span class="sxs-lookup"><span data-stu-id="ee822-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="ee822-152">Chociaż nazwy typów są tradycyjnie małe litery w OCaml, F # przyjęła schemat nazewnictwa .NET dla typów.</span><span class="sxs-lookup"><span data-stu-id="ee822-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="ee822-153">biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="ee822-153">DLLs</span></span>           | <span data-ttu-id="ee822-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-154">PascalCase</span></span> |                 | <span data-ttu-id="ee822-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="ee822-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="ee822-156">Tagi Unii</span><span class="sxs-lookup"><span data-stu-id="ee822-156">Union tags</span></span>     | <span data-ttu-id="ee822-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-157">PascalCase</span></span> | <span data-ttu-id="ee822-158">rzeczownik</span><span class="sxs-lookup"><span data-stu-id="ee822-158">Noun</span></span> | <span data-ttu-id="ee822-159">Niektóre, Dodaj Powodzenie</span><span class="sxs-lookup"><span data-stu-id="ee822-159">Some, Add, Success</span></span> | <span data-ttu-id="ee822-160">Nie używaj prefiksu w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="ee822-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="ee822-161">Opcjonalnie użyj prefiksu, gdy wewnętrznych, takich jak ''' wpisz zespoły = TAlpha</span><span class="sxs-lookup"><span data-stu-id="ee822-161">Optionally use a prefix when internal, such as \`\`\`type Teams = TAlpha</span></span> | <span data-ttu-id="ee822-162">TBeta</span><span class="sxs-lookup"><span data-stu-id="ee822-162">TBeta</span></span> | <span data-ttu-id="ee822-163">TDelta. ""</span><span class="sxs-lookup"><span data-stu-id="ee822-163">TDelta.\`\`\`</span></span> |
| <span data-ttu-id="ee822-164">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ee822-164">Event</span></span>          | <span data-ttu-id="ee822-165">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-165">PascalCase</span></span> | <span data-ttu-id="ee822-166">Zlecenie</span><span class="sxs-lookup"><span data-stu-id="ee822-166">Verb</span></span> | <span data-ttu-id="ee822-167">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="ee822-167">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="ee822-168">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="ee822-168">Exceptions</span></span>     | <span data-ttu-id="ee822-169">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-169">PascalCase</span></span> |      | <span data-ttu-id="ee822-170">WebException</span><span class="sxs-lookup"><span data-stu-id="ee822-170">WebException</span></span> | <span data-ttu-id="ee822-171">Nazwa powinna kończyć się "Wyjątków".</span><span class="sxs-lookup"><span data-stu-id="ee822-171">Name should end with “Exception”.</span></span> |
| <span data-ttu-id="ee822-172">Pole</span><span class="sxs-lookup"><span data-stu-id="ee822-172">Field</span></span>          | <span data-ttu-id="ee822-173">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-173">PascalCase</span></span> | <span data-ttu-id="ee822-174">rzeczownik</span><span class="sxs-lookup"><span data-stu-id="ee822-174">Noun</span></span> | <span data-ttu-id="ee822-175">CurrentName</span><span class="sxs-lookup"><span data-stu-id="ee822-175">CurrentName</span></span>  | |
| <span data-ttu-id="ee822-176">Typy interfejsów</span><span class="sxs-lookup"><span data-stu-id="ee822-176">Interface types</span></span> |  <span data-ttu-id="ee822-177">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-177">PascalCase</span></span> | <span data-ttu-id="ee822-178">Rzeczownik / przymiotników</span><span class="sxs-lookup"><span data-stu-id="ee822-178">Noun/ adjective</span></span> | <span data-ttu-id="ee822-179">Interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="ee822-179">IDisposable</span></span> | <span data-ttu-id="ee822-180">Nazwa powinna zaczynać się znakiem "I".</span><span class="sxs-lookup"><span data-stu-id="ee822-180">Name should start with “I”.</span></span> |
| <span data-ttu-id="ee822-181">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee822-181">Method</span></span> |  <span data-ttu-id="ee822-182">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-182">PascalCase</span></span> |  <span data-ttu-id="ee822-183">Zlecenie</span><span class="sxs-lookup"><span data-stu-id="ee822-183">Verb</span></span> | <span data-ttu-id="ee822-184">ToString</span><span class="sxs-lookup"><span data-stu-id="ee822-184">ToString</span></span> | |
| <span data-ttu-id="ee822-185">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ee822-185">Namespace</span></span> | <span data-ttu-id="ee822-186">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-186">PascalCase</span></span> | | <span data-ttu-id="ee822-187">Microsoft.fsharp.Core —</span><span class="sxs-lookup"><span data-stu-id="ee822-187">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="ee822-188">Na ogół służy `<Organization>.<Technology>[.<Subnamespace>]`, mimo że Porzuć organizacji, jeśli ta technologia jest niezależna od organizacji.</span><span class="sxs-lookup"><span data-stu-id="ee822-188">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="ee822-189">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee822-189">Parameters</span></span> | <span data-ttu-id="ee822-190">(camelcase)</span><span class="sxs-lookup"><span data-stu-id="ee822-190">camelCase</span></span> | <span data-ttu-id="ee822-191">rzeczownik</span><span class="sxs-lookup"><span data-stu-id="ee822-191">Noun</span></span> |  <span data-ttu-id="ee822-192">właściwość typeName, transform, zakres</span><span class="sxs-lookup"><span data-stu-id="ee822-192">typeName, transform, range</span></span> | |
| <span data-ttu-id="ee822-193">Let wartości (wewnętrzny)</span><span class="sxs-lookup"><span data-stu-id="ee822-193">let values (internal)</span></span> | <span data-ttu-id="ee822-194">(camelcase) lub PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-194">camelCase or PascalCase</span></span> | <span data-ttu-id="ee822-195">Rzeczownik / zlecenie</span><span class="sxs-lookup"><span data-stu-id="ee822-195">Noun/ verb</span></span> |  <span data-ttu-id="ee822-196">getValue, myTable</span><span class="sxs-lookup"><span data-stu-id="ee822-196">getValue, myTable</span></span> |
| <span data-ttu-id="ee822-197">Let wartości (zewnętrzne)</span><span class="sxs-lookup"><span data-stu-id="ee822-197">let values (external)</span></span> | <span data-ttu-id="ee822-198">(camelcase) lub PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-198">camelCase or PascalCase</span></span> | <span data-ttu-id="ee822-199">Rzeczownik/zlecenie</span><span class="sxs-lookup"><span data-stu-id="ee822-199">Noun/verb</span></span>  | <span data-ttu-id="ee822-200">List.map, Dates.Today</span><span class="sxs-lookup"><span data-stu-id="ee822-200">List.map, Dates.Today</span></span> | <span data-ttu-id="ee822-201">Let granica wartości często są publiczne, po wzorce projektowe funkcjonalności tradycyjnych.</span><span class="sxs-lookup"><span data-stu-id="ee822-201">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="ee822-202">Jednak na ogół służy PascalCase podczas identyfikator można używać z innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-202">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="ee822-203">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ee822-203">Property</span></span>  | <span data-ttu-id="ee822-204">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ee822-204">PascalCase</span></span>  | <span data-ttu-id="ee822-205">Rzeczownik / przymiotników</span><span class="sxs-lookup"><span data-stu-id="ee822-205">Noun/ adjective</span></span>  | <span data-ttu-id="ee822-206">IsEndOfFile, BackColor</span><span class="sxs-lookup"><span data-stu-id="ee822-206">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="ee822-207">Operatory logiczne ogólnie użycie jest i może i powinno być potwierdzającego, tak jak IsEndOfFile, nie IsNotEndOfFile.</span><span class="sxs-lookup"><span data-stu-id="ee822-207">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="ee822-208">Unikaj skrótów</span><span class="sxs-lookup"><span data-stu-id="ee822-208">Avoid abbreviations</span></span>

<span data-ttu-id="ee822-209">Wytyczne .NET nadal stosować skróty (na przykład "Użyj `OnButtonClick` zamiast `OnBtnClick`").</span><span class="sxs-lookup"><span data-stu-id="ee822-209">The .NET guidelines discourage the use of abbreviations (for example, “use `OnButtonClick` rather than `OnBtnClick`”).</span></span> <span data-ttu-id="ee822-210">Skrótów, takich jak `Async` są dopuszczalne dla "Asynchronous".</span><span class="sxs-lookup"><span data-stu-id="ee822-210">Common abbreviations, such as `Async` for “Asynchronous”, are tolerated.</span></span> <span data-ttu-id="ee822-211">Niniejsze wytyczne czasami jest ignorowany dla funkcjonalności programowania. na przykład `List.iter` używa skrót "iteracyjne".</span><span class="sxs-lookup"><span data-stu-id="ee822-211">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for “iterate”.</span></span> <span data-ttu-id="ee822-212">Z tego powodu przy użyciu skróty zwykle następować do lepszej w języku F #-do-F # — programowanie, ale nadal ogólnie należy unikać w projekcie składnik publiczny.</span><span class="sxs-lookup"><span data-stu-id="ee822-212">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="ee822-213">Unikaj wielkość liter konflikty nazw</span><span class="sxs-lookup"><span data-stu-id="ee822-213">Avoid casing name collisions</span></span>

<span data-ttu-id="ee822-214">Wytyczne .NET powiedzieć, że wielkość liter samodzielnie nie można użyć do odróżniania konflikty nazw, ponieważ niektóre języki klienta (na przykład Visual Basic) jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="ee822-214">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="ee822-215">Użyj akronimów, gdzie jest to odpowiednie</span><span class="sxs-lookup"><span data-stu-id="ee822-215">Use acronyms where appropriate</span></span>

<span data-ttu-id="ee822-216">Skrótów, takich jak XML nie są skróty i są powszechnie używane w bibliotekach .NET w postaci małymi (Xml).</span><span class="sxs-lookup"><span data-stu-id="ee822-216">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="ee822-217">Tylko akronimów dobrze znane, powszechnie rozpoznanym powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="ee822-217">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="ee822-218">Użyj PascalCase dla nazw parametrów ogólnych</span><span class="sxs-lookup"><span data-stu-id="ee822-218">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="ee822-219">Należy używać PascalCase nazw parametru ogólnego w publicznych interfejsach API, w tym w F #-ukierunkowane bibliotek.</span><span class="sxs-lookup"><span data-stu-id="ee822-219">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="ee822-220">W szczególności, użyj nazwy, jak `T`, `U`, `T1`, `T2` dla dowolnego parametry ogólne i gdy konkretne nazwy sensu, następnie w F #-nazwy, jak używać dostępnych bibliotek `Key`, `Value`, `Arg`(ale nie na przykład `TKey`).</span><span class="sxs-lookup"><span data-stu-id="ee822-220">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="ee822-221">Użyj PascalCase lub (camelcase) dla funkcji publicznych i wartości w modułach F #</span><span class="sxs-lookup"><span data-stu-id="ee822-221">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="ee822-222">(camelcase) służy do publicznego funkcje, które są przeznaczone do użycia niekwalifikowane (na przykład `invalidArg`), a "kolekcji standardowych funkcji" (na przykład List.map).</span><span class="sxs-lookup"><span data-stu-id="ee822-222">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the “standard collection functions” (for example, List.map).</span></span> <span data-ttu-id="ee822-223">W obu przypadkach nazwy funkcji znacznie działać tak jak słów kluczowych w języku.</span><span class="sxs-lookup"><span data-stu-id="ee822-223">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="ee822-224">Obiekt, typ i modułu projektu</span><span class="sxs-lookup"><span data-stu-id="ee822-224">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="ee822-225">Zawiera modułów i typów za pomocą przestrzeni nazw lub modułów</span><span class="sxs-lookup"><span data-stu-id="ee822-225">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="ee822-226">Każdy plik F # w składniku powinien zaczynać się od deklaracji przestrzeni nazw lub deklaracji modułu.</span><span class="sxs-lookup"><span data-stu-id="ee822-226">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="ee822-227">lub</span><span class="sxs-lookup"><span data-stu-id="ee822-227">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="ee822-228">Różnice między organizowanie kodu na najwyższym poziomie za pomocą modułów i przestrzenie nazw są następujące:</span><span class="sxs-lookup"><span data-stu-id="ee822-228">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="ee822-229">Przestrzenie nazw może obejmować wiele plików</span><span class="sxs-lookup"><span data-stu-id="ee822-229">Namespaces can span multiple files</span></span>
* <span data-ttu-id="ee822-230">Przestrzenie nazw nie może zawierać funkcje F #, chyba że są one modułu wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="ee822-230">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="ee822-231">Kod dla dowolnego podanego modułu musi być zawarty w jednym pliku</span><span class="sxs-lookup"><span data-stu-id="ee822-231">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="ee822-232">Moduły najwyższego poziomu może zawierać funkcje F # bez konieczności moduł wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="ee822-232">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="ee822-233">Wybór między najwyższego poziomu przestrzeni nazw lub modułu ma wpływ na formularzu skompilowanego kodu i w związku z tym będzie miało wpływ na widoku z innymi językami .NET należy interfejsu API ostatecznie używane poza kodzie języka F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-233">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="ee822-234">Użyj metody i właściwości dla operacji wewnętrznej do typów obiektów</span><span class="sxs-lookup"><span data-stu-id="ee822-234">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="ee822-235">Praca z obiektami, najlepiej upewnij się, że funkcje eksploatacyjny zostały zaimplementowane jako metody i właściwości tego typu.</span><span class="sxs-lookup"><span data-stu-id="ee822-235">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="ee822-236">Zbiorczego funkcji dla danego elementu członkowskiego nie muszą zawsze zaimplementowana w tym elemencie członkowskim, ale powinien być element eksploatacyjny te funkcje.</span><span class="sxs-lookup"><span data-stu-id="ee822-236">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="ee822-237">Umożliwia Hermetyzowanie modyfikowalną stan klasy</span><span class="sxs-lookup"><span data-stu-id="ee822-237">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="ee822-238">W języku F # to tylko trzeba zrobić, gdzie czy stanu nie jest już zamknięte przez inny konstrukcji języka, takie jak zamknięcia, wyrażenie sekwencji lub obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="ee822-238">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="ee822-239">Użyj interfejsów do grupy działań związanych z</span><span class="sxs-lookup"><span data-stu-id="ee822-239">Use interfaces to group related operations</span></span>

<span data-ttu-id="ee822-240">Typy interfejsów umożliwia reprezentują zestaw operacji.</span><span class="sxs-lookup"><span data-stu-id="ee822-240">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="ee822-241">Jest to preferowana względem inne opcje, takie jak krotek, funkcji lub rekordy funkcji.</span><span class="sxs-lookup"><span data-stu-id="ee822-241">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="ee822-242">W preference do:</span><span class="sxs-lookup"><span data-stu-id="ee822-242">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

<span data-ttu-id="ee822-243">Interfejsy są najwyższej jakości pojęcia związane z .NET, który służy do osiągnięcia co Funktorów pozwoli zwykle uzyskać.</span><span class="sxs-lookup"><span data-stu-id="ee822-243">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="ee822-244">Ponadto może być używany do kodowania typów egzystencjalna do tego programu, który rejestruje funkcji nie może.</span><span class="sxs-lookup"><span data-stu-id="ee822-244">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a><span data-ttu-id="ee822-245">Używaj modułu TPM na funkcje grupy, które działają w kolekcjach</span><span class="sxs-lookup"><span data-stu-id="ee822-245">Use a module to group functions which act on collections</span></span>

<span data-ttu-id="ee822-246">Podczas definiowania typem kolekcji, należy wziąć pod uwagę zapewnienie standardowy zestaw operacji, takich jak `CollectionType.map` i `CollectionType.iter`) dla nowych typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ee822-246">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="ee822-247">Jeśli takie modułu, wykonaj standardowe konwencje nazewnictwa dla funkcji systemu plikiem FSharp.Core.</span><span class="sxs-lookup"><span data-stu-id="ee822-247">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="ee822-248">Używaj modułu TPM do funkcji grupy do typowych funkcji kanonicznej, szczególnie w matematyczne i bibliotek DSL</span><span class="sxs-lookup"><span data-stu-id="ee822-248">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="ee822-249">Na przykład `Microsoft.FSharp.Core.Operators` automatycznie otwarte zbiór funkcji najwyższego poziomu (takich jak `abs` i `sin`) podany w pliku FSharp.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="ee822-249">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="ee822-250">Podobnie, biblioteka statystyki może obejmować modułu z funkcjami `erf` i `erfc`, gdy ten moduł jest może być jawnie lub automatycznie otwarte.</span><span class="sxs-lookup"><span data-stu-id="ee822-250">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="ee822-251">Należy rozważyć użycie RequireQualifiedAccess i ostrożnie stosować atrybutów AutoOpen</span><span class="sxs-lookup"><span data-stu-id="ee822-251">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="ee822-252">Dodawanie `[<RequireQualifiedAccess>]` modułu dla atrybutu wskazuje, że moduł nie może być otwarty i że odwołania do elementów modułu, wymaga jawnego kwalifikowana dostępu.</span><span class="sxs-lookup"><span data-stu-id="ee822-252">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="ee822-253">Na przykład `Microsoft.FSharp.Collections.List` moduł ma tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ee822-253">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="ee822-254">Jest to przydatne, gdy wartości w module i funkcje mają nazwy, które mogą powodować konflikt z nazwami w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="ee822-254">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="ee822-255">Wymagających dostępu kwalifikowaną może znacznie zwiększyć długoterminowej utrzymanie i evolvability biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ee822-255">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="ee822-256">Dodawanie `[<AutoOpen>]` modułu dla atrybutu oznacza, że moduł zostanie otwarty po otwarciu zawierającego przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ee822-256">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="ee822-257">`[<AutoOpen>]` Atrybutu może być również stosowany do zestawu, aby wskazać moduł, który jest automatycznie otwierane w momencie odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee822-257">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="ee822-258">Na przykład biblioteki statystyki **MathsHeaven.Statistics** może zawierać `module MathsHeaven.Statistics.Operators` zawierający funkcje `erf` i `erfc`.</span><span class="sxs-lookup"><span data-stu-id="ee822-258">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="ee822-259">Jest uzasadnione oznaczyć ten moduł jako `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="ee822-259">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="ee822-260">Oznacza to, że `open MathsHeaven.Statistics` będzie także otworzyć ten moduł i przełączyć nazwy `erf` i `erfc` do zakresu.</span><span class="sxs-lookup"><span data-stu-id="ee822-260">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="ee822-261">Użycie innego dobrego `[<AutoOpen>]` dla modułów zawierających metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ee822-261">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="ee822-262">Nadużywać z `[<AutoOpen>]` potencjalnych klientów zanieczyszczonych przestrzeni nazw i atrybutu należy używać ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="ee822-262">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="ee822-263">Dla biblioteki określonej w określonych domenach, korzystać z `[<AutoOpen>]` może prowadzić do lepszego użyteczność.</span><span class="sxs-lookup"><span data-stu-id="ee822-263">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="ee822-264">Rozważ zdefiniowanie operatora elementów członkowskich w klasach, gdzie jest odpowiednia przy użyciu operatorów dobrze znanego</span><span class="sxs-lookup"><span data-stu-id="ee822-264">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="ee822-265">Czasami klas są używane do modelu matematyczne konstrukcje, takich jak wektory.</span><span class="sxs-lookup"><span data-stu-id="ee822-265">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="ee822-266">Jeśli domeny modelowanego dobrze znane operatory, definiując je jako członków do klasy wewnętrznej jest przydatne.</span><span class="sxs-lookup"><span data-stu-id="ee822-266">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="ee822-267">W tych wskazówkach odpowiada ogólne wskazówki .NET dla tych typów.</span><span class="sxs-lookup"><span data-stu-id="ee822-267">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="ee822-268">Jednak może być również ważne w F # kodowania, ponieważ dzięki temu te typy do użycia w połączeniu z F # funkcje i metody ograniczenia elementu członkowskiego, takich jak list.sumby —.</span><span class="sxs-lookup"><span data-stu-id="ee822-268">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="ee822-269">Należy rozważyć użycie compiledname — w celu dostarczenia. NET-przyjazna nazwa dla innych użytkowników języka .NET</span><span class="sxs-lookup"><span data-stu-id="ee822-269">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="ee822-270">Czasami warto nazw coś w jednym stylu dla konsumentów F # (takich jak statyczny element członkowski w małe litery, tak że pojawi się tak, jakby była funkcja powiązane z modułu), ale ma inny styl dla nazwy, gdy jest on skompilowany w zestawie.</span><span class="sxs-lookup"><span data-stu-id="ee822-270">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="ee822-271">Można użyć `[<CompiledName>]` atrybut do zapewnienia innego stylu z systemem innym niż kodzie języka F # korzystających z zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee822-271">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="ee822-272">Przy użyciu `[<CompiledName>]`, można użyć .NET konwencje nazewnictwa dla klientów z systemem innym niż język F # zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee822-272">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="ee822-273">Użyj przeciążenie metody dla funkcji członkowskiej, jeśli ten sposób zapewnia prostszy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="ee822-273">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="ee822-274">Przeciążenie metody jest zaawansowanym narzędziem do uproszczenia interfejs API, który może być konieczne wykonanie podobne funkcje, ale z różnymi opcjami lub argumentów.</span><span class="sxs-lookup"><span data-stu-id="ee822-274">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="ee822-275">W F # jest najczęściej do przeciążenia na liczbę argumentów niż typy argumentów.</span><span class="sxs-lookup"><span data-stu-id="ee822-275">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="ee822-276">Ukryj reprezentacje rekordu i typami Unii, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji</span><span class="sxs-lookup"><span data-stu-id="ee822-276">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="ee822-277">Unikaj ujawniania konkretnych reprezentacje obiektów.</span><span class="sxs-lookup"><span data-stu-id="ee822-277">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="ee822-278">Na przykład konkretnych reprezentacja <xref:System.DateTime> wartości nie została ujawniona przez zewnętrznych, publiczny interfejs API .NET projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ee822-278">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="ee822-279">Środowisko uruchomieniowe języka wspólnego w czasie wykonywania, wie, zatwierdzone implementację, która będzie używana w wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ee822-279">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="ee822-280">Jednak skompilowanego kodu nie sam wybierz zależności dotyczące konkretnych reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="ee822-280">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="ee822-281">Unikaj stosowania dziedziczenia implementacji rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="ee822-281">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="ee822-282">W języku F # jest rzadko używana implementacja dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="ee822-282">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="ee822-283">Ponadto hierarchii dziedziczenia mają złożonej i trudnej można zmienić w momencie nadejścia nowych wymagań w zakresie.</span><span class="sxs-lookup"><span data-stu-id="ee822-283">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="ee822-284">Implementacja dziedziczenia nadal istnieje w języku F # dla zgodności i rzadkich przypadkach, gdy to najlepsze rozwiązanie problemu, ale alternatywnych metod należy dążyć w programach F # podczas projektowania polimorfizm, takich jak implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ee822-284">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="ee822-285">Funkcja i element członkowski podpisów</span><span class="sxs-lookup"><span data-stu-id="ee822-285">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="ee822-286">Użyj spójnych kolekcji dla wartości zwracanych, gdy zwracany jest niewielka liczba wielu niepowiązanych wartości</span><span class="sxs-lookup"><span data-stu-id="ee822-286">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="ee822-287">Oto przykład przy użyciu spójnych kolekcji w zwracanego typu:</span><span class="sxs-lookup"><span data-stu-id="ee822-287">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="ee822-288">Dla zwracanych typów zawierający wiele składników lub składniki programu są związane z pojedynczej do zidentyfikowania jednostki, należy rozważyć użycie typu o nazwie zamiast spójnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ee822-288">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="ee822-289">Użyj `Async<T>` programowania asynchronicznego na granicach interfejsu API F #</span><span class="sxs-lookup"><span data-stu-id="ee822-289">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="ee822-290">Jeśli istnieje odpowiadająca mu Operacja synchroniczna o nazwie `Operation` zwracającą `T`, a następnie powinno być nazwanym operacji asynchronicznej `AsyncOperation` Jeśli zwróci ona `Async<T>` lub `OperationAsync` Jeśli zwróci ona `Task<T>`.</span><span class="sxs-lookup"><span data-stu-id="ee822-290">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="ee822-291">Często używanych typów .NET, które udostępniają metody Begin/End, warto rozważyć użycie `Async.FromBeginEnd` do zapisania metody rozszerzenia jako fasad zapewnienie F # async modelu programowania do tych interfejsów API architektury .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-291">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="ee822-292">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="ee822-292">Exceptions</span></span>

<span data-ttu-id="ee822-293">Wyjątki są wyjątkowych w .NET; oznacza to, że ich nie powinien wystąpić często w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ee822-293">Exceptions are exceptional in .NET; that is, they should not occur frequently at runtime.</span></span> <span data-ttu-id="ee822-294">Gdy tak robią, informacje, które zawierają jest przydatna.</span><span class="sxs-lookup"><span data-stu-id="ee822-294">When they do, the information they contain is valuable.</span></span> <span data-ttu-id="ee822-295">Wyjątki są podstawowe pojęcia pierwszej klasie .NET; Dlatego IT, następuje, które odpowiednią aplikację wyjątki należy używać jako części projektu interfejsu składnika.</span><span class="sxs-lookup"><span data-stu-id="ee822-295">Exceptions are a core first class concept of .NET; it hence follows that appropriate application of the Exceptions should be used as part of the design of the interface of a component.</span></span>

#### <a name="follow-the-net-guidelines-for-exceptions"></a><span data-ttu-id="ee822-296">Postępuj zgodnie z wytycznymi .NET dla wyjątków</span><span class="sxs-lookup"><span data-stu-id="ee822-296">Follow the .NET guidelines for exceptions</span></span>

<span data-ttu-id="ee822-297">[Zaleceń dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/exceptions.md) podać znakomity stosowania wyjątków w kontekście programowania .NET wszystkie.</span><span class="sxs-lookup"><span data-stu-id="ee822-297">The [.NET Library Design Guidelines](../../standard/design-guidelines/exceptions.md) give excellent advice on the use of exceptions in the context of all .NET programming.</span></span> <span data-ttu-id="ee822-298">Niektóre z tych wskazówek są następujące:</span><span class="sxs-lookup"><span data-stu-id="ee822-298">Some of these guidelines are as follows:</span></span>

* <span data-ttu-id="ee822-299">Nie używaj wyjątki przepływu sterowania.</span><span class="sxs-lookup"><span data-stu-id="ee822-299">Do not use exceptions for normal flow of control.</span></span> <span data-ttu-id="ee822-300">Mimo że ta metoda jest często używane w językach takich jak OCaml, jest podatne błędów i może być mało wydajne na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-300">Although this technique is often used in languages such as OCaml, it is bug-prone and can be inefficient on .NET.</span></span> <span data-ttu-id="ee822-301">Zamiast tego należy wziąć pod uwagę zwracanie `None` wartość do wskazania błędu, który jest wystąpieniem wspólnych lub oczekiwanego opcji.</span><span class="sxs-lookup"><span data-stu-id="ee822-301">Instead, consider returning a `None` option value to indicate a failure that is a common or expected occurrence.</span></span>

* <span data-ttu-id="ee822-302">Następnie należy udokumentować wyjątki zgłaszane przez składniki, gdy używana jest funkcja niepoprawnie.</span><span class="sxs-lookup"><span data-stu-id="ee822-302">Document exceptions thrown by your components when a function is used incorrectly.</span></span>

* <span data-ttu-id="ee822-303">Jeśli to możliwe, należy stosować istniejących wyjątków z przestrzeni nazw systemu.</span><span class="sxs-lookup"><span data-stu-id="ee822-303">Where possible, employ existing exceptions from the System namespaces.</span></span> <span data-ttu-id="ee822-304">Unikaj <xref:System.ApplicationException>, ale.</span><span class="sxs-lookup"><span data-stu-id="ee822-304">Avoid <xref:System.ApplicationException>, though.</span></span>

* <span data-ttu-id="ee822-305">Nie zgłaszają <xref:System.Exception> kiedy zostanie escape, aby kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee822-305">Do not throw <xref:System.Exception> when it will escape to user code.</span></span> <span data-ttu-id="ee822-306">Dotyczy to również unikając stosowania `failwith`, `failwithf`, które są przydatne funkcje, użyj skrypty i kod opracowywane, ale powinna zostać usunięta z biblioteki kodzie języka F # na rzecz zgłaszanie więcej określony typ wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ee822-306">This includes avoiding the use of `failwith`, `failwithf`, which are handy functions for use in scripting and for code under development, but should be removed from F# library code in favor of throwing a more specific exception type.</span></span>

* <span data-ttu-id="ee822-307">Użyj `nullArg`, `invalidArg`, i `invalidOp` jako mechanizm throw <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, i <xref:System.InvalidOperationException> w odpowiednim przypadku.</span><span class="sxs-lookup"><span data-stu-id="ee822-307">Use `nullArg`, `invalidArg`, and `invalidOp` as the mechanism to throw <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, and <xref:System.InvalidOperationException> when appropriate.</span></span>

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a><span data-ttu-id="ee822-308">Rozważ użycie wartości opcji dla typy zwracane, gdy błąd nie jest kodem scenariusza</span><span class="sxs-lookup"><span data-stu-id="ee822-308">Consider using option values for return types when failure is not an exceptional scenario</span></span>

<span data-ttu-id="ee822-309">Podejście .NET do wyjątków jest, czy powinien być "wyjątkowych;" oznacza to, że ich powinna występować stosunkowo rzadko.</span><span class="sxs-lookup"><span data-stu-id="ee822-309">The .NET approach to exceptions is that they should be “exceptional”; that is, they should occur relatively infrequently.</span></span> <span data-ttu-id="ee822-310">Jednak niektóre operacje (np. wyszukiwanie tabeli) może się nie powieść często.</span><span class="sxs-lookup"><span data-stu-id="ee822-310">However, some operations (for example, searching a table) may fail frequently.</span></span> <span data-ttu-id="ee822-311">Wartości opcji F # są doskonałym sposobem reprezentują typy zwracane występujące w tych operacji.</span><span class="sxs-lookup"><span data-stu-id="ee822-311">F# option values are an excellent way to represent the return types of these operations.</span></span> <span data-ttu-id="ee822-312">Te operacje tradycyjnie rozpoczyna się od prefiksu nazwy "try":</span><span class="sxs-lookup"><span data-stu-id="ee822-312">These operations conventionally start with the name prefix “try”:</span></span>

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a><span data-ttu-id="ee822-313">Elementy członkowskie rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="ee822-313">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="ee822-314">Dokładnie zastosować F # elementy członkowskie rozszerzeń w języku F #-do-F # składniki</span><span class="sxs-lookup"><span data-stu-id="ee822-314">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="ee822-315">Elementy członkowskie rozszerzeń F # powinien zwykle można używać tylko dla operacji, które znajdują się w zamknięcia wewnętrzne operacje związane z typem w większości jej trybów użycia.</span><span class="sxs-lookup"><span data-stu-id="ee822-315">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="ee822-316">Jeden użycia ma na celu dostarczenie interfejsów API, które są bardziej idiomatyczne do F # dla różnych typów .NET:</span><span class="sxs-lookup"><span data-stu-id="ee822-316">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="ee822-317">Typy Unii</span><span class="sxs-lookup"><span data-stu-id="ee822-317">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="ee822-318">Użyj rozłączne zamiast klasy hierarchie strukturze drzewa danych</span><span class="sxs-lookup"><span data-stu-id="ee822-318">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="ee822-319">Struktury drzewa są zdefiniowane cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="ee822-319">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="ee822-320">Jest to nieodpowiednich z dziedziczenia, ale elegancki z Suma rozłączna Unii.</span><span class="sxs-lookup"><span data-stu-id="ee822-320">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="ee822-321">Reprezentacja drzewa danych z unie Suma rozłączna — umożliwia również korzystać z kompletności w dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="ee822-321">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="ee822-322">Użyj `[<RequireQualifiedAccess>]` złożenia typów, których nazwy nie są wystarczająco unikatowe</span><span class="sxs-lookup"><span data-stu-id="ee822-322">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="ee822-323">Może się okazać się w domenie, gdzie tej samej nazwie jest nazwą najlepsze dla różnych rzeczy, takich jak przypadków Unii Suma rozłączna.</span><span class="sxs-lookup"><span data-stu-id="ee822-323">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="ee822-324">Można użyć `[<RequireQualifiedAccess>]` do odróżnienia nazwy, aby uniknąć wyzwalania błędy myląca ze względu na przesłanianie zależne kolejność `open` — instrukcje</span><span class="sxs-lookup"><span data-stu-id="ee822-324">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="ee822-325">Ukryj reprezentacje rozłączne dla binarnego zgodne interfejsów API, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji</span><span class="sxs-lookup"><span data-stu-id="ee822-325">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="ee822-326">Typy Unii jest zależne od F # dopasowywanie do wzorca formularze zwięzły modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="ee822-326">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="ee822-327">Jak wspomniano wcześniej, należy unikać ujawniania danych konkretne oświadczenia, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji.</span><span class="sxs-lookup"><span data-stu-id="ee822-327">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="ee822-328">Na przykład reprezentację rozróżnianą Unię mogą być ukryte za pomocą deklaracji prywatny lub wewnętrzny lub przy użyciu pliku podpisu.</span><span class="sxs-lookup"><span data-stu-id="ee822-328">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="ee822-329">Jeśli przyrostu ujawnieniem rozłączne, może być trudne do wersji biblioteki bez przerywania kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee822-329">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="ee822-330">Zamiast tego należy wziąć pod uwagę ujawniania co najmniej jeden aktywne wzorce umożliwiające wzorzec dopasowany wartości tego typu.</span><span class="sxs-lookup"><span data-stu-id="ee822-330">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="ee822-331">Wzorce aktywne Podaj inny sposób udostępnić F # konsumentów wzorzec dopasowany unikając bezpośrednio udostępnianie typów złożenia języka F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-331">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="ee822-332">Wbudowane funkcje i ograniczenia elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="ee822-332">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="ee822-333">Zdefiniuj ogólnego algorytmów liczbowych za pomocą funkcji śródwierszowych ograniczenia elementu członkowskiego domyślnych i statycznie rozwiązywane typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="ee822-333">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="ee822-334">Ograniczenia elementu członkowskiego arytmetyczne i F # porównania ograniczenia są standardowe rozwiązanie dla programowania w języku F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-334">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="ee822-335">Rozważmy na przykład następujący kod:</span><span class="sxs-lookup"><span data-stu-id="ee822-335">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="ee822-336">Typ tej funkcji jest następujący:</span><span class="sxs-lookup"><span data-stu-id="ee822-336">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="ee822-337">Jest to funkcja odpowiednie dla publiczny interfejs API w bibliotece matematycznych.</span><span class="sxs-lookup"><span data-stu-id="ee822-337">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="ee822-338">Należy unikać używania ograniczenia elementu członkowskiego do symulowania typu klasy i wpisując kaczka</span><span class="sxs-lookup"><span data-stu-id="ee822-338">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="ee822-339">Można symulować "kacze, wpisując" za pomocą ograniczenia elementu członkowskiego F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-339">It is possible to simulate “duck typing” using F# member constraints.</span></span> <span data-ttu-id="ee822-340">Jednak elementów członkowskich, które należy użyć tego ogólne nie stosuje się w języku F #-do-biblioteki projektów F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-340">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="ee822-341">Jest tak, ponieważ na podstawie nieznane lub niestandardową ograniczeń niejawne projektów biblioteki mogą spowodować sztywne i wiązanej do jednej konkretnej framework wzorzec staną się kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee822-341">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="ee822-342">Ponadto istnieje szansa, że intensywnie korzysta z ograniczenia elementu członkowskiego w ten sposób może spowodować kompilacji bardzo dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="ee822-342">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="ee822-343">Definicje — operator</span><span class="sxs-lookup"><span data-stu-id="ee822-343">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="ee822-344">Unikaj definiowania niestandardowych symboliczne operatory</span><span class="sxs-lookup"><span data-stu-id="ee822-344">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="ee822-345">Operatory niestandardowe są niezbędne w niektórych sytuacjach i są bardzo przydatne notational urządzeniami w ramach dużą porcję kod implementacji.</span><span class="sxs-lookup"><span data-stu-id="ee822-345">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="ee822-346">Dla nowych użytkowników biblioteki funkcji o nazwie często są łatwiejsze w użyciu.</span><span class="sxs-lookup"><span data-stu-id="ee822-346">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="ee822-347">Ponadto niestandardowych operatory symboliczne może być trudne do dokumentu, a użytkownicy uważają trudniej uzyskać pomoc dotyczącą operatorów, ze względu na ograniczenia istniejącego w IDE i wyszukiwania aparaty wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ee822-347">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="ee822-348">W związku z tym najlepiej publikowanie z funkcji jako nazwane funkcje i elementy członkowskie, a ponadto ujawnia operatory dla tej funkcji tylko wtedy, gdy przeważają korzyści notational dokumentacji i kognitywnych koszt o ich.</span><span class="sxs-lookup"><span data-stu-id="ee822-348">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="ee822-349">Jednostki miary</span><span class="sxs-lookup"><span data-stu-id="ee822-349">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="ee822-350">Starannie Użyj jednostki miary dla typów dodanych bezpieczeństwa w kodzie języka F #</span><span class="sxs-lookup"><span data-stu-id="ee822-350">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="ee822-351">Dodatkowe informacje pisania jednostki miary wymazaniu widzianego innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-351">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="ee822-352">Należy pamiętać, że składniki platformy .NET, narzędzia i odbicie Zobacz typy sieci SAN jednostki.</span><span class="sxs-lookup"><span data-stu-id="ee822-352">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="ee822-353">Na przykład C# będą widzieli `float` zamiast `float<kg>`.</span><span class="sxs-lookup"><span data-stu-id="ee822-353">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="ee822-354">Skróty typów</span><span class="sxs-lookup"><span data-stu-id="ee822-354">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="ee822-355">Starannie użyć skróty typów, aby uprościć kodzie języka F #</span><span class="sxs-lookup"><span data-stu-id="ee822-355">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="ee822-356">Składniki platformy .NET, narzędzia i odbicie nie będą widzieć skróconej nazwy dla typów.</span><span class="sxs-lookup"><span data-stu-id="ee822-356">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="ee822-357">Skróty typów znaczne użycie można również ustawić domeny są wyświetlane faktycznie jest bardziej złożone niż, które można mylić konsumentów.</span><span class="sxs-lookup"><span data-stu-id="ee822-357">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="ee822-358">Unikaj skrótów typu typy publiczne, których elementy członkowskie i właściwości powinny być bardzo różni się od tych, które są dostępne w skracanym typie</span><span class="sxs-lookup"><span data-stu-id="ee822-358">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="ee822-359">W takim przypadku skracanym typie ujawnia zbyt dużo o reprezentację rzeczywisty typ jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="ee822-359">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="ee822-360">Zamiast tego należy wziąć pod uwagę zawijania skrót typu klasy lub jeden przypadek Unii rozłącznych (lub, gdy wydajność jest niezbędne, należy rozważyć użycie typu struct opakowywać skrót).</span><span class="sxs-lookup"><span data-stu-id="ee822-360">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="ee822-361">Na przykład jest kuszące do definiowania wielu mapy w szczególnych przypadkach F # mapy, na przykład:</span><span class="sxs-lookup"><span data-stu-id="ee822-361">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="ee822-362">Jednak operacje logiczne kropkowego w tym typie nie są takie same operacje na mapie — na przykład, jest uzasadnione, że operator wyszukiwania mapy. Pusta lista, jeśli klucz nie ma w słowniku zamiast generowanie wyjątków [klucza] powrotu.</span><span class="sxs-lookup"><span data-stu-id="ee822-362">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="ee822-363">Wytyczne dotyczące biblioteki do użycia z innymi językami .NET</span><span class="sxs-lookup"><span data-stu-id="ee822-363">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="ee822-364">Podczas projektowania biblioteki do użycia z innymi językami .NET, ważne jest, aby stosować się do [zaleceń dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee822-364">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="ee822-365">W tym dokumencie biblioteki te są oznaczone jako podstawowego bibliotek .NET, a nie F #-ukierunkowane bibliotek, które używają F # konstruuje bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="ee822-365">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="ee822-366">Projektowanie podstawowego bibliotek .NET oznacza zapewnienie znanego i idiomatyczne interfejsów API zgodne z pozostałą częścią programu .NET Framework, minimalizując użycie języka F #-konstrukcje określonych w publiczny interfejs API.</span><span class="sxs-lookup"><span data-stu-id="ee822-366">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="ee822-367">W poniższych sekcjach opisano reguły.</span><span class="sxs-lookup"><span data-stu-id="ee822-367">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="ee822-368">Namespace i typu projektu (dla biblioteki do użycia z innymi językami .NET)</span><span class="sxs-lookup"><span data-stu-id="ee822-368">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="ee822-369">Dotyczą konwencje nazewnictwa .NET publiczny interfejs API składników</span><span class="sxs-lookup"><span data-stu-id="ee822-369">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="ee822-370">Należy zwrócić szczególną uwagę na użycie skróconej nazwy i wskazówkami dotyczącymi .NET wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="ee822-370">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="ee822-371">Użyj przestrzeni nazw, typy i składniki jako podstawowy struktura organizacyjna składników</span><span class="sxs-lookup"><span data-stu-id="ee822-371">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="ee822-372">Wszystkie pliki zawierające publiczny funkcji powinny rozpoczynać się od `namespace` deklaracji i tylko jednostek publicznych w przestrzeniach nazw powinny być typów.</span><span class="sxs-lookup"><span data-stu-id="ee822-372">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="ee822-373">Nie należy używać modułów F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-373">Do not use F# modules.</span></span>

<span data-ttu-id="ee822-374">Użyj niepublicznych modułów do przechowywania w kodzie, typy narzędzi i funkcji narzędzia.</span><span class="sxs-lookup"><span data-stu-id="ee822-374">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="ee822-375">Statyczne typy powinny mieć pierwszeństwo modułów, jak pozwalają one na przyszłe zmiany interfejsu API do używania przeciążania i innych interfejs API .NET zagadnienia dotyczące projektowania, które nie mogą być używane w modułach F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-375">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="ee822-376">Na przykład zamiast następujące publiczny interfejs API:</span><span class="sxs-lookup"><span data-stu-id="ee822-376">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="ee822-377">Zamiast tego rozważ:</span><span class="sxs-lookup"><span data-stu-id="ee822-377">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="ee822-378">Użyć typy rekordów F # w waniliowe interfejsów API architektury .NET, jeśli projekt typów nie będą rozwijać</span><span class="sxs-lookup"><span data-stu-id="ee822-378">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="ee822-379">Typy rekordów F # kompilacji do prostą klasę platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-379">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="ee822-380">Są to odpowiednie dla niektórych typów prostych, stabilna w interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="ee822-380">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="ee822-381">Należy rozważyć użycie `[<NoEquality>]` i `[<NoComparison>]` atrybuty do pomijania automatyczne generowanie interfejsów.</span><span class="sxs-lookup"><span data-stu-id="ee822-381">You should consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="ee822-382">Również unikać pola rekordu modyfikowalną waniliowe interfejsów API architektury .NET jako te ujawnia pole publiczne.</span><span class="sxs-lookup"><span data-stu-id="ee822-382">Also avoid using mutable record fields in vanilla .NET APIs as these exposes a public field.</span></span> <span data-ttu-id="ee822-383">Zawsze należy rozważyć, czy klasa zapewni bardziej elastycznych opcji dla przyszłego rozwoju interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="ee822-383">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="ee822-384">Na przykład następujący kod F # przedstawia publiczny interfejs API do konsumenta C#:</span><span class="sxs-lookup"><span data-stu-id="ee822-384">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="ee822-385">F #:</span><span class="sxs-lookup"><span data-stu-id="ee822-385">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

<span data-ttu-id="ee822-386">C#:</span><span class="sxs-lookup"><span data-stu-id="ee822-386">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="ee822-387">Ukryj reprezentację typów F # Unii w waniliowe interfejsów API architektury .NET</span><span class="sxs-lookup"><span data-stu-id="ee822-387">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="ee822-388">Typy Unii języka F # nie są powszechnie stosowane poza granicami składnika, nawet w przypadku F #-do-F # kodowania.</span><span class="sxs-lookup"><span data-stu-id="ee822-388">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="ee822-389">Są one urządzenia znakomity wykonania, gdy używana wewnętrznie w składniki i biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ee822-389">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="ee822-390">Podczas projektowania waniliowe interfejs API .NET, należy wziąć pod uwagę ukrywanie reprezentacja typu union za pomocą deklaracji prywatnych lub plik podpisu.</span><span class="sxs-lookup"><span data-stu-id="ee822-390">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="ee822-391">Może również rozszerzyć typów, które używają reprezentację Unii z elementami członkowskimi zapewnienie do żądanej wewnętrznie. Interfejs API udostępnianych w sieci.</span><span class="sxs-lookup"><span data-stu-id="ee822-391">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="ee822-392">Projekt graficznego interfejsu użytkownika i inne składniki przy użyciu wzorce projektowe platformy</span><span class="sxs-lookup"><span data-stu-id="ee822-392">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="ee822-393">Wiele różnych platform są dostępne w ramach platformy .NET, takie jak WinForms, WPF i platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-393">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="ee822-394">Konwencje nazewnictwa i projektu dla każdego powinien być używany w przypadku projektowania składniki do użycia w tych platform.</span><span class="sxs-lookup"><span data-stu-id="ee822-394">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="ee822-395">Na przykład dla WPF programowania, przyjmuje WPF wzorce projektowe dla klasy, z którymi projektowania.</span><span class="sxs-lookup"><span data-stu-id="ee822-395">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="ee822-396">Dla modeli w programowaniu interfejsu użytkownika, użyj wzorce projektowe, takich jak zdarzenia i kolekcje oparte na powiadomienie, takich jak znaleźć w <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="ee822-396">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="ee822-397">Projekt obiektu i element członkowski (dla biblioteki do użycia z innymi językami .NET)</span><span class="sxs-lookup"><span data-stu-id="ee822-397">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="ee822-398">Umożliwia ujawnia zdarzenia platformy .NET w clievent — atrybut</span><span class="sxs-lookup"><span data-stu-id="ee822-398">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="ee822-399">Utworzyć `DelegateEvent` z określonych .NET przekazać typ, który pobiera obiekt i `EventArgs` (zamiast `Event`, który używa `FSharpHandler` typu domyślnie), aby zdarzenia są publikowane w taki sposób zapoznać się z innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-399">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a><span data-ttu-id="ee822-400">Udostępnianie operacji asynchronicznych jako metody zwracające zadania .NET</span><span class="sxs-lookup"><span data-stu-id="ee822-400">Expose asynchronous operations as methods which return .NET tasks</span></span>

<span data-ttu-id="ee822-401">Zadania są używane w środowisku .NET do reprezentowania active obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="ee822-401">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="ee822-402">Zadania są zwykle składu mniej niż F # `Async<T>` obiektów, ponieważ reprezentuje zadania "już wykonuje" i nie może być jednocześnie który równoległych utworzenia lub który Ukryj propagacji sygnały anulowania oraz innych Parametry kontekstowe.</span><span class="sxs-lookup"><span data-stu-id="ee822-402">Tasks are in general less compositional than F# `Async<T>` objects, since they represent “already executing” tasks and can’t be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="ee822-403">Mimo to, metody zwracające zadania są standardowe reprezentację programowanie asynchroniczne na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-403">However, despite this, methods which return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="ee822-404">Często będą również chcesz zaakceptować token anulowania explicit:</span><span class="sxs-lookup"><span data-stu-id="ee822-404">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="ee822-405">Użyj typów delegata .NET zamiast funkcji typów F #</span><span class="sxs-lookup"><span data-stu-id="ee822-405">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="ee822-406">W tym miejscu "typów F # funkcja" oznacza "strzałka" typy, takich jak `int -> int`.</span><span class="sxs-lookup"><span data-stu-id="ee822-406">Here “F# function types” mean “arrow” types like `int -> int`.</span></span>

<span data-ttu-id="ee822-407">Zamiast tego:</span><span class="sxs-lookup"><span data-stu-id="ee822-407">Instead of this:</span></span>

```fsharp
member this.Transform(f:int->int) =
    ...
```

<span data-ttu-id="ee822-408">wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ee822-408">Do this:</span></span>

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

<span data-ttu-id="ee822-409">Typ funkcji języka F # jest wyświetlany jako `class FSharpFunc<T,U>` do innych języków .NET i mniej odpowiedni język funkcji i narzędzi które zrozumieć typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="ee822-409">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understand delegate types.</span></span> <span data-ttu-id="ee822-410">Podczas tworzenia metody wyższego rzędu przeznaczonych dla platformy .NET Framework 3.5 lub nowszego, `System.Func` i `System.Action` delegatów są prawa interfejsów API do publikowania umożliwiają deweloperom korzystać z tych interfejsów API w sposób niskim tarcia .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-410">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="ee822-411">(Jeśli systemem docelowym jest środowisko .NET Framework 2.0, typy zdefiniowane w systemie delegata są bardziej ograniczone; Rozważ użycie typów delegatów wstępnie zdefiniowane, takich jak `System.Converter<T,U>` lub określenie typu określonego delegata.)</span><span class="sxs-lookup"><span data-stu-id="ee822-411">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="ee822-412">Na stronie Przerzucanie .NET delegatów nie są fizycznych w F # — ukierunkowane bibliotek (zobacz następną sekcję w F #-ukierunkowane bibliotek).</span><span class="sxs-lookup"><span data-stu-id="ee822-412">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="ee822-413">W związku z tym wspólnej strategii wdrażania, podczas tworzenia metody wyższego rzędu do bibliotek .NET podstawowego ma tworzyć wszystkie wdrożenia przy użyciu funkcji typów F #, a następnie utwórz publiczny interfejs API, używanie delegatów jako alokowania fasad nad rzeczywiste F # Implementacja.</span><span class="sxs-lookup"><span data-stu-id="ee822-413">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="ee822-414">Użyj wzorca TryGetValue zamiast zwracać wartości opcji F # i preferowane jest przeciążenie metody do uwzględnienia wartości opcji F # jako argumenty</span><span class="sxs-lookup"><span data-stu-id="ee822-414">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="ee822-415">Lepsze są typowe wzorce użycia dla typu opcji F # w interfejsów API zaimplementowano w waniliowe techniki projektowania interfejsów API platformy .NET przy użyciu platformy .NET standard.</span><span class="sxs-lookup"><span data-stu-id="ee822-415">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="ee822-416">Zamiast zwracać wartość opcji F #, należy rozważyć użycie zwracany typ bool plus parametru wyjściowego tak jak wzorzec "TryGetValue".</span><span class="sxs-lookup"><span data-stu-id="ee822-416">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="ee822-417">I zamiast przyjmowania wartości opcji F # jako parametry, należy rozważyć użycie przeciążenie metody lub argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="ee822-417">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="ee822-418">Użyj interfejsu kolekcji .NET typy IEnumerable\<T\> i IDictionary\<klucza, wartość\> dla parametrów i zwracanych wartości</span><span class="sxs-lookup"><span data-stu-id="ee822-418">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="ee822-419">Unikaj używania kolekcji konkretnych typów, takich jak .NET tablice `T[]`, typów F # `list<T>`, `Map<Key,Value>` i `Set<T>`, oraz konkretnych kolekcji .NET typów, takie jak `Dictionary<Key,Value>`.</span><span class="sxs-lookup"><span data-stu-id="ee822-419">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="ee822-420">Wytyczne dotyczące projektowania biblioteki .NET mają dobrej porad dotyczących kiedy należy używać różnych typów kolekcji, takie jak `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="ee822-420">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="ee822-421">Niektóre korzystanie z tablic (`T[]`) jest akceptowany w pewnych okolicznościach, na podstawie wydajności.</span><span class="sxs-lookup"><span data-stu-id="ee822-421">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="ee822-422">Należy pamiętać, że szczególnie `seq<T>` jest po prostu F # alias dla `IEnumerable<T>`, i w związku z tym seq jest często odpowiedniego typu dla waniliowe interfejsu API platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-422">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="ee822-423">Zamiast tego języka F # zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="ee822-423">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names : string list) =
    ...
```

<span data-ttu-id="ee822-424">Użyj sekwencji F #:</span><span class="sxs-lookup"><span data-stu-id="ee822-424">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="ee822-425">Użyj tego typu jednostki tylko typ danych wejściowych metody można zdefiniować metody zero argumentu lub jako jedynym zwracany typ celu zdefiniowania metody zwracające typ void</span><span class="sxs-lookup"><span data-stu-id="ee822-425">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="ee822-426">Unikaj innych celów tego typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="ee822-426">Avoid other uses of the unit type.</span></span> <span data-ttu-id="ee822-427">Są to dobry:</span><span class="sxs-lookup"><span data-stu-id="ee822-427">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

<span data-ttu-id="ee822-428">To jest nieprawidłowy:</span><span class="sxs-lookup"><span data-stu-id="ee822-428">This is bad:</span></span>

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="ee822-429">Sprawdź, czy wartości null na podstawowego granice interfejs API .NET</span><span class="sxs-lookup"><span data-stu-id="ee822-429">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="ee822-430">F # w kodzie zwykle ma mniejszą liczbę wartości null z powodu wzorce projektowe niezmienne i ograniczenia użytkowania literałów wartości null dla typów F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-430">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="ee822-431">Innymi językami .NET jest często używane jako wartości null częściej.</span><span class="sxs-lookup"><span data-stu-id="ee822-431">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="ee822-432">W związku z tym F # kod, który jest ujawniany przez waniliowe interfejs API .NET należy Sprawdź parametry dla wartości null na granicy interfejsu API i uniemożliwić te wartości głębiej otrzymywanych kod implementacji F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-432">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="ee822-433">`isNull` Funkcji lub dopasowania wzorca w `null` użyciem wzorca.</span><span class="sxs-lookup"><span data-stu-id="ee822-433">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="ee822-434">Unikaj używania krotek jako wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="ee822-434">Avoid using tuples as return values</span></span>

<span data-ttu-id="ee822-435">Zamiast tego preferowane zwracających Typ nazwany, zawierający dane zagregowane lub za pomocą parametrów out zwraca wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="ee822-435">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="ee822-436">Istnieje spójne kolekcje i struktury spójnych kolekcji w programie .NET (co obejmuje obsługę języka C# dla struktury krotek) one najczęściej nie zapewnia interfejsu API idealne i oczekiwany dla deweloperów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-436">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="ee822-437">Unikaj używania currying parametrów</span><span class="sxs-lookup"><span data-stu-id="ee822-437">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="ee822-438">Zamiast tego należy użyć .NET konwencji wywoływania ``Method(arg1,arg2,…,argN)``.</span><span class="sxs-lookup"><span data-stu-id="ee822-438">Instead, use .NET calling conventions ``Method(arg1,arg2,…,argN)``.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="ee822-439">Porada: Jeśli projektujesz biblioteki do użycia z dowolnego języka .NET, to nie ma nie zastąpi faktycznie wykonywania niektórych eksperymentalne C# i Visual Basic programowania upewnij się, że bibliotek "działanie po prawej" z tych języków.</span><span class="sxs-lookup"><span data-stu-id="ee822-439">Tip: If you’re designing libraries for use from any .NET language, then there’s no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="ee822-440">Aby upewnić się, że biblioteki i ich dokumentacji są wyświetlane zgodnie z oczekiwaniami do deweloperów umożliwia także narzędzi, takich jak .NET reflektora i przeglądarki obiektów Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ee822-440">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="ee822-441">Dodatek</span><span class="sxs-lookup"><span data-stu-id="ee822-441">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="ee822-442">Przykład end-to-end projektowania kodzie języka F # do użytku przez innych języków .NET</span><span class="sxs-lookup"><span data-stu-id="ee822-442">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="ee822-443">Należy wziąć pod uwagę następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="ee822-443">Consider the following class:</span></span>

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

<span data-ttu-id="ee822-444">Wnioskowany Typ F # tej klasy jest następujący:</span><span class="sxs-lookup"><span data-stu-id="ee822-444">The inferred F# type of this class is as follows:</span></span>

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

<span data-ttu-id="ee822-445">Spójrzmy na sposób wyświetlania tego typu F # do programisty, przy użyciu innego języka .NET.</span><span class="sxs-lookup"><span data-stu-id="ee822-445">Let’s take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="ee822-446">Na przykład przybliżonej C# "podpisu" wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="ee822-446">For example, the approximate C# “signature” is as follows:</span></span>

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

<span data-ttu-id="ee822-447">Istnieje kilka ważnych kwestii do uwagi dotyczące sposobu F # reprezentuje konstrukcje tutaj.</span><span class="sxs-lookup"><span data-stu-id="ee822-447">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="ee822-448">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ee822-448">For example:</span></span>

* <span data-ttu-id="ee822-449">Metadane, takie jak nazwy argumentów została zachowana.</span><span class="sxs-lookup"><span data-stu-id="ee822-449">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="ee822-450">F # metod, które przyjmują dwóch argumentów stają się C# metod, które przyjmują dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="ee822-450">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="ee822-451">Funkcje i list stają się odwołania do odpowiednie typy w bibliotece języka F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-451">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="ee822-452">Poniższy kod przedstawia sposób Dostosuj ten kod, aby uwzględnić te czynności.</span><span class="sxs-lookup"><span data-stu-id="ee822-452">The following code shows how to adjust this code to take these things into account.</span></span>

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

<span data-ttu-id="ee822-453">Wnioskowany Typ F # kodu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="ee822-453">The inferred F# type of the code is as follows:</span></span>

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

<span data-ttu-id="ee822-454">Podpis C# jest teraz w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ee822-454">The C# signature is now as follows:</span></span>

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

<span data-ttu-id="ee822-455">Poprawki wprowadzone do przygotowania tego typu do użycia jako część podstawowego biblioteki .NET są następujące:</span><span class="sxs-lookup"><span data-stu-id="ee822-455">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="ee822-456">Dostosowana kilka nazw: `Point1`, `n`, `l`, i `f` stał się `RadialPoint`, `count`, `factor`, i `transform`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="ee822-456">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="ee822-457">Używany typ zwracany `seq<RadialPoint>` zamiast `RadialPoint list` zmieniając konstruowania listy przy użyciu `[ ... ]` je przy użyciu konstrukcji sekwencji `IEnumerable<RadialPoint>`.</span><span class="sxs-lookup"><span data-stu-id="ee822-457">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="ee822-458">Używany typ delegata .NET `System.Func` zamiast typem funkcji języka F #.</span><span class="sxs-lookup"><span data-stu-id="ee822-458">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="ee822-459">Dzięki temu można znacznie wrażeń zużyje w kodzie języka C#.</span><span class="sxs-lookup"><span data-stu-id="ee822-459">This makes it far nicer to consume in C# code.</span></span>
