---
title: Najważniejsze wskazówki dotyczące współdziałania natywnej — .NET
description: Poznaj najlepsze rozwiązania dotyczące łączenia się ze składnikami macierzystymi w .NET.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391224"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="2cfdc-103">Najlepsze rozwiązania dotyczące współpracy natywnej</span><span class="sxs-lookup"><span data-stu-id="2cfdc-103">Native interoperability best practices</span></span>

<span data-ttu-id="2cfdc-104">.NET oferuje wiele sposobów dostosowywania natywnego kodu współdziałania.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="2cfdc-105">Ten artykuł zawiera wskazówki, które zespoły platformy .NET firmy Microsoft przestrzegać dla natywnej współdziałania.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="2cfdc-106">Wskazówki ogólne</span><span class="sxs-lookup"><span data-stu-id="2cfdc-106">General guidance</span></span>

<span data-ttu-id="2cfdc-107">Wskazówki w tej sekcji dotyczy wszystkich scenariuszy interop.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="2cfdc-108">✔️ DO używać tej samej nazwy i wielkich liter dla metod i parametrów, jak metoda natywna, którą chcesz wywołać.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-108">✔️ DO use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="2cfdc-109">✔️ NALEŻY ROZWAŻYĆ użycie tego samego nazewnictwa i wielkich liter dla wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-109">✔️ CONSIDER using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="2cfdc-110">✔️ do użycia typów .NET, które mapują najbliżej typu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-110">✔️ DO use .NET types that map closest to the native type.</span></span> <span data-ttu-id="2cfdc-111">Na przykład w języku `uint` C#użyj, `unsigned int`gdy typem macierzystym jest .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="2cfdc-112">✔️ DO używać `[In]` tylko `[Out]` i atrybuty, gdy zachowanie, które chcesz różni się od zachowania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-112">✔️ DO only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="2cfdc-113">✔️ NALEŻY ROZWAŻYĆ <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> użycie do puli buforów tablicy macierzystych.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-113">✔️ CONSIDER using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="2cfdc-114">✔️ NALEŻY ROZWAŻYĆ zawijanie deklaracji P/Invoke w klasie o takiej samej nazwie i wielkich literach jak biblioteka macierzysta.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-114">✔️ CONSIDER wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="2cfdc-115">Dzięki temu `[DllImport]` atrybuty do `nameof` korzystania z funkcji języka języka języka C# przekazać w nazwie biblioteki macierzystej i upewnij się, że nie błędnie nazwę biblioteki macierzystej.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="2cfdc-116">Ustawienia atrybutu DllImport</span><span class="sxs-lookup"><span data-stu-id="2cfdc-116">DllImport attribute settings</span></span>

| <span data-ttu-id="2cfdc-117">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="2cfdc-117">Setting</span></span> | <span data-ttu-id="2cfdc-118">Domyślne</span><span class="sxs-lookup"><span data-stu-id="2cfdc-118">Default</span></span> | <span data-ttu-id="2cfdc-119">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="2cfdc-119">Recommendation</span></span> | <span data-ttu-id="2cfdc-120">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2cfdc-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="2cfdc-121">zachowaj wartość domyślną</span><span class="sxs-lookup"><span data-stu-id="2cfdc-121">keep default</span></span>  | <span data-ttu-id="2cfdc-122">Gdy jest jawnie ustawiona na false, nie powiodło się HRESULT zwracane wartości zostaną przekształcone w wyjątki (i zwraca wartość w definicji staje się null w wyniku).</span><span class="sxs-lookup"><span data-stu-id="2cfdc-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="2cfdc-123">zależy od API</span><span class="sxs-lookup"><span data-stu-id="2cfdc-123">depends on the API</span></span>  | <span data-ttu-id="2cfdc-124">Ustaw to na true, jeśli interfejs API używa GetLastError i użyj Marshal.GetLastWin32Error, aby uzyskać wartość.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="2cfdc-125">Jeśli interfejs API ustawia warunek, który mówi, że ma błąd, pobierz błąd przed wykonaniem innych wywołań, aby uniknąć nieumyślnego jego nadania.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="2cfdc-126">`CharSet.None`, który wraca `CharSet.Ansi` do zachowania</span><span class="sxs-lookup"><span data-stu-id="2cfdc-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="2cfdc-127">Jawnie `CharSet.Unicode` używać `CharSet.Ansi` lub gdy ciągi lub znaki są obecne w definicji</span><span class="sxs-lookup"><span data-stu-id="2cfdc-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="2cfdc-128">Określa zachowanie marshaling ciągów i `ExactSpelling` co `false`robi, gdy .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="2cfdc-129">Należy `CharSet.Ansi` pamiętać, że jest rzeczywiście UTF8 na Unix.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="2cfdc-130">_W_ większości przypadków system Windows używa unicode, podczas gdy Unix używa UTF8.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="2cfdc-131">Zobacz więcej informacji na temat [dokumentacji znaków](./charset.md).</span><span class="sxs-lookup"><span data-stu-id="2cfdc-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="2cfdc-132">Ustaw tę wartość true i uzyskaj niewielką korzyść perf, ponieważ środowisko wykonawcze nie będzie szukać alternatywnych nazw funkcji z `CharSet` przyrostkiem "A" lub "W" w zależności od wartości ustawienia ("A" dla `CharSet.Ansi` i "W" dla `CharSet.Unicode`).</span><span class="sxs-lookup"><span data-stu-id="2cfdc-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="2cfdc-133">Parametry ciągu</span><span class="sxs-lookup"><span data-stu-id="2cfdc-133">String parameters</span></span>

<span data-ttu-id="2cfdc-134">Gdy CharSet jest Unicode lub argument jest `[MarshalAs(UnmanagedType.LPWSTR)]` jawnie oznaczony jako _i_ ciąg jest przekazywany przez wartość (nie `ref` lub), `out`ciąg zostanie przypięty i używany bezpośrednio przez kod macierzysty (a nie kopiowane).</span><span class="sxs-lookup"><span data-stu-id="2cfdc-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="2cfdc-135">Pamiętaj, aby `[DllImport]` `Charset.Unicode` oznaczyć jako, chyba że wyraźnie chcesz ANSI leczenia strun.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="2cfdc-136">❌NIE używaj `[Out] string` parametrów.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-136">❌ DO NOT use `[Out] string` parameters.</span></span> <span data-ttu-id="2cfdc-137">Parametry ciągu przekazywane przez `[Out]` wartość z atrybutem może zdestabilizować środowisko uruchomieniowe, jeśli ciąg jest ciąg internowany.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="2cfdc-138">Zobacz więcej informacji na temat internowania ciągów w dokumentacji dla <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2cfdc-139">❌UNIKNĄĆ `StringBuilder` parametrów.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-139">❌ AVOID `StringBuilder` parameters.</span></span> <span data-ttu-id="2cfdc-140">`StringBuilder`organizowanie *zawsze* tworzy natywną kopię buforu.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="2cfdc-141">Jako takie, może to być bardzo nieefektywne.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="2cfdc-142">Weź typowy scenariusz wywoływania interfejsu API systemu Windows, który przyjmuje ciąg:</span><span class="sxs-lookup"><span data-stu-id="2cfdc-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="2cfdc-143">Tworzenie SB żądanej pojemności (przydziela zarządzaną pojemność)**{1}**</span><span class="sxs-lookup"><span data-stu-id="2cfdc-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="2cfdc-144">Invoke</span><span class="sxs-lookup"><span data-stu-id="2cfdc-144">Invoke</span></span>
   1. <span data-ttu-id="2cfdc-145">Przydziela bufor macierzysty**{2}**</span><span class="sxs-lookup"><span data-stu-id="2cfdc-145">Allocates a native buffer **{2}**</span></span>
   2. <span data-ttu-id="2cfdc-146">Kopiuje zawartość, jeśli `[In]` _(domyślnie dla parametru) `StringBuilder` _</span><span class="sxs-lookup"><span data-stu-id="2cfdc-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>
   3. <span data-ttu-id="2cfdc-147">Kopiuje bufor macierzysty do nowo `[Out]` **{3}** przydzielonej tablicy zarządzanej, jeśli _(również `StringBuilder`domyślnie)_</span><span class="sxs-lookup"><span data-stu-id="2cfdc-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>
3. <span data-ttu-id="2cfdc-148">`ToString()`przydziela kolejną tablicę zarządzana**{4}**</span><span class="sxs-lookup"><span data-stu-id="2cfdc-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="2cfdc-149">To *{4}* jest alokacje, aby uzyskać ciąg z kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="2cfdc-150">Najlepsze, co możesz zrobić, aby ograniczyć to jest ponowne użycie `StringBuilder` w innym wywołaniu, ale to nadal zapisuje tylko *1* alokacji.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="2cfdc-151">Znacznie lepiej jest używać i buforować `ArrayPool`bufor znaków z — można następnie `ToString()` dostać się do tylko alokacji dla kolejnych wywołań.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="2cfdc-152">Innym problemem `StringBuilder` jest to, że zawsze kopiuje buforu zwracanego z powrotem do pierwszej wartości null.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="2cfdc-153">Jeśli przekazany ciąg wstecz nie jest zakończony lub jest ciągiem zakończonym z podwójną wartością null, p/invoke jest w najlepszym wypadku niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="2cfdc-154">Jeśli *używasz* `StringBuilder`, jeden ostatni gotcha jest to, że pojemność **nie** zawiera ukryte null, który jest zawsze rozliczane w interop.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="2cfdc-155">Jest to typowe dla ludzi, aby uzyskać ten błąd, jak większość interfejsów API chcesz rozmiar buforu, *w tym* null.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="2cfdc-156">Może to spowodować zmarnowane/niepotrzebne alokacje.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="2cfdc-157">Ponadto ten gotcha uniemożliwia środowisko uruchomieniowe `StringBuilder` optymalizacji organizowania, aby zminimalizować kopie.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="2cfdc-158">✔️ ROZWAŻ użycie `char[]`s z `ArrayPool`pliku .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-158">✔️ CONSIDER using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="2cfdc-159">Aby uzyskać więcej informacji na temat organizowania [ciągów, zobacz Domyślne kierowanie ciągami i](../../framework/interop/default-marshaling-for-strings.md) [dostosowywanie ciągów .](customize-parameter-marshaling.md#customizing-string-parameters)</span><span class="sxs-lookup"><span data-stu-id="2cfdc-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="2cfdc-160">__Specyficzne dla systemu Windows__ W `[Out]` przypadku ciągów CLR będzie domyślnie `CoTaskMemFree` `SysStringFree` używany do wolnych `UnmanagedType.BSTR`ciągów lub ciągów, które są oznaczone jako .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-160">__Windows Specific__ For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>
> <span data-ttu-id="2cfdc-161">**Dla większości interfejsów API z buforem ciągu wyjściowego:** Liczba przekazanych znaków musi zawierać wartość null.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-161">**For most APIs with an output string buffer:** The passed in character count must include the null.</span></span> <span data-ttu-id="2cfdc-162">Jeśli zwracana wartość jest mniejsza niż liczba przekazanych znaków wywołanie zakończyło się pomyślnie, a wartość jest liczbą znaków *bez* końcowego null.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-162">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="2cfdc-163">W przeciwnym razie liczba jest wymagany rozmiar buforu, *w tym* znak null.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-163">Otherwise the count is the required size of the buffer *including* the null character.</span></span>
>
> - <span data-ttu-id="2cfdc-164">Pass in 5, get 4: Ciąg ma 4 znaki długości z końcowego null.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-164">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="2cfdc-165">Przekaż w 5, get 6: Ciąg ma długość 5 znaków, potrzebujesz bufora 6 znaków, aby pomieścić wartość null.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-165">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>
> [<span data-ttu-id="2cfdc-166">Typy danych systemu Windows dla ciągów</span><span class="sxs-lookup"><span data-stu-id="2cfdc-166">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="2cfdc-167">Parametry i pola logiczne</span><span class="sxs-lookup"><span data-stu-id="2cfdc-167">Boolean parameters and fields</span></span>

<span data-ttu-id="2cfdc-168">Wartości logiczne są łatwe do bałaganu.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-168">Booleans are easy to mess up.</span></span> <span data-ttu-id="2cfdc-169">Domyślnie .NET `bool` jest organizowane do `BOOL`systemu Windows , gdzie jest to wartość 4-bajtowa.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-169">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="2cfdc-170">Jednak , `_Bool`i `bool` typy w C i C++ są *pojedynczym* bajtem.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-170">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="2cfdc-171">Może to prowadzić do trudnych do wyśledzenia błędów, ponieważ połowa wartości zwracanej zostanie odrzucona, co tylko *potencjalnie* zmieni wynik.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-171">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="2cfdc-172">Aby uzyskać więcej informacji na `bool` temat organizowania wartości `bool` .NET do typów C lub C++, zobacz dokumentację [dotyczącą dostosowywania zasadowania pól logicznych](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span><span class="sxs-lookup"><span data-stu-id="2cfdc-172">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="2cfdc-173">Identyfikatory guid</span><span class="sxs-lookup"><span data-stu-id="2cfdc-173">GUIDs</span></span>

<span data-ttu-id="2cfdc-174">Identyfikatory GUID można bezpośrednio ująć w podpisach.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-174">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="2cfdc-175">Wiele interfejsów API `GUID&` systemu Windows `REFIID`przyjmuje aliasy typów, takie jak .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-175">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="2cfdc-176">Po przejściu przez ref, mogą `ref` one być `[MarshalAs(UnmanagedType.LPStruct)]` przekazywane przez lub z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-176">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="2cfdc-177">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2cfdc-177">GUID</span></span> | <span data-ttu-id="2cfdc-178">Identyfikator GUID przez ref</span><span class="sxs-lookup"><span data-stu-id="2cfdc-178">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="2cfdc-179">❌NIE używaj `[MarshalAs(UnmanagedType.LPStruct)]` do `ref` niczego innego niż parametry GUID.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-179">❌ DO NOT Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="2cfdc-180">Typy blittable</span><span class="sxs-lookup"><span data-stu-id="2cfdc-180">Blittable types</span></span>

<span data-ttu-id="2cfdc-181">Typy Blittable są typy, które mają taką samą reprezentację na poziomie bitowym w kodzie zarządzanym i macierzystym.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-181">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="2cfdc-182">W związku z tym nie muszą być konwertowane na inny format, który ma być organizowany do i z kodu macierzystego, a ponieważ zwiększa to wydajność powinny być preferowane.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-182">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="2cfdc-183">**Typy Blittable:**</span><span class="sxs-lookup"><span data-stu-id="2cfdc-183">**Blittable types:**</span></span>

- <span data-ttu-id="2cfdc-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="2cfdc-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="2cfdc-185">nie zagnieżdżone jednowymiarowe tablice typów `int[]`blittable (na przykład)</span><span class="sxs-lookup"><span data-stu-id="2cfdc-185">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="2cfdc-186">struktury i klasy o stałym układzie, które mają tylko typy wartości blittable dla pól instancji</span><span class="sxs-lookup"><span data-stu-id="2cfdc-186">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="2cfdc-187">wymaga `[StructLayout(LayoutKind.Sequential)]` lub`[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="2cfdc-187">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="2cfdc-188">struktury są `LayoutKind.Sequential` domyślnie, klasy są`LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="2cfdc-188">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="2cfdc-189">**NIE blittable:**</span><span class="sxs-lookup"><span data-stu-id="2cfdc-189">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="2cfdc-190">**CZASAMI blittable:**</span><span class="sxs-lookup"><span data-stu-id="2cfdc-190">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="2cfdc-191">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="2cfdc-191">`char`, `string`</span></span>

<span data-ttu-id="2cfdc-192">Gdy typy blittable są przekazywane przez odwołanie, są one po prostu przypięte przez marshaller zamiast kopiowane do buforu pośredniego.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-192">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="2cfdc-193">(Klasy są z natury przekazywane przez odwołanie, struktury są `ref` `out`przekazywane przez odwołanie, gdy są używane z lub .)</span><span class="sxs-lookup"><span data-stu-id="2cfdc-193">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="2cfdc-194">`char`jest blittable w tablicy jednowymiarowej **lub** jeśli jest to część typu, `[StructLayout]` który `CharSet = CharSet.Unicode`zawiera jest jawnie oznaczone .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-194">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="2cfdc-195">`string`jest blittable, jeśli nie jest zawarty w innym typie i jest przekazywany `[DllImport]` `CharSet = CharSet.Unicode` jako argument, który jest oznaczony `[MarshalAs(UnmanagedType.LPWStr)]` lub ma zestaw.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-195">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="2cfdc-196">Możesz sprawdzić, czy typ jest blittable, próbując `GCHandle`utworzyć przypięty .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-196">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="2cfdc-197">Jeśli typ nie jest ciągiem lub uważany `GCHandle.Alloc` za `ArgumentException`blittable, zrzuci .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-197">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="2cfdc-198">✔️ zrobić, aby twoje struktury blittable, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-198">✔️ DO make your structures blittable when possible.</span></span>

<span data-ttu-id="2cfdc-199">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="2cfdc-199">For more information, see:</span></span>

- [<span data-ttu-id="2cfdc-200">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="2cfdc-200">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)
- [<span data-ttu-id="2cfdc-201">Typ Marshaling</span><span class="sxs-lookup"><span data-stu-id="2cfdc-201">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="2cfdc-202">Utrzymywanie obiektów zarządzanych przy życiu</span><span class="sxs-lookup"><span data-stu-id="2cfdc-202">Keeping managed objects alive</span></span>

<span data-ttu-id="2cfdc-203">`GC.KeepAlive()`zapewni, że obiekt pozostanie w zakresie, dopóki metoda KeepAlive nie zostanie trafiona.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-203">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="2cfdc-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)umożliwia marshaller zachować obiekt przy życiu na czas trwania P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="2cfdc-205">Może być używany zamiast `IntPtr` w podpisy metody.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-205">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="2cfdc-206">`SafeHandle`skutecznie zastępuje tę klasę i powinien być stosowany zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-206">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="2cfdc-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)umożliwia przypinanie obiektu zarządzanego i uzyskanie do niego natywnego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="2cfdc-208">Podstawowy wzór to:</span><span class="sxs-lookup"><span data-stu-id="2cfdc-208">The basic pattern is:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="2cfdc-209">Przypinanie nie jest `GCHandle`ustawieniem domyślnym dla .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-209">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="2cfdc-210">Inny wzorzec głównych jest przekazywanie odwołania do obiektu zarządzanego za pośrednictwem kodu macierzystego i z powrotem do kodu zarządzanego, zwykle z wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-210">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="2cfdc-211">Oto wzór:</span><span class="sxs-lookup"><span data-stu-id="2cfdc-211">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="2cfdc-212">Nie zapominaj, `GCHandle` że musi być jawnie uwolniony, aby uniknąć przecieków pamięci.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-212">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="2cfdc-213">Typowe typy danych systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2cfdc-213">Common Windows data types</span></span>

<span data-ttu-id="2cfdc-214">Oto lista typów danych powszechnie używanych w interfejsach API systemu Windows i typy C# do użycia podczas wywoływania kodu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-214">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="2cfdc-215">Następujące typy są tego samego rozmiaru w systemie Windows 32-bitowym i 64-bitowym, pomimo ich nazw.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-215">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="2cfdc-216">impulsów</span><span class="sxs-lookup"><span data-stu-id="2cfdc-216">Width</span></span> | <span data-ttu-id="2cfdc-217">Windows</span><span class="sxs-lookup"><span data-stu-id="2cfdc-217">Windows</span></span>          | <span data-ttu-id="2cfdc-218">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="2cfdc-218">C (Windows)</span></span>          | <span data-ttu-id="2cfdc-219">C#</span><span class="sxs-lookup"><span data-stu-id="2cfdc-219">C#</span></span>       | <span data-ttu-id="2cfdc-220">Alternatywnych</span><span class="sxs-lookup"><span data-stu-id="2cfdc-220">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="2cfdc-221">32</span><span class="sxs-lookup"><span data-stu-id="2cfdc-221">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="2cfdc-222">8</span><span class="sxs-lookup"><span data-stu-id="2cfdc-222">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="2cfdc-223">8</span><span class="sxs-lookup"><span data-stu-id="2cfdc-223">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="2cfdc-224">8</span><span class="sxs-lookup"><span data-stu-id="2cfdc-224">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="2cfdc-225">8</span><span class="sxs-lookup"><span data-stu-id="2cfdc-225">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="2cfdc-226">16</span><span class="sxs-lookup"><span data-stu-id="2cfdc-226">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="2cfdc-227">16</span><span class="sxs-lookup"><span data-stu-id="2cfdc-227">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="2cfdc-228">16</span><span class="sxs-lookup"><span data-stu-id="2cfdc-228">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="2cfdc-229">16</span><span class="sxs-lookup"><span data-stu-id="2cfdc-229">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="2cfdc-230">16</span><span class="sxs-lookup"><span data-stu-id="2cfdc-230">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="2cfdc-231">32</span><span class="sxs-lookup"><span data-stu-id="2cfdc-231">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="2cfdc-232">32</span><span class="sxs-lookup"><span data-stu-id="2cfdc-232">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="2cfdc-233">32</span><span class="sxs-lookup"><span data-stu-id="2cfdc-233">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="2cfdc-234">32</span><span class="sxs-lookup"><span data-stu-id="2cfdc-234">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="2cfdc-235">64</span><span class="sxs-lookup"><span data-stu-id="2cfdc-235">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="2cfdc-236">64</span><span class="sxs-lookup"><span data-stu-id="2cfdc-236">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="2cfdc-237">64</span><span class="sxs-lookup"><span data-stu-id="2cfdc-237">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="2cfdc-238">64</span><span class="sxs-lookup"><span data-stu-id="2cfdc-238">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="2cfdc-239">64</span><span class="sxs-lookup"><span data-stu-id="2cfdc-239">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="2cfdc-240">32</span><span class="sxs-lookup"><span data-stu-id="2cfdc-240">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="2cfdc-241">32</span><span class="sxs-lookup"><span data-stu-id="2cfdc-241">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="2cfdc-242">Następujące typy, będąc wskaźniki, należy wykonać szerokość platformy.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-242">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="2cfdc-243">`IntPtr` / Użyj `UIntPtr` do nich.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-243">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="2cfdc-244">Typy wskaźników `IntPtr`podpisanych (używanie)</span><span class="sxs-lookup"><span data-stu-id="2cfdc-244">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="2cfdc-245">Niepodpisane typy `UIntPtr`wskaźników (użyj)</span><span class="sxs-lookup"><span data-stu-id="2cfdc-245">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="2cfdc-246">System `PVOID` Windows, który `void*` jest C może `IntPtr` być `UIntPtr`organizowane `void*` jako jeden lub , ale wolą, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-246">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="2cfdc-247">Typy danych systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2cfdc-247">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="2cfdc-248">Zakresy typów danych</span><span class="sxs-lookup"><span data-stu-id="2cfdc-248">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="2cfdc-249">Struktury</span><span class="sxs-lookup"><span data-stu-id="2cfdc-249">Structs</span></span>

<span data-ttu-id="2cfdc-250">Struktury zarządzane są tworzone na stosie i nie są usuwane, dopóki metoda nie zwróci.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-250">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="2cfdc-251">Zgodnie z definicją są one "przypięte" (nie zostaną przeniesione przez GC).</span><span class="sxs-lookup"><span data-stu-id="2cfdc-251">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="2cfdc-252">Można również po prostu wziąć adres w niebezpiecznych bloków kodu, jeśli kod macierzysty nie będzie używać wskaźnika poza koniec bieżącej metody.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-252">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="2cfdc-253">Struktury Blittable są znacznie bardziej wydajne, ponieważ mogą być po prostu używane bezpośrednio przez warstwę organizowania.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-253">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="2cfdc-254">Spróbuj zrobić struktury blittable (na przykład, uniknąć `bool`).</span><span class="sxs-lookup"><span data-stu-id="2cfdc-254">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="2cfdc-255">Aby uzyskać więcej informacji, zobacz [Blittable typy](#blittable-types) sekcji.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-255">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="2cfdc-256">*Jeśli* struktura jest blittable, `sizeof()` należy `Marshal.SizeOf<MyStruct>()` użyć zamiast dla lepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-256">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="2cfdc-257">Jak wspomniano powyżej, można sprawdzić, czy typ jest blittable, próbując `GCHandle`utworzyć przypięty .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-257">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="2cfdc-258">Jeśli typ nie jest ciągiem lub `GCHandle.Alloc` uważany za `ArgumentException`blittable, zrzuci plik .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-258">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="2cfdc-259">Wskaźniki do struktur w definicjach muszą być `ref` przekazywane `unsafe` przez `*`lub używać i .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-259">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="2cfdc-260">✔️ DO dopasować zarządzane struktury jak najbliżej kształtu i nazwy, które są używane w oficjalnej dokumentacji platformy lub nagłówka.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-260">✔️ DO match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="2cfdc-261">✔️ do użycia języka C# `sizeof()` zamiast `Marshal.SizeOf<MyStruct>()` struktur blittable w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-261">✔️ DO use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="2cfdc-262">❌UNIKAJ `System.Delegate` używania pól lub `System.MulticastDelegate` pól do reprezentowania pól wskaźnika funkcji w strukturach.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-262">❌ AVOID using `System.Delegate` or `System.MulticastDelegate` fields to represent function pointer fields in structures.</span></span>

<span data-ttu-id="2cfdc-263">Ponieważ <xref:System.Delegate?displayProperty=fullName> <xref:System.MulticastDelegate?displayProperty=fullName> i nie mają wymaganego podpisu, nie gwarantują, że pełnomocnik przeszedł będzie zgodny z podpisem kod macierzysty oczekuje.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-263">Since <xref:System.Delegate?displayProperty=fullName> and <xref:System.MulticastDelegate?displayProperty=fullName> don't have a required signature, they don't guarantee that the delegate passed in will match the signature the native code expects.</span></span> <span data-ttu-id="2cfdc-264">Ponadto w .NET Framework i .NET Core kierowanie struktury `System.Delegate` `System.MulticastDelegate` zawierającej lub z jego reprezentacji macierzystej do obiektu zarządzanego może zdestabilizować środowisko uruchomieniowe, jeśli wartość pola w reprezentacji macierzystej nie jest wskaźnikiem funkcji, który zawija zarządzanego delegata.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-264">Additionally, in .NET Framework and .NET Core, marshaling a struct containing a `System.Delegate` or `System.MulticastDelegate` from its native representation to a managed object can destabilize the runtime if the value of the field in the native representation isn't a function pointer that wraps a managed delegate.</span></span> <span data-ttu-id="2cfdc-265">W wersji .NET 5 i `System.Delegate` nowszych kierowanie lub `System.MulticastDelegate` pole z reprezentacji natywnej do obiektu zarządzanego nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-265">In .NET 5 and later versions, marshaling a `System.Delegate` or `System.MulticastDelegate` field from a native representation to a managed object is not supported.</span></span> <span data-ttu-id="2cfdc-266">Użyj określonego typu delegata `System.Delegate` `System.MulticastDelegate`zamiast lub .</span><span class="sxs-lookup"><span data-stu-id="2cfdc-266">Use a specific delegate type instead of `System.Delegate` or `System.MulticastDelegate`.</span></span>

### <a name="fixed-buffers"></a><span data-ttu-id="2cfdc-267">Stałe bufory</span><span class="sxs-lookup"><span data-stu-id="2cfdc-267">Fixed Buffers</span></span>

<span data-ttu-id="2cfdc-268">Tablica `INT_PTR Reserved1[2]` taka jak musi być `IntPtr` zorganizowana do dwóch pól `Reserved1a` i `Reserved1b`.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-268">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="2cfdc-269">Gdy tablica natywna jest typem `fixed` pierwotnym, możemy użyć słowa kluczowego, aby napisać go trochę bardziej czysto.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-269">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="2cfdc-270">Na przykład `SYSTEM_PROCESS_INFORMATION` wygląda następująco w nagłówku macierzystym:</span><span class="sxs-lookup"><span data-stu-id="2cfdc-270">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="2cfdc-271">W języku C# możemy napisać to w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="2cfdc-271">In C#, we can write it like this:</span></span>

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

<span data-ttu-id="2cfdc-272">Istnieją jednak pewne gotchas ze stałymi buforami.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-272">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="2cfdc-273">Stałe bufory typów nietrwalonych nie będą poprawnie organizowane, więc tablica w miejscu musi zostać rozszerzona na wiele pojedynczych pól.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-273">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="2cfdc-274">Ponadto w programie .NET Framework i .NET Core przed 3.0, jeśli struktura zawierająca stałe pole buforu jest zagnieżdżona w strukturze nieduwalnej, stałe pole buforu nie zostanie poprawnie zorganizowane do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="2cfdc-274">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
