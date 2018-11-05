---
title: 'F # składnika wytyczne dotyczące projektowania'
description: 'Dowiedz się, zalecenia dotyczące pisania F # składników przeznaczonych do użytku przez inne obiekty wywołujące.'
ms.date: 05/14/2018
ms.openlocfilehash: 446cba0f810af9517b655ef5741ddf7a919676d5
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43488290"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="d584e-103">F # składnika wytyczne dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="d584e-103">F# component design guidelines</span></span>

<span data-ttu-id="d584e-104">W tym dokumencie to zestaw składników wytycznych projektowych dla języka F # programowania, w oparciu F # składnika wytycznych projektowych, wersja 14, Microsoft Research oraz [inna wersja](https://fsharp.org/specs/component-design-guidelines/) pierwotnie nadzorowane i obsługiwane przez F # Software Foundation.</span><span class="sxs-lookup"><span data-stu-id="d584e-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and [another version](https://fsharp.org/specs/component-design-guidelines/) originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="d584e-105">W tym dokumencie przyjęto założenie, że czytelnik zna programowanie F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="d584e-106">Wiele dzięki społeczność języka F # ich wkład i przydatne opinie na temat różnych wersji tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="d584e-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="d584e-107">Omówienie</span><span class="sxs-lookup"><span data-stu-id="d584e-107">Overview</span></span>

<span data-ttu-id="d584e-108">W tym dokumencie patrzy na niektórych problemów związanych z F # składnika projektowania i kodowania.</span><span class="sxs-lookup"><span data-stu-id="d584e-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="d584e-109">Składnik może oznaczać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d584e-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="d584e-110">Warstwy w projekcie języka F #, zawierającej klientów zewnętrznych w ramach tego projektu.</span><span class="sxs-lookup"><span data-stu-id="d584e-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="d584e-111">Biblioteka przeznaczone do użytku przez kod F # poza granicami zestawu.</span><span class="sxs-lookup"><span data-stu-id="d584e-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="d584e-112">Biblioteka przeznaczonych do użycia za pomocą dowolnego języka platformy .NET poza granicami zestawu.</span><span class="sxs-lookup"><span data-stu-id="d584e-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="d584e-113">Biblioteka przeznaczone do dystrybucji za pośrednictwem repozytorium pakietów, takich jak [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="d584e-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="d584e-114">Postępuj zgodnie z metod opisanych w tym artykule [pięć zasadami dobrej kodzie języka F #](index.md#five-principles-of-good-f-code), dlatego korzystanie z obu funkcjonalności i obiekt programowania zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="d584e-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="d584e-115">Niezależnie od tego, metodologii składników i biblioteki projektanta twarzy szereg problemów praktycznych i prosaic podczas próby jednostki interfejsu API, który jest najłatwiej jest używany przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="d584e-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="d584e-116">Sumienia stosowania [wytyczne dotyczące projektowania biblioteki .NET](../../standard/design-guidelines/index.md) kierowania do tworzenia spójny zestaw interfejsów API, które są przyjemne korzystać.</span><span class="sxs-lookup"><span data-stu-id="d584e-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="d584e-117">Ogólne wskazówki</span><span class="sxs-lookup"><span data-stu-id="d584e-117">General guidelines</span></span>

<span data-ttu-id="d584e-118">Istnieje kilka universal wskazówki, które dotyczą bibliotek F #, niezależnie od odbiorców dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d584e-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="d584e-119">Dowiedz się, wytyczne dotyczące projektowania w bibliotece platformy .NET</span><span class="sxs-lookup"><span data-stu-id="d584e-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="d584e-120">Niezależnie od rodzaju F # kodowania, którą wykonujesz, jest przydatna dla ma praktyczną wiedzę na temat [wytyczne dotyczące projektowania biblioteki .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="d584e-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="d584e-121">Większość innych F # programistów .NET będzie należy zapoznać się z tymi wytycznymi i oczekują kodu platformy .NET, które są zgodne z nich.</span><span class="sxs-lookup"><span data-stu-id="d584e-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="d584e-122">Wytyczne dotyczące projektowania dla biblioteki .NET zapewniają ogólne wskazówki dotyczące nazewnictwa, projektowanie klas i interfejsów, projekt elementu członkowskiego (właściwości, metody, zdarzenia itp.) i inne i są przydatne, pierwszy punkt odniesienia dla różnych wskazówki dotyczące projektowania.</span><span class="sxs-lookup"><span data-stu-id="d584e-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="d584e-123">Dodaj komentarze dokumentacji XML w kodzie</span><span class="sxs-lookup"><span data-stu-id="d584e-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="d584e-124">Dokumentacja XML w publicznych interfejsach API upewnij się, że użytkownicy będą mogli uzyskać doskonałe Intellisense i szybkich informacji podczas tych typów i elementów członkowskich i Włącz tworzenie dokumentacji plików biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d584e-124">XML documentation on public APIs ensure that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="d584e-125">Zobacz [dokumentacji XML](../language-reference/xml-documentation.md) o różne tagi xml, które mogą służyć do dodatkową marżę w ramach xmldoc komentarzy.</span><span class="sxs-lookup"><span data-stu-id="d584e-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

<span data-ttu-id="d584e-126">Możesz użyć albo komentarze XML krótka (`/// comment`), lub standardowych komentarzy XML (`///<summary>comment</summary>`).</span><span class="sxs-lookup"><span data-stu-id="d584e-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="d584e-127">Należy wziąć pod uwagę przy użyciu plików jawne podpisu (.fsi) dla biblioteki stabilny, jak i składnika interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d584e-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="d584e-128">Za pomocą jawnego podpisów plików w bibliotece F # zawiera zwięzły podsumowanie publicznego interfejsu API, który zarówno pomaga zapewnić, że możesz znać powierzchni publicznej biblioteki, a także umożliwia czystą separacji między publiczną dokumentację i wewnętrzne Szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="d584e-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which both helps to ensure that you know the full public surface of your library, as well as provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="d584e-129">Należy pamiętać, pliki podpisów dodać zajmowania się do zmiany publicznego interfejsu API, wymagając od zmian w plikach implementacji i podpis.</span><span class="sxs-lookup"><span data-stu-id="d584e-129">Note that signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="d584e-130">W rezultacie plików sygnatur zwykle tylko należy wprowadzić po stają się zestalone interfejsu API oraz nie jest już oczekuje się znacznie zmieniać.</span><span class="sxs-lookup"><span data-stu-id="d584e-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="d584e-131">Zawsze stosować najlepsze rozwiązania dotyczące używania ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="d584e-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="d584e-132">Postępuj zgodnie z [najlepsze rozwiązania dotyczące Using Strings in .NET](../../standard/base-types/best-practices-strings.md) wskazówki.</span><span class="sxs-lookup"><span data-stu-id="d584e-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="d584e-133">W szczególności należy zawsze jawnie określać *kultury intencji* konwersji i porównanie ciągów (jeśli dotyczy).</span><span class="sxs-lookup"><span data-stu-id="d584e-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="d584e-134">Wytyczne dotyczące języka F #-połączonego z biblioteki</span><span class="sxs-lookup"><span data-stu-id="d584e-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="d584e-135">W tej sekcji przedstawiono zalecenia dotyczące tworzenia publicznego F #-połączonego z biblioteki; oznacza to, że biblioteki udostępnia publiczne interfejsy API, które są przeznaczone do użycia przez deweloperów F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="d584e-136">Istnieją różne zalecenia dotyczące projektowania biblioteki dotyczy w szczególności F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="d584e-137">W przypadku braku szczegółowe zalecenia, które należy wykonać wytyczne dotyczące projektowania dla biblioteki .NET są wskazówki rezerwowego.</span><span class="sxs-lookup"><span data-stu-id="d584e-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="d584e-138">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d584e-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="d584e-139">Użyj platformy .NET konwencji nazewnictwa i wielkości liter</span><span class="sxs-lookup"><span data-stu-id="d584e-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="d584e-140">Poniższa tabela jest zgodna z konwencjami nazewnictwa i wielkości liter, platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="d584e-141">Istnieją małe dodatki, aby obejmować konstrukcje F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="d584e-142">Konstrukcja</span><span class="sxs-lookup"><span data-stu-id="d584e-142">Construct</span></span> | <span data-ttu-id="d584e-143">przypadek</span><span class="sxs-lookup"><span data-stu-id="d584e-143">Case</span></span> | <span data-ttu-id="d584e-144">Część</span><span class="sxs-lookup"><span data-stu-id="d584e-144">Part</span></span> | <span data-ttu-id="d584e-145">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d584e-145">Examples</span></span> | <span data-ttu-id="d584e-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d584e-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="d584e-147">Typów konkretnych</span><span class="sxs-lookup"><span data-stu-id="d584e-147">Concrete types</span></span> | <span data-ttu-id="d584e-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-148">PascalCase</span></span> | <span data-ttu-id="d584e-149">Rzeczownik / przymiotników</span><span class="sxs-lookup"><span data-stu-id="d584e-149">Noun/ adjective</span></span> | <span data-ttu-id="d584e-150">Lista, Double, złożone</span><span class="sxs-lookup"><span data-stu-id="d584e-150">List, Double, Complex</span></span> | <span data-ttu-id="d584e-151">Konkretne typy są struktur, klas, wyliczeń, delegatów, rekordy i Unii.</span><span class="sxs-lookup"><span data-stu-id="d584e-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="d584e-152">Chociaż nazwy typów są zazwyczaj pisane małymi literami w OCaml, F # przyjęła schemat nazewnictwa platformy .NET dla typów.</span><span class="sxs-lookup"><span data-stu-id="d584e-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="d584e-153">biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="d584e-153">DLLs</span></span>           | <span data-ttu-id="d584e-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-154">PascalCase</span></span> |                 | <span data-ttu-id="d584e-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="d584e-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="d584e-156">Tagi Unii</span><span class="sxs-lookup"><span data-stu-id="d584e-156">Union tags</span></span>     | <span data-ttu-id="d584e-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-157">PascalCase</span></span> | <span data-ttu-id="d584e-158">Rzeczownik</span><span class="sxs-lookup"><span data-stu-id="d584e-158">Noun</span></span> | <span data-ttu-id="d584e-159">Niektóre z nich, Dodaj sukces</span><span class="sxs-lookup"><span data-stu-id="d584e-159">Some, Add, Success</span></span> | <span data-ttu-id="d584e-160">Nie używaj prefiksu w publicznych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="d584e-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="d584e-161">Opcjonalnie użyj prefiksu, gdy wewnętrznych, takich jak "" wpisz zespołów = TAlpha</span><span class="sxs-lookup"><span data-stu-id="d584e-161">Optionally use a prefix when internal, such as \`\`\`type Teams = TAlpha</span></span> | <span data-ttu-id="d584e-162">TBeta</span><span class="sxs-lookup"><span data-stu-id="d584e-162">TBeta</span></span> | <span data-ttu-id="d584e-163">TDelta. ""</span><span class="sxs-lookup"><span data-stu-id="d584e-163">TDelta.\`\`\`</span></span> |
| <span data-ttu-id="d584e-164">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="d584e-164">Event</span></span>          | <span data-ttu-id="d584e-165">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-165">PascalCase</span></span> | <span data-ttu-id="d584e-166">zlecenia</span><span class="sxs-lookup"><span data-stu-id="d584e-166">Verb</span></span> | <span data-ttu-id="d584e-167">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="d584e-167">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="d584e-168">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d584e-168">Exceptions</span></span>     | <span data-ttu-id="d584e-169">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-169">PascalCase</span></span> |      | <span data-ttu-id="d584e-170">Klasa WebException</span><span class="sxs-lookup"><span data-stu-id="d584e-170">WebException</span></span> | <span data-ttu-id="d584e-171">Nazwa powinna kończyć "Wyjątki".</span><span class="sxs-lookup"><span data-stu-id="d584e-171">Name should end with “Exception”.</span></span> |
| <span data-ttu-id="d584e-172">Pole</span><span class="sxs-lookup"><span data-stu-id="d584e-172">Field</span></span>          | <span data-ttu-id="d584e-173">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-173">PascalCase</span></span> | <span data-ttu-id="d584e-174">Rzeczownik</span><span class="sxs-lookup"><span data-stu-id="d584e-174">Noun</span></span> | <span data-ttu-id="d584e-175">CurrentName</span><span class="sxs-lookup"><span data-stu-id="d584e-175">CurrentName</span></span>  | |
| <span data-ttu-id="d584e-176">Typy interfejsów</span><span class="sxs-lookup"><span data-stu-id="d584e-176">Interface types</span></span> |  <span data-ttu-id="d584e-177">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-177">PascalCase</span></span> | <span data-ttu-id="d584e-178">Rzeczownik / przymiotników</span><span class="sxs-lookup"><span data-stu-id="d584e-178">Noun/ adjective</span></span> | <span data-ttu-id="d584e-179">Interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="d584e-179">IDisposable</span></span> | <span data-ttu-id="d584e-180">Nazwa powinna rozpoczynać "I".</span><span class="sxs-lookup"><span data-stu-id="d584e-180">Name should start with “I”.</span></span> |
| <span data-ttu-id="d584e-181">Metoda</span><span class="sxs-lookup"><span data-stu-id="d584e-181">Method</span></span> |  <span data-ttu-id="d584e-182">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-182">PascalCase</span></span> |  <span data-ttu-id="d584e-183">zlecenia</span><span class="sxs-lookup"><span data-stu-id="d584e-183">Verb</span></span> | <span data-ttu-id="d584e-184">ToString</span><span class="sxs-lookup"><span data-stu-id="d584e-184">ToString</span></span> | |
| <span data-ttu-id="d584e-185">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="d584e-185">Namespace</span></span> | <span data-ttu-id="d584e-186">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-186">PascalCase</span></span> | | <span data-ttu-id="d584e-187">Microsoft.FSharp.Core</span><span class="sxs-lookup"><span data-stu-id="d584e-187">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="d584e-188">Na ogół używają `<Organization>.<Technology>[.<Subnamespace>]`, mimo że Porzuć organizacji, jeśli ta technologia jest niezależny od organizacji.</span><span class="sxs-lookup"><span data-stu-id="d584e-188">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="d584e-189">Parametry</span><span class="sxs-lookup"><span data-stu-id="d584e-189">Parameters</span></span> | <span data-ttu-id="d584e-190">camelCase</span><span class="sxs-lookup"><span data-stu-id="d584e-190">camelCase</span></span> | <span data-ttu-id="d584e-191">Rzeczownik</span><span class="sxs-lookup"><span data-stu-id="d584e-191">Noun</span></span> |  <span data-ttu-id="d584e-192">Element typeName, przekształcania, zakresu</span><span class="sxs-lookup"><span data-stu-id="d584e-192">typeName, transform, range</span></span> | |
| <span data-ttu-id="d584e-193">Pozwól wartości (wewnętrzny)</span><span class="sxs-lookup"><span data-stu-id="d584e-193">let values (internal)</span></span> | <span data-ttu-id="d584e-194">camelCase lub PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-194">camelCase or PascalCase</span></span> | <span data-ttu-id="d584e-195">Rzeczownik / zlecenia</span><span class="sxs-lookup"><span data-stu-id="d584e-195">Noun/ verb</span></span> |  <span data-ttu-id="d584e-196">getValue, myTable</span><span class="sxs-lookup"><span data-stu-id="d584e-196">getValue, myTable</span></span> |
| <span data-ttu-id="d584e-197">Pozwól wartości (zewnętrzne)</span><span class="sxs-lookup"><span data-stu-id="d584e-197">let values (external)</span></span> | <span data-ttu-id="d584e-198">camelCase lub PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-198">camelCase or PascalCase</span></span> | <span data-ttu-id="d584e-199">Rzeczownik/zlecenia</span><span class="sxs-lookup"><span data-stu-id="d584e-199">Noun/verb</span></span>  | <span data-ttu-id="d584e-200">List.map, Dates.Today</span><span class="sxs-lookup"><span data-stu-id="d584e-200">List.map, Dates.Today</span></span> | <span data-ttu-id="d584e-201">wartości powiązanym umożliwiają często są publiczne, gdy następujące wzorce projektowe funkcjonalności tradycyjnych.</span><span class="sxs-lookup"><span data-stu-id="d584e-201">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="d584e-202">Jednak zazwyczaj użyć PascalCase identyfikator może być używana z innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-202">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="d584e-203">Właściwość</span><span class="sxs-lookup"><span data-stu-id="d584e-203">Property</span></span>  | <span data-ttu-id="d584e-204">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d584e-204">PascalCase</span></span>  | <span data-ttu-id="d584e-205">Rzeczownik / przymiotników</span><span class="sxs-lookup"><span data-stu-id="d584e-205">Noun/ adjective</span></span>  | <span data-ttu-id="d584e-206">IsEndOfFile, kolor tła</span><span class="sxs-lookup"><span data-stu-id="d584e-206">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="d584e-207">Operatory logiczne ogólnie użycie jest i może i powinno być twierdząca, tak jak IsEndOfFile, nie IsNotEndOfFile.</span><span class="sxs-lookup"><span data-stu-id="d584e-207">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="d584e-208">Unikaj skrótów</span><span class="sxs-lookup"><span data-stu-id="d584e-208">Avoid abbreviations</span></span>

<span data-ttu-id="d584e-209">Wskazówki .NET zniechęcać do używania skrótów (na przykład "Użyj `OnButtonClick` zamiast `OnBtnClick`").</span><span class="sxs-lookup"><span data-stu-id="d584e-209">The .NET guidelines discourage the use of abbreviations (for example, “use `OnButtonClick` rather than `OnBtnClick`”).</span></span> <span data-ttu-id="d584e-210">Skrótów, takich jak `Async` dla "Asynchroniczne" są tolerowane.</span><span class="sxs-lookup"><span data-stu-id="d584e-210">Common abbreviations, such as `Async` for “Asynchronous”, are tolerated.</span></span> <span data-ttu-id="d584e-211">Ta wytyczna czasami jest ignorowany dla programowania funkcjonalności. na przykład `List.iter` używa skrót "iteracji".</span><span class="sxs-lookup"><span data-stu-id="d584e-211">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for “iterate”.</span></span> <span data-ttu-id="d584e-212">Z tego powodu, za pomocą skrótów zwykle tolerowane większym stopniu w języku F #-do-programowanie F #, ale nadal jest ogólnie należy unikać w projekcie składnik publiczny.</span><span class="sxs-lookup"><span data-stu-id="d584e-212">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="d584e-213">Należy unikać wielkość liter Kolizje nazw</span><span class="sxs-lookup"><span data-stu-id="d584e-213">Avoid casing name collisions</span></span>

<span data-ttu-id="d584e-214">Wskazówki .NET Załóżmy, że wielkość liter samodzielnie nie można użyć do odróżniania konfliktów nazw, ponieważ niektóre języki klienta (na przykład Visual Basic) jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="d584e-214">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="d584e-215">Użyj akronimów, gdzie jest to odpowiednie</span><span class="sxs-lookup"><span data-stu-id="d584e-215">Use acronyms where appropriate</span></span>

<span data-ttu-id="d584e-216">Akronimów, takich jak XML nie są skróty i są powszechnie używane w bibliotekach .NET w postaci małymi (Xml).</span><span class="sxs-lookup"><span data-stu-id="d584e-216">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="d584e-217">Tylko należy używać dobrze znanej i dobrze znana akronimów.</span><span class="sxs-lookup"><span data-stu-id="d584e-217">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="d584e-218">Użyj PascalCase dla nazw parametrów ogólnych</span><span class="sxs-lookup"><span data-stu-id="d584e-218">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="d584e-219">Na użytek PascalCase nazwy parametru ogólnego w publicznych interfejsów API, w tym w języku F #-połączonego z biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d584e-219">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="d584e-220">W szczególności należy używać nazw takich jak `T`, `U`, `T1`, `T2` dla dowolnych parametrów ogólnych, a gdy konkretne nazwy sensu, następnie w języku F #-bibliotek umożliwiający dostęp do Internetu Użyj nazwy, takie jak `Key`, `Value`, `Arg`(ale nie na przykład `TKey`).</span><span class="sxs-lookup"><span data-stu-id="d584e-220">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="d584e-221">Na użytek PascalCase lub camelCase funkcji publicznych i wartości w modułach F #</span><span class="sxs-lookup"><span data-stu-id="d584e-221">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="d584e-222">camelCase służy do funkcji publicznych, które są przeznaczone do służyć niekwalifikowana (na przykład `invalidArg`) i "standardowe kolekcji funkcji" (na przykład List.map).</span><span class="sxs-lookup"><span data-stu-id="d584e-222">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the “standard collection functions” (for example, List.map).</span></span> <span data-ttu-id="d584e-223">W obu tych przypadkach nazwy funkcji działają podobnie jak słowa kluczowe w języku.</span><span class="sxs-lookup"><span data-stu-id="d584e-223">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="d584e-224">Obiekt, typ i moduł projektu</span><span class="sxs-lookup"><span data-stu-id="d584e-224">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="d584e-225">Użyj przestrzeni nazw lub modułów, aby zawierać modułów i typów</span><span class="sxs-lookup"><span data-stu-id="d584e-225">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="d584e-226">Każdy plik F # w składniku powinien zaczynać się od deklaracji przestrzeni nazw lub deklaracja modułu.</span><span class="sxs-lookup"><span data-stu-id="d584e-226">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="d584e-227">lub</span><span class="sxs-lookup"><span data-stu-id="d584e-227">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="d584e-228">Różnice między używaniem modułów i przestrzeni nazw do organizowania kodu na najwyższym poziomie są następujące:</span><span class="sxs-lookup"><span data-stu-id="d584e-228">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="d584e-229">Przestrzenie nazw może obejmować wiele plików</span><span class="sxs-lookup"><span data-stu-id="d584e-229">Namespaces can span multiple files</span></span>
* <span data-ttu-id="d584e-230">Przestrzenie nazw nie może zawierać funkcji F #, chyba że są one w moduł wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="d584e-230">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="d584e-231">Kod dla każdego danego modułu muszą znajdować się w jednym pliku</span><span class="sxs-lookup"><span data-stu-id="d584e-231">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="d584e-232">Moduły najwyższego poziomu może zawierać funkcji F # bez konieczności moduł wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="d584e-232">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="d584e-233">Wybór między przestrzeń nazw najwyższego poziomu lub moduł ma wpływ na formularzu skompilowanego kodu i związku z tym wpływają na widok z innymi językami .NET należy interfejsu API po pewnym czasie być używane poza kodzie języka F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-233">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="d584e-234">Użyj metody i właściwości dla operacji wewnętrznej do typów obiektów</span><span class="sxs-lookup"><span data-stu-id="d584e-234">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="d584e-235">Praca z obiektami, najlepiej upewnij się, że w użyciu jest implementowana jako metody i właściwości tego typu.</span><span class="sxs-lookup"><span data-stu-id="d584e-235">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="d584e-236">Większość funkcji dla danego elementu członkowskiego nie muszą zawsze zaimplementowana w tym elemencie członkowskim, ale powinien być w użyciu część tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d584e-236">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="d584e-237">Używanie klas do hermetyzacji modyfikowalnego stanu</span><span class="sxs-lookup"><span data-stu-id="d584e-237">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="d584e-238">W języku F # tylko musi to której odbywać, że stan nie jest już zamknięte przez innej konstrukcji języka, takich jak zamknięcie, wyrażenia sekwencji lub asynchroniczne obliczenie.</span><span class="sxs-lookup"><span data-stu-id="d584e-238">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="d584e-239">Użyj interfejsów do grupowania działań związanych z</span><span class="sxs-lookup"><span data-stu-id="d584e-239">Use interfaces to group related operations</span></span>

<span data-ttu-id="d584e-240">Typy interfejsów umożliwia reprezentuje zestaw operacji.</span><span class="sxs-lookup"><span data-stu-id="d584e-240">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="d584e-241">To jest preferowana względem innych opcji, takie jak krotek funkcji lub rekordy funkcji.</span><span class="sxs-lookup"><span data-stu-id="d584e-241">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="d584e-242">W preference do:</span><span class="sxs-lookup"><span data-stu-id="d584e-242">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

<span data-ttu-id="d584e-243">Najwyższej jakości koncepcje na platformie .NET, którego można użyć do osiągnięcia, jakie Funktory będzie zwykle zapewniają są interfejsy.</span><span class="sxs-lookup"><span data-stu-id="d584e-243">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="d584e-244">Ponadto może być używany do kodowania typów egzystencjalna do tego programu, który rejestruje funkcji nie może.</span><span class="sxs-lookup"><span data-stu-id="d584e-244">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a><span data-ttu-id="d584e-245">Używaj modułu TPM funkcje grupy, które działają w kolekcjach</span><span class="sxs-lookup"><span data-stu-id="d584e-245">Use a module to group functions which act on collections</span></span>

<span data-ttu-id="d584e-246">Podczas definiowania typem kolekcji, należy wziąć pod uwagę zapewnienie standardowy zestaw operacji, takich jak `CollectionType.map` i `CollectionType.iter`) dla nowych typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d584e-246">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="d584e-247">Jeśli takie modułu, należy wykonać standardowe konwencje nazewnictwa dla funkcje dostępne w elemencie FSharp.Core.</span><span class="sxs-lookup"><span data-stu-id="d584e-247">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="d584e-248">Używaj modułu TPM funkcje grupy do wspólnego, kanonicznej funkcji, szczególnie w przypadku matematyczne i biblioteki DSL</span><span class="sxs-lookup"><span data-stu-id="d584e-248">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="d584e-249">Na przykład `Microsoft.FSharp.Core.Operators` automatycznie otwierane zbiór funkcji najwyższego poziomu (np. `abs` i `sin`) dostarczonych przez FSharp.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="d584e-249">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="d584e-250">Podobnie, biblioteka statystyki może obejmować modułu za pomocą funkcji `erf` i `erfc`, w którym ten moduł służy do można jawnie lub automatycznie otworzyć.</span><span class="sxs-lookup"><span data-stu-id="d584e-250">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="d584e-251">Należy rozważyć użycie RequireQualifiedAccess i dokładnie Zastosuj AutoOpen — atrybuty</span><span class="sxs-lookup"><span data-stu-id="d584e-251">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="d584e-252">Dodawanie `[<RequireQualifiedAccess>]` atrybut do modułu wskazuje, że moduł nie może być otwarty i że odwołania do elementów moduł wymaga jawnego kwalifikowana dostępu.</span><span class="sxs-lookup"><span data-stu-id="d584e-252">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="d584e-253">Na przykład `Microsoft.FSharp.Collections.List` moduł ma tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d584e-253">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="d584e-254">Jest to przydatne, gdy funkcje i wartości w module mają nazwy, które mogą powodować konflikt z nazwami w innych modułach.</span><span class="sxs-lookup"><span data-stu-id="d584e-254">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="d584e-255">Wymagające dostępu kwalifikowana może znacznie zwiększyć długoterminowe łatwość konserwacji i evolvability biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d584e-255">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="d584e-256">Dodawanie `[<AutoOpen>]` atrybutu do modułu oznacza, że moduł zostanie otwarty po otwarciu zawierającej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d584e-256">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="d584e-257">`[<AutoOpen>]` Atrybut ma również zastosowanie do zestawu, aby wskazać, moduł, który jest automatycznie otwierana, gdy odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d584e-257">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="d584e-258">Na przykład, biblioteka statystyki **MathsHeaven.Statistics** może zawierać `module MathsHeaven.Statistics.Operators` zawierająca funkcje `erf` i `erfc`.</span><span class="sxs-lookup"><span data-stu-id="d584e-258">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="d584e-259">Można oznaczyć ten moduł jako `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="d584e-259">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="d584e-260">Oznacza to, że `open MathsHeaven.Statistics` również spowoduje to otwarcie tego modułu i przenieść nazwy `erf` i `erfc` do zakresu.</span><span class="sxs-lookup"><span data-stu-id="d584e-260">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="d584e-261">Użycie innego dobre `[<AutoOpen>]` dla modułów zawierających metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d584e-261">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="d584e-262">Nadużywać z `[<AutoOpen>]` prowadzi do zanieczyszczonych przestrzenie nazw i atrybutu powinna być stosowana z rozwagą.</span><span class="sxs-lookup"><span data-stu-id="d584e-262">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="d584e-263">Dla określonych bibliotek w określonych domenach, korzystać z `[<AutoOpen>]` może prowadzić do lepszego użyteczność.</span><span class="sxs-lookup"><span data-stu-id="d584e-263">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="d584e-264">Należy rozważyć Definiowanie operatora członków w klasach, gdzie jest odpowiednia przy użyciu dobrze znanych operatorów</span><span class="sxs-lookup"><span data-stu-id="d584e-264">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="d584e-265">Czasami klasy służą do modelowania konstrukcje matematyczne, takie jak wektory.</span><span class="sxs-lookup"><span data-stu-id="d584e-265">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="d584e-266">Kiedy domeny są modelowane ma dobrze znanym użytkownikom, definiując je jako elementy członkowskie wewnętrzne klasy jest pomocne.</span><span class="sxs-lookup"><span data-stu-id="d584e-266">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="d584e-267">Niniejsze wskazówki odpowiada ogólne wskazówki .NET dotyczące tych typów.</span><span class="sxs-lookup"><span data-stu-id="d584e-267">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="d584e-268">Jednak może być dodatkowo ważne w F # kodowania, ponieważ pozwala ono tych typów, które ma być używany w połączeniu z F # funkcje i metody z ograniczeniami elementu członkowskiego, takie jak List.sumBy.</span><span class="sxs-lookup"><span data-stu-id="d584e-268">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="d584e-269">Należy rozważyć użycie compiledname — w celu zapewnienia. NET — przyjazna nazwa dla innych klientów języka .NET</span><span class="sxs-lookup"><span data-stu-id="d584e-269">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="d584e-270">Czasami możesz chcieć nazw coś w jednym stylu dla konsumentów F # (takich jak statyczny element członkowski w małe litery, tak aby pojawił tak, jakby była to funkcja powiązane z modułu), ale mają różne style dla nazwy, gdy jest ona kompilowana do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d584e-270">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="d584e-271">Możesz użyć `[<CompiledName>]` atrybutu, aby zapewnić innego stylu dla kodu innego niż F #, korzystanie z zestawu.</span><span class="sxs-lookup"><span data-stu-id="d584e-271">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="d584e-272">Za pomocą `[<CompiledName>]`, można użyć konwencji nazewnictwa platformy .NET, innego niż F # w konsumentach napisanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="d584e-272">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="d584e-273">Użyj przeciążenie metody do funkcji elementu członkowskiego, jeśli w ten sposób zapewnia prostszy interfejs API</span><span class="sxs-lookup"><span data-stu-id="d584e-273">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="d584e-274">Przeciążenie metody jest zaawansowanym narzędziem internetowym upraszczającym interfejsu API, który może być konieczne wykonanie podobne funkcje, ale z różnych opcji lub argumentów.</span><span class="sxs-lookup"><span data-stu-id="d584e-274">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="d584e-275">W języku F # jest bardziej powszechne, aby można było przeciążyć na liczbę argumentów, a nie typy argumentów.</span><span class="sxs-lookup"><span data-stu-id="d584e-275">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="d584e-276">Ukryj liczbami w postaci rekordu i typy Unii, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji</span><span class="sxs-lookup"><span data-stu-id="d584e-276">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="d584e-277">Unikaj ujawniania konkretnych reprezentacje obiektów.</span><span class="sxs-lookup"><span data-stu-id="d584e-277">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="d584e-278">Na przykład konkretny reprezentacja <xref:System.DateTime> wartości nie została ujawniona przez zewnętrzny, publiczny interfejs API projektu biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-278">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="d584e-279">W czasie wykonywania środowisko uruchomieniowe języka wspólnego wie, implementacja zatwierdzone, używanym w całym wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d584e-279">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="d584e-280">Jednak kod skompilowany nie sam przejmą zależności od konkretnych reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="d584e-280">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="d584e-281">Unikaj stosowania dziedziczenia implementacji rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="d584e-281">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="d584e-282">W języku F # jest rzadko używana implementacja dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="d584e-282">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="d584e-283">Ponadto hierarchii dziedziczenia najczęściej złożonej i trudnej można zmienić po nadejściu nowych wymagań.</span><span class="sxs-lookup"><span data-stu-id="d584e-283">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="d584e-284">Implementacja dziedziczenia nadal istnieje w języku F # dla zgodności i rzadkich przypadkach, gdy jest to najlepsze rozwiązanie problemu, ale techniki alternatywnego należy dążyć w swoich programach F # podczas projektowania dla polimorfizmu, takich jak implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d584e-284">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="d584e-285">Sygnatury funkcji i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="d584e-285">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="d584e-286">Używaj krotek dla wartości zwracanych, gdy zwracany jest niewielka liczba wielu niepowiązanych wartości</span><span class="sxs-lookup"><span data-stu-id="d584e-286">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="d584e-287">W tym miejscu jest dobrym przykładem korzystania z krotki w typ zwracany:</span><span class="sxs-lookup"><span data-stu-id="d584e-287">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="d584e-288">Zwracane typy zawierające wiele składników lub w przypadku, gdy składniki są powiązane z pojedynczą jednostkę do zidentyfikowania, należy rozważyć użycie typu nazwanego zamiast spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d584e-288">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="d584e-289">Użyj `Async<T>` dla programowania asynchronicznego na granicach interfejsu API języka F #</span><span class="sxs-lookup"><span data-stu-id="d584e-289">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="d584e-290">Jeśli jest odpowiednia Operacja synchroniczna, o nazwie `Operation` zwracającego `T`, powinien zostać nazwany operacji asynchronicznej, a następnie `AsyncOperation` Jeśli zwróci ona `Async<T>` lub `OperationAsync` Jeśli zwróci ona `Task<T>`.</span><span class="sxs-lookup"><span data-stu-id="d584e-290">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="d584e-291">Dla często używanych typów .NET, które ujawniają początek/koniec metody, należy wziąć pod uwagę przy użyciu `Async.FromBeginEnd` do zapisania metody rozszerzenia jako fasada zapewnienie F # asynchronicznego modelu programowania do tych interfejsów API platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-291">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

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

### <a name="exceptions"></a><span data-ttu-id="d584e-292">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d584e-292">Exceptions</span></span>

<span data-ttu-id="d584e-293">Zobacz [zarządzanie błędami](conventions.md#error-management) Aby dowiedzieć się więcej na temat właściwego użycia, wyjątków, wyniki i opcje.</span><span class="sxs-lookup"><span data-stu-id="d584e-293">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="d584e-294">Elementy członkowskie rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="d584e-294">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="d584e-295">Dokładnie zastosować F # elementy członkowskie rozszerzeń w języku F #-do-F # składników</span><span class="sxs-lookup"><span data-stu-id="d584e-295">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="d584e-296">Elementy członkowskie rozszerzeń F # powinien ogólnie można używać tylko dla operacji, które znajdują się w zamknięcia wewnętrzne operacje skojarzone z typem w większości jej trybów użytkowania.</span><span class="sxs-lookup"><span data-stu-id="d584e-296">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="d584e-297">Jeden z najczęściej używanych jest zapewnienie interfejsów API, które są bardziej idiomatyczną do F # dla różnych typów .NET:</span><span class="sxs-lookup"><span data-stu-id="d584e-297">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="d584e-298">Typy Unii</span><span class="sxs-lookup"><span data-stu-id="d584e-298">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="d584e-299">Na użytek dyskryminowanych związków zamiast hierarchii klas strukturze drzewa danych</span><span class="sxs-lookup"><span data-stu-id="d584e-299">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="d584e-300">Struktury drzewa są rekursywnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="d584e-300">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="d584e-301">Jest niewygodna za pomocą dziedziczenia, ale elegancki za pomocą sumy rozłączne.</span><span class="sxs-lookup"><span data-stu-id="d584e-301">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="d584e-302">Efektywna reprezentacja danych drzewa za pomocą sumy rozłączne umożliwia również korzystać z kompletności w dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="d584e-302">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="d584e-303">Użyj `[<RequireQualifiedAccess>]` na typy Unii, w których wielkość nazwy nie są wystarczająco unikatowe</span><span class="sxs-lookup"><span data-stu-id="d584e-303">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="d584e-304">Może się okazać się w domenie, gdzie takiej samej nazwie jest najlepszą nazwę dla różnych rzeczy, takich jak przypadków Unii rozłącznej.</span><span class="sxs-lookup"><span data-stu-id="d584e-304">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="d584e-305">Możesz użyć `[<RequireQualifiedAccess>]` do rozróżniania wielkości liter nazwy w celu uniknięcia wyzwalania błędy myląca ze względu na przesłanianie zależne od kolejność `open` instrukcji</span><span class="sxs-lookup"><span data-stu-id="d584e-305">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="d584e-306">Ukryj reprezentacje sumy rozłączne binarne zgodnych interfejsów API, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji</span><span class="sxs-lookup"><span data-stu-id="d584e-306">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="d584e-307">Typy Unii korzystają ze F # dopasowania do wzorca formularzy zwięzłą modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="d584e-307">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="d584e-308">Jak wspomniano wcześniej, należy unikać, odsłaniając reprezentacje konkretnych danych, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji.</span><span class="sxs-lookup"><span data-stu-id="d584e-308">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="d584e-309">Na przykład, reprezentacja złożenia dyskryminowanego mogą być ukrywane przy użyciu deklarację prywatne lub wewnętrzne lub przy użyciu pliku podpisu.</span><span class="sxs-lookup"><span data-stu-id="d584e-309">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="d584e-310">Jeśli sumy rozłączne są ujawnione masowe, może okazać się trudne do wersji biblioteki bez przerywania kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d584e-310">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="d584e-311">Zamiast tego należy wziąć pod uwagę przedstawiania co najmniej jeden wzorce aktywne, aby umożliwić dopasowywanie wzorców względem wartości tego typu.</span><span class="sxs-lookup"><span data-stu-id="d584e-311">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="d584e-312">Wzorce aktywne zapewniają alternatywny sposób zapewnienie konsumentów F # za pomocą wzorca dopasowania unikając bezpośrednio udostępnianie typów złożenia F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-312">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="d584e-313">Funkcje śródwierszowe i ograniczeniami elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="d584e-313">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="d584e-314">Zdefiniuj ogólnego algorytmy numeryczne, za pomocą wbudowanych funkcji z ograniczeniami elementu członkowskiego domniemane i statycznie rozwiązany typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="d584e-314">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="d584e-315">Ograniczenia Członkowskie arytmetyczne i ograniczenia porównania F # są standardowe rozwiązanie dla programowania w języku F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-315">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="d584e-316">Na przykład rozważmy następujący kod:</span><span class="sxs-lookup"><span data-stu-id="d584e-316">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="d584e-317">Typ tej funkcji jest następująca:</span><span class="sxs-lookup"><span data-stu-id="d584e-317">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="d584e-318">To jest odpowiednia funkcja publicznego interfejsu API w bibliotekę funkcji matematycznych.</span><span class="sxs-lookup"><span data-stu-id="d584e-318">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="d584e-319">Unikaj korzystania z ograniczeniami elementu członkowskiego symulacji klasy typów i wpisując kaczka</span><span class="sxs-lookup"><span data-stu-id="d584e-319">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="d584e-320">Istnieje możliwość zasymulować "kacze, wpisując" przy użyciu języka F # ograniczeniami elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d584e-320">It is possible to simulate “duck typing” using F# member constraints.</span></span> <span data-ttu-id="d584e-321">Jednak elementy członkowskie, które należy użyć tego ogólne nie należy używać w języku F #-do-projekty biblioteki F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-321">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="d584e-322">Jest tak, ponieważ projekty biblioteki, na podstawie nieznaną lub niestandardową niejawne ograniczeń, które mogą spowodować, że kod użytkownika do stają się sztywny i wiązanej wzorcem jednej określonej struktury.</span><span class="sxs-lookup"><span data-stu-id="d584e-322">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="d584e-323">Ponadto jest dobrym pomysłem, która intensywnie korzysta z ograniczeniami elementu członkowskiego w ten sposób może spowodować czasy kompilacji bardzo długi.</span><span class="sxs-lookup"><span data-stu-id="d584e-323">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="d584e-324">Definicje — operator</span><span class="sxs-lookup"><span data-stu-id="d584e-324">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="d584e-325">Unikaj definiowania niestandardowych operatorów symboliczne</span><span class="sxs-lookup"><span data-stu-id="d584e-325">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="d584e-326">Operatory niestandardowe są niezbędne w niektórych sytuacjach i są bardzo przydatne notational urządzeń znajdujących się w dużej części kodu realizacji.</span><span class="sxs-lookup"><span data-stu-id="d584e-326">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="d584e-327">Nowi użytkownicy biblioteki nazwane funkcje są często łatwiejsze w użyciu.</span><span class="sxs-lookup"><span data-stu-id="d584e-327">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="d584e-328">Ponadto niestandardowych operatorów symboliczne może być trudne do dokumentu, a użytkownicy znaleźć trudniej uzyskać pomoc dotyczącą operatorów, ze względu na ograniczenia istniejącego w IDE i wyszukiwania aparaty wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d584e-328">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="d584e-329">W rezultacie warto publikować własne funkcje jako nazwane funkcje i elementy członkowskie, a dodatkowo ujawnić operatory dla tej funkcji, tylko wtedy, gdy przeważają korzyści notational, dokumentacji i cognitive koszt oni.</span><span class="sxs-lookup"><span data-stu-id="d584e-329">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="d584e-330">Jednostki miary</span><span class="sxs-lookup"><span data-stu-id="d584e-330">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="d584e-331">Dokładnie użycia jednostek miary bezpieczeństwo typów dodanych w kodzie języka F #</span><span class="sxs-lookup"><span data-stu-id="d584e-331">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="d584e-332">Dodatkowe informacje Pisownia jednostki miary są usuwane w przypadku widocznej z innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-332">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="d584e-333">Należy pamiętać, że składniki .NET, narzędzia i odbicia będą widzieć typy sieci SAN, jednostek.</span><span class="sxs-lookup"><span data-stu-id="d584e-333">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="d584e-334">Na przykład C# będą widzieli `float` zamiast `float<kg>`.</span><span class="sxs-lookup"><span data-stu-id="d584e-334">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="d584e-335">Skróty typów</span><span class="sxs-lookup"><span data-stu-id="d584e-335">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="d584e-336">Dokładnie uprościć kod F # za pomocą skróty typów</span><span class="sxs-lookup"><span data-stu-id="d584e-336">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="d584e-337">Składniki .NET, narzędzia i odbicia nie będą widzieć skrócone nazwy dla typów.</span><span class="sxs-lookup"><span data-stu-id="d584e-337">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="d584e-338">Znaczne wykorzystanie skróty typów można również ustawić domenę pojawiają się faktycznie jest bardziej złożone niż, który może mylić konsumentów.</span><span class="sxs-lookup"><span data-stu-id="d584e-338">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="d584e-339">Unikaj skrótów typu dla typów publicznych, na których elementy członkowskie i właściwości powinny różnić się wewnętrznie do tych, które są dostępne wobec typu jest skracana</span><span class="sxs-lookup"><span data-stu-id="d584e-339">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="d584e-340">W tym przypadku typ jest skrócona, co spowoduje wyświetlenie zbyt dużo o reprezentujący rzeczywisty typ zostały zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="d584e-340">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="d584e-341">Zamiast tego należy wziąć pod uwagę zawijania — skrót typu klasy lub pojedynczym przypadku złożenia dyskryminowanego (lub, jeśli wydajność ma podstawowe, należy wziąć pod uwagę przy użyciu typu struktury do opakowania skrót).</span><span class="sxs-lookup"><span data-stu-id="d584e-341">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="d584e-342">Na przykład jest kuszące do definiowania wielu map w szczególnych przypadkach F # mapy, na przykład:</span><span class="sxs-lookup"><span data-stu-id="d584e-342">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="d584e-343">Jednak operacje logiczne notacji z kropką dla tego typu nie są takie same, jak operacje na mapie — na przykład, jest uzasadnione, że operator wyszukiwania mapy. Zwróć [klucza] pusta lista, jeśli klucz nie znajduje się w słowniku, zamiast zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d584e-343">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="d584e-344">Wytyczne dotyczące biblioteki do użycia z innymi językami .NET</span><span class="sxs-lookup"><span data-stu-id="d584e-344">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="d584e-345">Podczas projektowania biblioteki do użycia z innymi językami .NET, należy stosować się do [wytyczne dotyczące projektowania biblioteki .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="d584e-345">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="d584e-346">W tym dokumencie biblioteki te są oznaczone jako podstawowego bibliotek .NET, w przeciwieństwie do F #-połączonego z bibliotek, które używają F # tworzy bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="d584e-346">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="d584e-347">Projektowanie wanilii bibliotek .NET oznacza, że zapewnienie znanego i idiomatyczną interfejsów API zgodne z pozostałą częścią programu .NET Framework, minimalizując użycie języka F #-określonych konstrukcje w publicznym interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="d584e-347">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="d584e-348">Zasady zostały wyjaśnione w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="d584e-348">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="d584e-349">Namespace i typu projektu (w przypadku biblioteki do użycia z innymi językami .NET)</span><span class="sxs-lookup"><span data-stu-id="d584e-349">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="d584e-350">Zastosuj konwencji nazewnictwa platformy .NET do publicznego interfejsu API składniki</span><span class="sxs-lookup"><span data-stu-id="d584e-350">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="d584e-351">Należy zwrócić szczególną uwagę na użycie skrócone nazwy i wytyczne dotyczące użycia wielkich liter .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-351">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="d584e-352">Użyj przestrzeni nazw, typów i elementów członkowskich jako podstawowej struktury organizacyjnej składników</span><span class="sxs-lookup"><span data-stu-id="d584e-352">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="d584e-353">Wszystkie pliki zawierające publiczny funkcji powinna zaczynać się od `namespace` deklaracji i tylko jednostki publicznymi w przestrzeniach nazw powinny być typów.</span><span class="sxs-lookup"><span data-stu-id="d584e-353">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="d584e-354">Nie należy używać modułów F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-354">Do not use F# modules.</span></span>

<span data-ttu-id="d584e-355">Użyj modułach niepubliczna zawierającą kod implementacji, typy narzędzia i funkcje narzędziowe.</span><span class="sxs-lookup"><span data-stu-id="d584e-355">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="d584e-356">Typy statyczne powinny mieć pierwszeństwo modułów, ponieważ umożliwiają one pod kątem przyszłego rozwoju interfejsu API do użycia przeciążania operacji i innych interfejsu API platformy .NET zagadnienia dotyczące projektowania, które nie mogą być używane w modułach F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-356">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="d584e-357">Na przykład, zamiast następujące publicznego interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="d584e-357">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="d584e-358">Rozważ zamiast tego:</span><span class="sxs-lookup"><span data-stu-id="d584e-358">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="d584e-359">Używać typów rekordów F # w vanilla interfejsów API platformy .NET, jeśli projekt typy nie będą ewoluować</span><span class="sxs-lookup"><span data-stu-id="d584e-359">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="d584e-360">Typy rekordów F # kompilacji do prostych klasy .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-360">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="d584e-361">Są one odpowiednie dla niektóre typy proste i stabilne interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="d584e-361">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="d584e-362">Należy rozważyć użycie `[<NoEquality>]` i `[<NoComparison>]` atrybutów, które mają pominąć automatyczne generowanie interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d584e-362">You should consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="d584e-363">Należy też unikać stosowania pól rekordu mutable w vanilla interfejsów API platformy .NET jako tych ujawnia pole publiczne.</span><span class="sxs-lookup"><span data-stu-id="d584e-363">Also avoid using mutable record fields in vanilla .NET APIs as these exposes a public field.</span></span> <span data-ttu-id="d584e-364">Zawsze należy rozważyć, czy klasa zapewni bardziej elastycznych opcji pod kątem przyszłego rozwoju interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="d584e-364">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="d584e-365">Na przykład poniższy kod F # ujawnia publiczny interfejs API użytkownika języka C#:</span><span class="sxs-lookup"><span data-stu-id="d584e-365">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="d584e-366">F #:</span><span class="sxs-lookup"><span data-stu-id="d584e-366">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

<span data-ttu-id="d584e-367">C#:</span><span class="sxs-lookup"><span data-stu-id="d584e-367">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="d584e-368">Ukryj reprezentacja typów F # Unii w vanilla interfejsów API platformy .NET</span><span class="sxs-lookup"><span data-stu-id="d584e-368">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="d584e-369">Typy Unii F # nie są powszechnie używane przez granice składnika, nawet w przypadku F #-do-F # kodowania.</span><span class="sxs-lookup"><span data-stu-id="d584e-369">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="d584e-370">Są one urządzenia doskonałą implementacji, gdy jest używana wewnętrznie w ramach składniki i biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d584e-370">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="d584e-371">Podczas projektowania vanilla interfejsu API platformy .NET, należy wziąć pod uwagę ukrywanie reprezentacja typu złożenia przy użyciu prywatnego deklaracji lub plik podpisu.</span><span class="sxs-lookup"><span data-stu-id="d584e-371">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="d584e-372">Może także rozszerzyć typy, które umożliwia reprezentację złożenia wewnętrznie z elementami członkowskimi zapewniają odpowiednią. Interfejs API skierowaną do sieci.</span><span class="sxs-lookup"><span data-stu-id="d584e-372">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="d584e-373">Projekt graficzny interfejs użytkownika i inne składniki, korzystania z wzorców projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="d584e-373">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="d584e-374">Brak dostępnych wiele różnych platform w ramach platformy .NET, takich jak WinForms, WPF i programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-374">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="d584e-375">Konwencje nazewnictwa i projektowania dla każdego należy używać w przypadku projektowania składniki do użycia w tych platform.</span><span class="sxs-lookup"><span data-stu-id="d584e-375">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="d584e-376">Na przykład dla programowania WPF, należy przyjąć WPF wzorców projektowych dla klas, które projektowania.</span><span class="sxs-lookup"><span data-stu-id="d584e-376">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="d584e-377">W przypadku modeli w programowaniu interfejsu użytkownika, użyj wzorce projektowe, takich jak zdarzenia i kolekcje oparte na powiadomienie, takich jak znaleźć w <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="d584e-377">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="d584e-378">Projektowanie obiektów i elementów członkowskich (w przypadku biblioteki do użycia z innymi językami .NET)</span><span class="sxs-lookup"><span data-stu-id="d584e-378">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="d584e-379">Umożliwia udostępnianie zdarzeń .NET clievent — atrybut</span><span class="sxs-lookup"><span data-stu-id="d584e-379">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="d584e-380">Konstruowania `DelegateEvent` przy użyciu określonej platformy .NET należy przekazać typ, który przyjmuje obiekt i `EventArgs` (zamiast `Event`, który używa `FSharpHandler` typu domyślnie), aby zdarzenia są publikowane w dobrze znana metoda innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-380">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

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

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a><span data-ttu-id="d584e-381">Uwidacznianie operacji asynchronicznych jako metody, które zwracają zadania platformy .NET</span><span class="sxs-lookup"><span data-stu-id="d584e-381">Expose asynchronous operations as methods which return .NET tasks</span></span>

<span data-ttu-id="d584e-382">Zadania są używane na platformie .NET do reprezentowania aktywnego asynchronicznych obliczeń.</span><span class="sxs-lookup"><span data-stu-id="d584e-382">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="d584e-383">Zadania są ogólnie rzecz biorąc, mniej składu niż F # `Async<T>` obiektów, ponieważ reprezentuje zadania "już wykonuje", a nie może być ze sobą w sposób, które wykonują równolegle kompozycji, lub który ukryć propagacji anulowania sygnały i innych Parametry kontekstowe.</span><span class="sxs-lookup"><span data-stu-id="d584e-383">Tasks are in general less compositional than F# `Async<T>` objects, since they represent “already executing” tasks and can’t be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="d584e-384">Jednak mimo to metody, które zwracają zadania są standardowa reprezentacja programowanie asynchroniczne na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-384">However, despite this, methods which return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="d584e-385">Często obejmuje także do akceptowania tokenu anulowania jawne:</span><span class="sxs-lookup"><span data-stu-id="d584e-385">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="d584e-386">Użyj typów obiektów delegowanych .NET zamiast typów F # — funkcja</span><span class="sxs-lookup"><span data-stu-id="d584e-386">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="d584e-387">W tym miejscu "typów F # funkcja" oznacza "strzałkę" typów, takich jak `int -> int`.</span><span class="sxs-lookup"><span data-stu-id="d584e-387">Here “F# function types” mean “arrow” types like `int -> int`.</span></span>

<span data-ttu-id="d584e-388">Zamiast tego:</span><span class="sxs-lookup"><span data-stu-id="d584e-388">Instead of this:</span></span>

```fsharp
member this.Transform(f:int->int) =
    ...
```

<span data-ttu-id="d584e-389">wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="d584e-389">Do this:</span></span>

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

<span data-ttu-id="d584e-390">Typu funkcji F # jest wyświetlany jako `class FSharpFunc<T,U>` do innych języków platformy .NET jest mniej odpowiednia dla funkcji języka i narzędzi, które zrozumieć typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="d584e-390">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understand delegate types.</span></span> <span data-ttu-id="d584e-391">Podczas tworzenia metody wyższego rzędu przeznaczone dla .NET Framework 3.5 lub nowszego, `System.Func` i `System.Action` obiekty delegowane są odpowiednie interfejsy API w celu publikowania umożliwia deweloperom platformy .NET do korzystania z tych interfejsów API w sposób prostego.</span><span class="sxs-lookup"><span data-stu-id="d584e-391">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="d584e-392">(Podczas określania wartości docelowej platformy .NET Framework 2.0, typy zdefiniowane przez system delegatów są bardziej ograniczone; należy wziąć pod uwagę przy użyciu wstępnie zdefiniowanego delegata typy, takie jak `System.Converter<T,U>` lub definiujący typ określonego obiektu delegowanego.)</span><span class="sxs-lookup"><span data-stu-id="d584e-392">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="d584e-393">Po drugiej stronie delegatów .NET nie są fizyczną w języku F #-połączonego z biblioteki (zobacz następną sekcję F #-połączonego z bibliotekami).</span><span class="sxs-lookup"><span data-stu-id="d584e-393">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="d584e-394">W wyniku typowych strategii wdrażania podczas tworzenia metody wyższego rzędu do wanilii bibliotek .NET jest tworzyć wszystkie wdrożenia za pomocą funkcji typów F #, a następnie utwórz publiczny interfejs API przy użyciu delegatów jako fasada alokowania elastycznego na jego podstawie rzeczywistej F # Implementacja.</span><span class="sxs-lookup"><span data-stu-id="d584e-394">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="d584e-395">Użyj wzorca TryGetValue zamiast zwracać wartości opcji F # i wolisz przeciążenie metody do uwzględnienia wartości opcji F # jako argumenty</span><span class="sxs-lookup"><span data-stu-id="d584e-395">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="d584e-396">Typowe wzorce użycia typu opcji F # w interfejsach API są lepsze zaimplementowane w vanilla techniki projektowania interfejsów API platformy .NET przy użyciu platformy .NET standard.</span><span class="sxs-lookup"><span data-stu-id="d584e-396">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="d584e-397">Zamiast zwracać wartość opcji F #, należy wziąć pod uwagę przy użyciu zwracanego typu wartość logiczna, a także parametru wyjściowego tak jak wzorzec "TryGetValue".</span><span class="sxs-lookup"><span data-stu-id="d584e-397">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="d584e-398">I zamiast wartości opcji F # jako parametry, należy wziąć pod uwagę przy użyciu przeciążenie metody lub argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d584e-398">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

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

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="d584e-399">Korzystając z platformy .NET kolekcji typów IEnumerable\<T\> i IDictionary\<klucz, wartość\> dla parametrów i zwracanych wartości</span><span class="sxs-lookup"><span data-stu-id="d584e-399">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="d584e-400">Należy unikać użycia kolekcji konkretnych typów, takich jak tablice platformy .NET `T[]`, typów F # `list<T>`, `Map<Key,Value>` i `Set<T>`, i typy kolekcji konkretny .NET, takie jak `Dictionary<Key,Value>`.</span><span class="sxs-lookup"><span data-stu-id="d584e-400">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="d584e-401">Wytyczne dotyczące projektowania dla biblioteki .NET mają dobrej porad dotyczących kiedy należy używać różnych typów kolekcji, takich jak `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="d584e-401">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="d584e-402">Użyj tablic (`T[]`) jest dopuszczalna w pewnych okolicznościach, na podstawie wydajności.</span><span class="sxs-lookup"><span data-stu-id="d584e-402">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="d584e-403">Należy pamiętać, że szczególnie `seq<T>` jest po prostu języka F # alias dla `IEnumerable<T>`, i dlatego seq jest często odpowiednich typów vanilla interfejsu API platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-403">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="d584e-404">Zamiast list języka F #:</span><span class="sxs-lookup"><span data-stu-id="d584e-404">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names : string list) =
    ...
```

<span data-ttu-id="d584e-405">Sekwencje F #:</span><span class="sxs-lookup"><span data-stu-id="d584e-405">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="d584e-406">Użyj tego typu jednostki jako jedyny typ danych wejściowych metody do definiowania metody zero argument lub jako tylko zwraca typ, aby zdefiniować metodę zwracającą typ void</span><span class="sxs-lookup"><span data-stu-id="d584e-406">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="d584e-407">Należy unikać inne zastosowania tego typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="d584e-407">Avoid other uses of the unit type.</span></span> <span data-ttu-id="d584e-408">Są one dobrym:</span><span class="sxs-lookup"><span data-stu-id="d584e-408">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

<span data-ttu-id="d584e-409">To jest nieprawidłowy:</span><span class="sxs-lookup"><span data-stu-id="d584e-409">This is bad:</span></span>

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="d584e-410">Sprawdzanie pod kątem wartości null wanilii granice interfejsu API platformy .NET</span><span class="sxs-lookup"><span data-stu-id="d584e-410">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="d584e-411">Kod implementacji F # zwykle mają mniejszą liczbę wartości null, ze względu na wzorce projektowe niezmienne i ograniczenia związane z użyciem literały null dla typów F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-411">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="d584e-412">Innymi językami .NET często używają wartości null jako wartość znacznie częściej.</span><span class="sxs-lookup"><span data-stu-id="d584e-412">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="d584e-413">W związku z tym kodzie języka F #, który jest uwidaczniany vanilla interfejsu API platformy .NET należy sprawdzić parametry o wartości null na granicy interfejsu API i te wartości uniemożliwiają otrzymywanych przez lepszy kod implementacji F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-413">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="d584e-414">`isNull` Funkcji lub dopasowania do wzorca w `null` wzorca można użyć.</span><span class="sxs-lookup"><span data-stu-id="d584e-414">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="d584e-415">Unikaj korzystania z krotek jako wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="d584e-415">Avoid using tuples as return values</span></span>

<span data-ttu-id="d584e-416">Zamiast tego wolisz, zwracająca Typ nazwany, rezerwowanie zagregowane dane lub korzystanie z parametrów out zwracanie wielu wartości.</span><span class="sxs-lookup"><span data-stu-id="d584e-416">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="d584e-417">Mimo że krotek struktur i kolekcje objęte .NET (w tym obsługa języka C# dla krotek struktur), będą w większości przypadków nie zapewniają idealne i oczekiwanego interfejsu API dla deweloperów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-417">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="d584e-418">Unikaj stosowania currying parametrów</span><span class="sxs-lookup"><span data-stu-id="d584e-418">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="d584e-419">Zamiast tego należy użyć konwencji wywoływania .NET ``Method(arg1,arg2,…,argN)``.</span><span class="sxs-lookup"><span data-stu-id="d584e-419">Instead, use .NET calling conventions ``Method(arg1,arg2,…,argN)``.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="d584e-420">Porada: Jeśli projektujesz biblioteki do użycia z dowolnego języka platformy .NET, występuje nie zastąpi faktycznie wykonywania niektórych eksperymentalne języka C# i Visual Basic programowania do upewnij się, że bibliotek "działania po prawej" z tych języków.</span><span class="sxs-lookup"><span data-stu-id="d584e-420">Tip: If you’re designing libraries for use from any .NET language, then there’s no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="d584e-421">Narzędzia takie jak reflektor .NET i przeglądarki obiektów usługi Visual Studio umożliwia również upewnić się, że bibliotek i ich dokumentację są wyświetlane zgodnie z oczekiwaniami dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="d584e-421">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="d584e-422">Dodatek</span><span class="sxs-lookup"><span data-stu-id="d584e-422">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="d584e-423">Przykład end-to-end projektowania kodzie języka F # do użytku przez innymi językami .NET</span><span class="sxs-lookup"><span data-stu-id="d584e-423">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="d584e-424">Należy wziąć pod uwagę następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="d584e-424">Consider the following class:</span></span>

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

<span data-ttu-id="d584e-425">Wnioskowany Typ F # tej klasy jest następująca:</span><span class="sxs-lookup"><span data-stu-id="d584e-425">The inferred F# type of this class is as follows:</span></span>

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

<span data-ttu-id="d584e-426">Spójrzmy na sposób wyświetlania tego typu F # do programisty, użycie innego języka .NET.</span><span class="sxs-lookup"><span data-stu-id="d584e-426">Let’s take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="d584e-427">Na przykład przybliżony języka C# "podpis" jest w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d584e-427">For example, the approximate C# “signature” is as follows:</span></span>

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

<span data-ttu-id="d584e-428">Istnieją pewne ważne punkty, które informacja dotycząca jak F # reprezentuje konstrukcje w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="d584e-428">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="d584e-429">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d584e-429">For example:</span></span>

* <span data-ttu-id="d584e-430">Metadane, takie jak nazwy argumentów została zachowana.</span><span class="sxs-lookup"><span data-stu-id="d584e-430">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="d584e-431">F # metod, które przyjmują dwa argumenty stają się języka C# metod, które przyjmują dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="d584e-431">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="d584e-432">Funkcje i listy stają się odwołania do odpowiadające typy w bibliotece programu F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-432">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="d584e-433">Poniższy kod pokazuje, jak dostosować ten kod w celu uwzględnienia tych rzeczy.</span><span class="sxs-lookup"><span data-stu-id="d584e-433">The following code shows how to adjust this code to take these things into account.</span></span>

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

<span data-ttu-id="d584e-434">Wnioskowany Typ F # kodu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="d584e-434">The inferred F# type of the code is as follows:</span></span>

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

<span data-ttu-id="d584e-435">Podpis C# jest teraz w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d584e-435">The C# signature is now as follows:</span></span>

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

<span data-ttu-id="d584e-436">Poprawki wprowadzone do przygotowania tego typu do użycia jako część podstawowego biblioteki .NET są następujące:</span><span class="sxs-lookup"><span data-stu-id="d584e-436">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="d584e-437">Skorygowane kilka nazw: `Point1`, `n`, `l`, i `f` stało się `RadialPoint`, `count`, `factor`, i `transform`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="d584e-437">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="d584e-438">Zwracany typ używany `seq<RadialPoint>` zamiast `RadialPoint list` , zmieniając konstruowania listy przy użyciu `[ ... ]` do konstruowania sekwencji za pomocą `IEnumerable<RadialPoint>`.</span><span class="sxs-lookup"><span data-stu-id="d584e-438">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="d584e-439">Używany typ delegata .NET `System.Func` zamiast typu funkcji F #.</span><span class="sxs-lookup"><span data-stu-id="d584e-439">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="d584e-440">Dzięki temu znacznie wrażeń korzystanie w kodzie języka C#.</span><span class="sxs-lookup"><span data-stu-id="d584e-440">This makes it far nicer to consume in C# code.</span></span>
