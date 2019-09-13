---
title: Najlepsze praktyki dotyczące natywnego współdziałania — platforma .NET
description: Poznaj najlepsze rozwiązania dotyczące współkorzystania ze składnikami macierzystymi w programie .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 0405fd5aef9d89fc1f47123ed358e6358656d95b
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70923769"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="45784-103">Najlepsze rozwiązania w zakresie współdziałania natywnego</span><span class="sxs-lookup"><span data-stu-id="45784-103">Native interoperability best practices</span></span>

<span data-ttu-id="45784-104">Program .NET oferuje różne sposoby dostosowywania natywnego kodu współdziałania.</span><span class="sxs-lookup"><span data-stu-id="45784-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="45784-105">Ten artykuł zawiera wskazówki, które są zgodne z zespołem .NET firmy Microsoft dotyczącym natywnej współdziałania.</span><span class="sxs-lookup"><span data-stu-id="45784-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="45784-106">Wskazówki ogólne</span><span class="sxs-lookup"><span data-stu-id="45784-106">General guidance</span></span>

<span data-ttu-id="45784-107">Wskazówki zawarte w tej sekcji dotyczą wszystkich scenariuszy międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="45784-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="45784-108">**✔️** Użyj tej samej nazwy i wielkości liter dla metod i parametrów jako metody natywnej, którą chcesz wywołać.</span><span class="sxs-lookup"><span data-stu-id="45784-108">**✔️ DO** use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="45784-109">**✔️ rozważyć** użycie tego samego nazewnictwa i wielkich liter w przypadku wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="45784-109">**✔️ CONSIDER** using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="45784-110">**✔️** Użyj typów .NET, które są mapowane bliżej typu natywnego.</span><span class="sxs-lookup"><span data-stu-id="45784-110">**✔️ DO** use .NET types that map closest to the native type.</span></span> <span data-ttu-id="45784-111">Na przykład, w C#, użyj `uint` , gdy typem natywnym `unsigned int`jest.</span><span class="sxs-lookup"><span data-stu-id="45784-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="45784-112">**✔️ są** używane `[In]` i `[Out]` atrybuty tylko wtedy, gdy zachowanie jest inne niż domyślne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="45784-112">**✔️ DO** only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="45784-113">**✔️ rozważyć** użycie <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> usługi do puli natywnych buforów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="45784-113">**✔️ CONSIDER** using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="45784-114">**✔️ Rozważ** zapakowanie deklaracji P/Invoke w klasie o tej samej nazwie i wielkości liter jako biblioteki natywnej.</span><span class="sxs-lookup"><span data-stu-id="45784-114">**✔️ CONSIDER** wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="45784-115">Dzięki `[DllImport]` temu atrybuty mogą C# `nameof` korzystać z funkcji języka w celu przekazania nazwy biblioteki natywnej i upewnienia się, że nie jest ona błędną nazwą biblioteki natywnej.</span><span class="sxs-lookup"><span data-stu-id="45784-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="45784-116">Ustawienia atrybutów DllImport</span><span class="sxs-lookup"><span data-stu-id="45784-116">DllImport attribute settings</span></span>

| <span data-ttu-id="45784-117">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="45784-117">Setting</span></span> | <span data-ttu-id="45784-118">Domyślny</span><span class="sxs-lookup"><span data-stu-id="45784-118">Default</span></span> | <span data-ttu-id="45784-119">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="45784-119">Recommendation</span></span> | <span data-ttu-id="45784-120">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="45784-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="45784-121">Zachowaj domyślne</span><span class="sxs-lookup"><span data-stu-id="45784-121">keep default</span></span>  | <span data-ttu-id="45784-122">Jeśli ta opcja jest jawnie ustawiona na false, Niepowodzenie zwracanych wartości HRESULT spowoduje włączenie wyjątków (a wartość zwracana w definicji zmieni się na wartość null).</span><span class="sxs-lookup"><span data-stu-id="45784-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="45784-123">zależy od interfejsu API</span><span class="sxs-lookup"><span data-stu-id="45784-123">depends on the API</span></span>  | <span data-ttu-id="45784-124">Ustaw tę wartość na true, jeśli interfejs API używa wartości GetLastError i użyj Marshal. metodę GetLastWin32Error, aby pobrać wartość.</span><span class="sxs-lookup"><span data-stu-id="45784-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="45784-125">Jeśli interfejs API ustawi warunek informujący o błędzie, należy uzyskać błąd przed wywołaniem innych wywołań, aby uniknąć niezamierzonego nadpisania.</span><span class="sxs-lookup"><span data-stu-id="45784-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="45784-126">`CharSet.None`, która powraca do `CharSet.Ansi` zachowania</span><span class="sxs-lookup"><span data-stu-id="45784-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="45784-127">Jawne użycie `CharSet.Unicode` lub `CharSet.Ansi` gdy ciągi lub znaki są obecne w definicji</span><span class="sxs-lookup"><span data-stu-id="45784-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="45784-128">Określa to kierowanie zachowania ciągów i to, `ExactSpelling` co `false`robi.</span><span class="sxs-lookup"><span data-stu-id="45784-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="45784-129">Pamiętaj, `CharSet.Ansi` że jest to w rzeczywistości UTF8 w systemie UNIX.</span><span class="sxs-lookup"><span data-stu-id="45784-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="45784-130">_Większość_ czasu Windows używa standardu Unicode, podczas gdy w systemie UNIX używa kodowania UTF8.</span><span class="sxs-lookup"><span data-stu-id="45784-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="45784-131">Więcej informacji na temat zestawów [znaków](./charset.md)można znaleźć w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="45784-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="45784-132">Ustaw tę wartość na true i uzyskaj niewielką korzyść w zakresie wydajności, ponieważ środowisko uruchomieniowe nie będzie szukać alternatywnych nazw funkcji z sufiksem "a" lub "w" w zależności od wartości `CharSet` ustawienia ("a" dla `CharSet.Ansi` i "w" dla `CharSet.Unicode`).</span><span class="sxs-lookup"><span data-stu-id="45784-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="45784-133">Parametry ciągu</span><span class="sxs-lookup"><span data-stu-id="45784-133">String parameters</span></span>

<span data-ttu-id="45784-134">Gdy zestaw znaków jest Unicode lub argument jest jawnie `[MarshalAs(UnmanagedType.LPWSTR)]` oznaczony jako _i_ ciąg jest przenoszona przez wartość (not `ref` lub `out`), ciąg zostanie przypięty i użyty bezpośrednio przez kod natywny (zamiast kopiować).</span><span class="sxs-lookup"><span data-stu-id="45784-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="45784-135">Pamiętaj, `[DllImport]` aby oznaczyć element `Charset.Unicode` jako, chyba że jawnie zachodzi konieczność traktowania ciągów znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="45784-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="45784-136">**❌ Nie** używać `[Out] string` parametrów.</span><span class="sxs-lookup"><span data-stu-id="45784-136">**❌ DO NOT** use `[Out] string` parameters.</span></span> <span data-ttu-id="45784-137">Parametry ciągu przesłane przez wartość z `[Out]` atrybutem mogą destabilizację środowiska uruchomieniowego, jeśli ciąg jest ciągiem z stażystami.</span><span class="sxs-lookup"><span data-stu-id="45784-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="45784-138">Zobacz więcej informacji na temat sposobu informowania o ciągach w dokumentacji dotyczącej programu <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45784-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="45784-139">**❌ Unikać** `StringBuilder` parametry.</span><span class="sxs-lookup"><span data-stu-id="45784-139">**❌ AVOID** `StringBuilder` parameters.</span></span> <span data-ttu-id="45784-140">`StringBuilder`kierowanie *zawsze* tworzy natywną kopię buforu.</span><span class="sxs-lookup"><span data-stu-id="45784-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="45784-141">W związku z tym może być wyjątkowo niewydajne.</span><span class="sxs-lookup"><span data-stu-id="45784-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="45784-142">Zapoznaj się z typowym scenariuszem wywoływania interfejsu API systemu Windows, który pobiera ciąg:</span><span class="sxs-lookup"><span data-stu-id="45784-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="45784-143">Utwórz SB o żądanej pojemności (przydzieli zarządzaną pojemność) **{1}**</span><span class="sxs-lookup"><span data-stu-id="45784-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="45784-144">wywoływanie</span><span class="sxs-lookup"><span data-stu-id="45784-144">Invoke</span></span>
   1. <span data-ttu-id="45784-145">Przydziela bufor natywny **{2}**</span><span class="sxs-lookup"><span data-stu-id="45784-145">Allocates a native buffer **{2}**</span></span>  
   2. <span data-ttu-id="45784-146">Kopiuje zawartość, jeśli `[In]` _( `StringBuilder` wartość domyślna parametru)_</span><span class="sxs-lookup"><span data-stu-id="45784-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>  
   3. <span data-ttu-id="45784-147">Kopiuje bufor macierzysty do nowo przydzielonej tablicy zarządzanej, jeśli `[Out]` **{3}** _(również `StringBuilder`domyślnie dla)_</span><span class="sxs-lookup"><span data-stu-id="45784-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>  
3. <span data-ttu-id="45784-148">`ToString()`alokuje jeszcze inną zarządzaną tablicę **{4}**</span><span class="sxs-lookup"><span data-stu-id="45784-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="45784-149">Jest to *{4}* alokacje w celu pobrania ciągu z kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="45784-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="45784-150">Najlepszym rozwiązaniem jest to, aby ograniczyć to użycie w innym wywołaniu `StringBuilder` , ale nadal tylko *1* przydział.</span><span class="sxs-lookup"><span data-stu-id="45784-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="45784-151">Znacznie lepiej jest używać bufora `ArrayPool`znaków i pamięci podręcznej, a następnie można przejść do przydziału `ToString()` dla kolejnych wywołań.</span><span class="sxs-lookup"><span data-stu-id="45784-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="45784-152">Innym problemem `StringBuilder` jest to, że zawsze kopiuje kopię zapasową buforu powrotu do pierwszej wartości null.</span><span class="sxs-lookup"><span data-stu-id="45784-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="45784-153">Jeśli przeszedł ciąg zakończony nieprzerwanie lub jest ciągiem o podwójnej wartości null, element P/Invoke jest niewłaściwy.</span><span class="sxs-lookup"><span data-stu-id="45784-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="45784-154">W `StringBuilder`przypadku *korzystania z* programu Gotcha, że pojemność nie obejmuje ukrytych wartości null, które zawsze **są uwzględniane w** ramach międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="45784-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="45784-155">Jest to często używane w przypadku, gdy większość interfejsów API ma rozmiar buforu, *łącznie* z wartością null.</span><span class="sxs-lookup"><span data-stu-id="45784-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="45784-156">Może to spowodować marnowanie/niepotrzebne alokacje.</span><span class="sxs-lookup"><span data-stu-id="45784-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="45784-157">Ponadto ta Gotcha uniemożliwia środowisko uruchomieniowe optymalizacji `StringBuilder` organizowania, aby zminimalizować kopie.</span><span class="sxs-lookup"><span data-stu-id="45784-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="45784-158">**✔️ rozważyć** użycie `char[]`s z `ArrayPool`.</span><span class="sxs-lookup"><span data-stu-id="45784-158">**✔️ CONSIDER** using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="45784-159">Aby uzyskać więcej informacji na temat organizowania ciągów, zobacz [domyślne kierowanie dla ciągów](../../framework/interop/default-marshaling-for-strings.md) i [Dostosowywanie organizowania ciągów](customize-parameter-marshaling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="45784-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="45784-160">__Specyficzne dla systemu Windows__</span><span class="sxs-lookup"><span data-stu-id="45784-160">__Windows Specific__</span></span>  
> <span data-ttu-id="45784-161">Dla `[Out]` ciągów, które domyślnie są `CoTaskMemFree` używane przez środowisko CLR do zwalniania ciągów lub `SysStringFree` ciągów, które `UnmanagedType.BSTR`są oznaczone jako.</span><span class="sxs-lookup"><span data-stu-id="45784-161">For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>  
<span data-ttu-id="45784-162">**W przypadku większości interfejsów API z buforem ciągu wyjściowego:**</span><span class="sxs-lookup"><span data-stu-id="45784-162">**For most APIs with an output string buffer:**</span></span>  
> <span data-ttu-id="45784-163">Liczba przesłanych znaków musi zawierać wartość null.</span><span class="sxs-lookup"><span data-stu-id="45784-163">The passed in character count must include the null.</span></span> <span data-ttu-id="45784-164">Jeśli zwracana wartość jest mniejsza niż przekazana liczba znaków, wywołanie zakończyło się pomyślnie, a wartość jest liczbą znaków *bez* końcowej wartości null.</span><span class="sxs-lookup"><span data-stu-id="45784-164">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="45784-165">W przeciwnym razie liczba jest wymaganym rozmiarem bufora, w *tym* znakiem null.</span><span class="sxs-lookup"><span data-stu-id="45784-165">Otherwise the count is the required size of the buffer *including* the null character.</span></span>  
>
> - <span data-ttu-id="45784-166">Przekaż 5, Pobierz 4: Ciąg zawiera 4 znaki o długości końcowej null.</span><span class="sxs-lookup"><span data-stu-id="45784-166">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="45784-167">Przekaż 5, Pobierz 6: Ciąg ma długość 5 znaków, a potrzeba przechowania wartości null w buforze zawierającym 6 znaków.</span><span class="sxs-lookup"><span data-stu-id="45784-167">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>  
> [<span data-ttu-id="45784-168">Typy danych systemu Windows dla ciągów</span><span class="sxs-lookup"><span data-stu-id="45784-168">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="45784-169">Parametry i pola logiczne</span><span class="sxs-lookup"><span data-stu-id="45784-169">Boolean parameters and fields</span></span>

<span data-ttu-id="45784-170">Wartości logiczne są łatwe w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="45784-170">Booleans are easy to mess up.</span></span> <span data-ttu-id="45784-171">Domyślnie środowisko .NET `bool` jest organizowane w systemie Windows `BOOL`, gdzie jest wartością 4-bajtową.</span><span class="sxs-lookup"><span data-stu-id="45784-171">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="45784-172">Jednak, i `bool` typy w C i C++ są *pojedynczym* bajtem. `_Bool`</span><span class="sxs-lookup"><span data-stu-id="45784-172">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="45784-173">Może to prowadzić do trudnej śledzenia błędów w postaci połowy wartości zwracanej zostanie odrzucone, co *spowoduje jedynie zmianę* wyniku.</span><span class="sxs-lookup"><span data-stu-id="45784-173">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="45784-174">Aby uzyskać więcej informacji o kierowaniu wartości `bool` .NET do języka C C++ `bool` lub typów, zobacz dokumentację dotyczącą [dostosowywania kierowania pól logicznych](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span><span class="sxs-lookup"><span data-stu-id="45784-174">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="45784-175">Identyfikatory GUID</span><span class="sxs-lookup"><span data-stu-id="45784-175">GUIDs</span></span>

<span data-ttu-id="45784-176">Identyfikatory GUID można używać bezpośrednio w sygnaturach.</span><span class="sxs-lookup"><span data-stu-id="45784-176">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="45784-177">Wiele interfejsów API `GUID&` systemu Windows korzysta z `REFIID`aliasów typu, takich jak.</span><span class="sxs-lookup"><span data-stu-id="45784-177">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="45784-178">Gdy są przesyłane przez odwołanie, mogą być przesyłane przez `ref` lub `[MarshalAs(UnmanagedType.LPStruct)]` z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="45784-178">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="45784-179">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="45784-179">GUID</span></span> | <span data-ttu-id="45784-180">Według-ref — identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="45784-180">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="45784-181">**❌ nie** Używać `[MarshalAs(UnmanagedType.LPStruct)]` dla elementów innych niż `ref` parametry GUID.</span><span class="sxs-lookup"><span data-stu-id="45784-181">**❌ DO NOT** Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="45784-182">Typy danych kopiowalnych</span><span class="sxs-lookup"><span data-stu-id="45784-182">Blittable types</span></span>

<span data-ttu-id="45784-183">Typy danych kopiowalnych są typami, które mają taką samą reprezentację na poziomie bitowym w kodzie zarządzanym i natywnym.</span><span class="sxs-lookup"><span data-stu-id="45784-183">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="45784-184">W związku z tym nie trzeba przekonwertowane do innego formatu, który ma być zorganizowany do i z kodu natywnego, a w miarę zwiększania wydajności powinny one być preferowane.</span><span class="sxs-lookup"><span data-stu-id="45784-184">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="45784-185">**Typy danych kopiowalnych:**</span><span class="sxs-lookup"><span data-stu-id="45784-185">**Blittable types:**</span></span>

- <span data-ttu-id="45784-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="45784-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="45784-187">niezagnieżdżone tablice jednowymiarowe typów danych kopiowalnych (na przykład `int[]`)</span><span class="sxs-lookup"><span data-stu-id="45784-187">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="45784-188">struktury i klasy ze stałym układem, które mają tylko typy wartości danych kopiowalnych dla pól wystąpień</span><span class="sxs-lookup"><span data-stu-id="45784-188">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="45784-189">układ stały wymaga `[StructLayout(LayoutKind.Sequential)]` lub`[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="45784-189">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="45784-190">struktury są `LayoutKind.Sequential` domyślnie, klasy są`LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="45784-190">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="45784-191">**NIE danych kopiowalnych:**</span><span class="sxs-lookup"><span data-stu-id="45784-191">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="45784-192">**Czasami danych kopiowalnych:**</span><span class="sxs-lookup"><span data-stu-id="45784-192">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="45784-193">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="45784-193">`char`, `string`</span></span>

<span data-ttu-id="45784-194">Gdy typy danych kopiowalnych są przesyłane przez odwołanie, są one po prostu przypięte przez organizatora, zamiast kopiować do buforu pośredniego.</span><span class="sxs-lookup"><span data-stu-id="45784-194">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="45784-195">(Klasy są z założenia przesyłane przez odwołanie, struktury są przesyłane przez odwołanie, gdy jest `ref` używany `out`z lub).</span><span class="sxs-lookup"><span data-stu-id="45784-195">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="45784-196">`char`jest danych kopiowalnych w tablicy jednowymiarowej **lub** , jeśli jest częścią typu, który zawiera, jest jawnie oznaczona `[StructLayout]` przy użyciu. `CharSet = CharSet.Unicode`</span><span class="sxs-lookup"><span data-stu-id="45784-196">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="45784-197">`string`jest danych kopiowalnych, jeśli nie jest zawarty w innym typie i jest przenoszona jako argument, który jest oznaczony za `[MarshalAs(UnmanagedType.LPWStr)]` pomocą `[DllImport]` lub ma `CharSet = CharSet.Unicode` ustawioną wartość.</span><span class="sxs-lookup"><span data-stu-id="45784-197">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="45784-198">Możesz sprawdzić, czy typ to danych kopiowalnych, próbując utworzyć przypięty `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="45784-198">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="45784-199">Jeśli typ nie jest ciągiem lub jest traktowany jako `GCHandle.Alloc` danych kopiowalnych, zostanie `ArgumentException`zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="45784-199">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="45784-200">**✔️** , gdy to możliwe, danych kopiowalnych struktury.</span><span class="sxs-lookup"><span data-stu-id="45784-200">**✔️ DO** make your structures blittable when possible.</span></span>

<span data-ttu-id="45784-201">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="45784-201">For more information, see:</span></span>

- [<span data-ttu-id="45784-202">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="45784-202">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)  
- [<span data-ttu-id="45784-203">Kierowanie typów</span><span class="sxs-lookup"><span data-stu-id="45784-203">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="45784-204">Utrzymywanie aktywności obiektów zarządzanych</span><span class="sxs-lookup"><span data-stu-id="45784-204">Keeping managed objects alive</span></span>

<span data-ttu-id="45784-205">`GC.KeepAlive()`Upewnij się, że obiekt pozostaje w zakresie, dopóki nie zostanie osiągnięta Metoda utrzymywania aktywności.</span><span class="sxs-lookup"><span data-stu-id="45784-205">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="45784-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)umożliwia Organizatorowi utrzymywanie obiektu na czas trwania elementu P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="45784-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="45784-207">Może być używany zamiast `IntPtr` podpisów metod.</span><span class="sxs-lookup"><span data-stu-id="45784-207">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="45784-208">`SafeHandle`efektywnie zastępuje tę klasę i powinny być używane zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="45784-208">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="45784-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)umożliwia Przypinanie obiektu zarządzanego i uzyskanie wskaźnika natywnego do niego.</span><span class="sxs-lookup"><span data-stu-id="45784-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="45784-210">Wzorzec podstawowy to:</span><span class="sxs-lookup"><span data-stu-id="45784-210">The basic pattern is:</span></span>  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="45784-211">Przypinanie nie jest domyślne `GCHandle`dla elementu.</span><span class="sxs-lookup"><span data-stu-id="45784-211">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="45784-212">Inny wzorzec główny polega na przekazaniu odwołania do zarządzanego obiektu za pomocą kodu natywnego i z powrotem do kodu zarządzanego, zazwyczaj przy użyciu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="45784-212">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="45784-213">Oto wzorzec:</span><span class="sxs-lookup"><span data-stu-id="45784-213">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="45784-214">Nie zapomnij `GCHandle` , że musi być jawnie zwolnione, aby uniknąć przecieków pamięci.</span><span class="sxs-lookup"><span data-stu-id="45784-214">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="45784-215">Typowe typy danych systemu Windows</span><span class="sxs-lookup"><span data-stu-id="45784-215">Common Windows data types</span></span>

<span data-ttu-id="45784-216">Poniżej znajduje się lista typów danych używanych w interfejsach API systemu Windows, C# które mają być używane podczas wywoływania kodu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="45784-216">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="45784-217">Następujące typy są takie same, jak w przypadku systemu Windows 32-bitowego i 64-bitowego, niezależnie od ich nazw.</span><span class="sxs-lookup"><span data-stu-id="45784-217">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="45784-218">Szerokość</span><span class="sxs-lookup"><span data-stu-id="45784-218">Width</span></span> | <span data-ttu-id="45784-219">Windows</span><span class="sxs-lookup"><span data-stu-id="45784-219">Windows</span></span>          | <span data-ttu-id="45784-220">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="45784-220">C (Windows)</span></span>          | <span data-ttu-id="45784-221">C#</span><span class="sxs-lookup"><span data-stu-id="45784-221">C#</span></span>       | <span data-ttu-id="45784-222">Różne</span><span class="sxs-lookup"><span data-stu-id="45784-222">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="45784-223">32</span><span class="sxs-lookup"><span data-stu-id="45784-223">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="45784-224">8</span><span class="sxs-lookup"><span data-stu-id="45784-224">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="45784-225">8</span><span class="sxs-lookup"><span data-stu-id="45784-225">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="45784-226">8</span><span class="sxs-lookup"><span data-stu-id="45784-226">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="45784-227">8</span><span class="sxs-lookup"><span data-stu-id="45784-227">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="45784-228">16</span><span class="sxs-lookup"><span data-stu-id="45784-228">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="45784-229">16</span><span class="sxs-lookup"><span data-stu-id="45784-229">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="45784-230">16</span><span class="sxs-lookup"><span data-stu-id="45784-230">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="45784-231">16</span><span class="sxs-lookup"><span data-stu-id="45784-231">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="45784-232">16</span><span class="sxs-lookup"><span data-stu-id="45784-232">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="45784-233">32</span><span class="sxs-lookup"><span data-stu-id="45784-233">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="45784-234">32</span><span class="sxs-lookup"><span data-stu-id="45784-234">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="45784-235">32</span><span class="sxs-lookup"><span data-stu-id="45784-235">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="45784-236">32</span><span class="sxs-lookup"><span data-stu-id="45784-236">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="45784-237">64</span><span class="sxs-lookup"><span data-stu-id="45784-237">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="45784-238">64</span><span class="sxs-lookup"><span data-stu-id="45784-238">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="45784-239">64</span><span class="sxs-lookup"><span data-stu-id="45784-239">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="45784-240">64</span><span class="sxs-lookup"><span data-stu-id="45784-240">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="45784-241">64</span><span class="sxs-lookup"><span data-stu-id="45784-241">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="45784-242">32</span><span class="sxs-lookup"><span data-stu-id="45784-242">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="45784-243">32</span><span class="sxs-lookup"><span data-stu-id="45784-243">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="45784-244">Następujące typy, które są wskaźnikami, są zgodne z szerokością platformy.</span><span class="sxs-lookup"><span data-stu-id="45784-244">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="45784-245">Użyj `IntPtr` / tego elementu`UIntPtr` .</span><span class="sxs-lookup"><span data-stu-id="45784-245">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="45784-246">Typy wskaźników ze znakiem `IntPtr`(Użyj)</span><span class="sxs-lookup"><span data-stu-id="45784-246">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="45784-247">Niepodpisane typy wskaźnika ( `UIntPtr`Użyj)</span><span class="sxs-lookup"><span data-stu-id="45784-247">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="45784-248">System Windows `PVOID` , który jest C `void*` , może `IntPtr` być zorganizowany jako lub `UIntPtr`, ale preferowany `void*` , jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="45784-248">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="45784-249">Typy danych systemu Windows</span><span class="sxs-lookup"><span data-stu-id="45784-249">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="45784-250">Zakresy typu danych</span><span class="sxs-lookup"><span data-stu-id="45784-250">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="45784-251">Struktury</span><span class="sxs-lookup"><span data-stu-id="45784-251">Structs</span></span>

<span data-ttu-id="45784-252">Zarządzane struktury są tworzone na stosie i nie są usuwane, dopóki metoda nie zwróci metody.</span><span class="sxs-lookup"><span data-stu-id="45784-252">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="45784-253">Według definicji są one "przypięte" (nie są przenoszone przez wykaz globalny).</span><span class="sxs-lookup"><span data-stu-id="45784-253">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="45784-254">Można również po prostu przełączyć adres w niebezpieczny blok kodu, jeśli kod natywny nie będzie używać wskaźnika poza końcem bieżącej metody.</span><span class="sxs-lookup"><span data-stu-id="45784-254">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="45784-255">Struktury danych kopiowalnych są znacznie bardziej wydajne, ponieważ mogą być używane bezpośrednio przez warstwę kierującą.</span><span class="sxs-lookup"><span data-stu-id="45784-255">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="45784-256">Spróbuj utworzyć struktury danych kopiowalnych (na przykład unikać `bool`).</span><span class="sxs-lookup"><span data-stu-id="45784-256">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="45784-257">Aby uzyskać więcej informacji, zobacz sekcję [typy danych kopiowalnych](#blittable-types) .</span><span class="sxs-lookup"><span data-stu-id="45784-257">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="45784-258">*Jeśli* struktura jest danych kopiowalnych, użyj `sizeof()` zamiast niej `Marshal.SizeOf<MyStruct>()` , aby uzyskać lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="45784-258">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="45784-259">Jak wspomniano powyżej, można sprawdzić, czy typ to danych kopiowalnych, próbując utworzyć przypięty `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="45784-259">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="45784-260">Jeśli typ nie jest ciągiem lub uznano za danych kopiowalnych, `GCHandle.Alloc` spowoduje to `ArgumentException`zgłoszenie.</span><span class="sxs-lookup"><span data-stu-id="45784-260">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="45784-261">Wskaźniki do struktur w definicjach muszą być przesyłane przez `ref` `unsafe` lub i `*`.</span><span class="sxs-lookup"><span data-stu-id="45784-261">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="45784-262">**✔️** być zgodna z zarządzaną strukturą jak najbliżej kształtu i nazw, które są używane w oficjalnej dokumentacji lub nagłówku platformy.</span><span class="sxs-lookup"><span data-stu-id="45784-262">**✔️ DO** match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="45784-263">aby zwiększyć wydajność, C# `sizeof()` ✔️ używać `Marshal.SizeOf<MyStruct>()` danych kopiowalnych zamiast for for Structure.</span><span class="sxs-lookup"><span data-stu-id="45784-263">**✔️ DO** use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="45784-264">Tablica, taka `INT_PTR Reserved1[2]` jak musi być organizowana do dwóch `IntPtr` pól, `Reserved1a` i `Reserved1b`.</span><span class="sxs-lookup"><span data-stu-id="45784-264">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="45784-265">Gdy natywna tablica jest typem pierwotnym, możemy użyć `fixed` słowa kluczowego, aby napisać je nieco bardziej czysty.</span><span class="sxs-lookup"><span data-stu-id="45784-265">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="45784-266">Na przykład `SYSTEM_PROCESS_INFORMATION` wygląda to w postaci natywnego nagłówka:</span><span class="sxs-lookup"><span data-stu-id="45784-266">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="45784-267">W C#programie możemy napisać następujący element:</span><span class="sxs-lookup"><span data-stu-id="45784-267">In C#, we can write it like this:</span></span>

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

<span data-ttu-id="45784-268">Istnieje jednak kilka pytania dotyczące usługi z stałymi buforami.</span><span class="sxs-lookup"><span data-stu-id="45784-268">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="45784-269">Stałe bufory typów innych niż danych kopiowalnych nie będą poprawnie organizowane, więc tablica w miejscu musi być rozwijana do wielu pojedynczych pól.</span><span class="sxs-lookup"><span data-stu-id="45784-269">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="45784-270">Ponadto w .NET Framework i .NET Core przed 3,0, jeśli struktura zawierająca pole stałego buforu jest zagnieżdżona w strukturze innej niż danych kopiowalnych, stałe pole buforu nie będzie poprawnie organizowane w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="45784-270">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
