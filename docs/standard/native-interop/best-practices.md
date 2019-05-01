---
title: Współdziałanie natywne najlepsze rozwiązania — .NET
description: Dowiedz się, najlepsze rozwiązania dotyczące komunikacji z usługą składnikami macierzystymi na platformie .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 6702d469abf317b3b1f545ce79b980e8581ab5f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973605"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="01c5a-103">Współdziałanie natywne najlepszych rozwiązań</span><span class="sxs-lookup"><span data-stu-id="01c5a-103">Native interoperability best practices</span></span>

<span data-ttu-id="01c5a-104">.NET zapewnia szereg sposobów dostosowywania kodu interoperacyjności macierzystej.</span><span class="sxs-lookup"><span data-stu-id="01c5a-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="01c5a-105">Ten artykuł zawiera wskazówki, które zespoły .NET firmy Microsoft należy wykonać w przypadku interoperacyjności macierzystej.</span><span class="sxs-lookup"><span data-stu-id="01c5a-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="01c5a-106">Wskazówki ogólne</span><span class="sxs-lookup"><span data-stu-id="01c5a-106">General guidance</span></span>

<span data-ttu-id="01c5a-107">Wskazówki zawarte w tej sekcji ma zastosowanie do wszystkich scenariuszy międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="01c5a-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="01c5a-108">**CZY ✔️** użyć tych samych nazw i wielkości liter dla metody i parametrów jako metodę natywną ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="01c5a-108">**✔️ DO** use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="01c5a-109">**ROZWAŻ ✔️** przy użyciu tych samych nazw i wielkości liter dla wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="01c5a-109">**✔️ CONSIDER** using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="01c5a-110">**CZY ✔️** używanie typów .NET, znajdujący się najbliżej mapowane na typ macierzysty.</span><span class="sxs-lookup"><span data-stu-id="01c5a-110">**✔️ DO** use .NET types that map closest to the native type.</span></span> <span data-ttu-id="01c5a-111">Na przykład w C#, użyj `uint` po typ natywny `unsigned int`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="01c5a-112">**CZY ✔️** składać się tylko `[In]` i `[Out]` atrybuty, gdy zachowanie zostanie różni się od zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="01c5a-112">**✔️ DO** only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="01c5a-113">**ROZWAŻ ✔️** przy użyciu <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> do puli buforów Twoja natywna tablica.</span><span class="sxs-lookup"><span data-stu-id="01c5a-113">**✔️ CONSIDER** using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="01c5a-114">**ROZWAŻ ✔️** opakowujące aplikacje usługi deklaracje P/Invoke w klasie za pomocą tej samej nazwie i wielkość liter jak natywne biblioteki.</span><span class="sxs-lookup"><span data-stu-id="01c5a-114">**✔️ CONSIDER** wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="01c5a-115">Dzięki temu Twoje `[DllImport]` atrybutów, które mają używać C# `nameof` funkcji języka, aby przekazać nazwę bibliotekę natywną i upewnij się, że nie wpiszesz nazwę bibliotekę natywną.</span><span class="sxs-lookup"><span data-stu-id="01c5a-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="01c5a-116">Ustawienia atrybut DllImport</span><span class="sxs-lookup"><span data-stu-id="01c5a-116">DllImport attribute settings</span></span>

| <span data-ttu-id="01c5a-117">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="01c5a-117">Setting</span></span> | <span data-ttu-id="01c5a-118">Domyślny</span><span class="sxs-lookup"><span data-stu-id="01c5a-118">Default</span></span> | <span data-ttu-id="01c5a-119">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="01c5a-119">Recommendation</span></span> | <span data-ttu-id="01c5a-120">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="01c5a-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="01c5a-121">Zachowaj domyślne</span><span class="sxs-lookup"><span data-stu-id="01c5a-121">keep default</span></span>  | <span data-ttu-id="01c5a-122">Jeśli jawnie ustawiono na zwracane wartości HRESULT false, zakończone niepowodzeniem, zostanie włączony do wyjątków (i wartość zwracana w definicji staje się wartości null w wyniku).</span><span class="sxs-lookup"><span data-stu-id="01c5a-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="01c5a-123">zależy od interfejsu API</span><span class="sxs-lookup"><span data-stu-id="01c5a-123">depends on the API</span></span>  | <span data-ttu-id="01c5a-124">Ustaw na wartość true, jeśli interfejs API korzysta GetLastError i użyj Marshal.GetLastWin32Error, aby uzyskać wartość.</span><span class="sxs-lookup"><span data-stu-id="01c5a-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="01c5a-125">Jeśli interfejs API określa warunek, stwierdzający, że ma błąd, komunikat o błędzie przed wprowadzeniem innych wywołań, aby uniknąć przypadkowego on zastąpiony.</span><span class="sxs-lookup"><span data-stu-id="01c5a-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="01c5a-126">`CharSet.None`, która przechodzi do `CharSet.Ansi` zachowanie</span><span class="sxs-lookup"><span data-stu-id="01c5a-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="01c5a-127">Jawnie użyć `CharSet.Unicode` lub `CharSet.Ansi` kiedy ciągów lub znaki są obecne w definicji</span><span class="sxs-lookup"><span data-stu-id="01c5a-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="01c5a-128">Określa zachowanie kierujące ciągi i co `ExactSpelling` gdy `false`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-128">This specifies marshalling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="01c5a-129">Należy pamiętać, że `CharSet.Ansi` jest faktycznie UTF8 w systemach Unix.</span><span class="sxs-lookup"><span data-stu-id="01c5a-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="01c5a-130">_Większość_ czasu Windows używa Unicode, podczas gdy Unix używa UTF8.</span><span class="sxs-lookup"><span data-stu-id="01c5a-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="01c5a-131">Zobacz więcej informacji na [dokumentację dotyczącą zestawów znaków](./charset.md).</span><span class="sxs-lookup"><span data-stu-id="01c5a-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="01c5a-132">Ustaw tę wartość true, i uzyskać korzyści wydajności niewielkie, ponieważ środowisko wykonawcze nie będzie szukać funkcji alternatywne nazwy z sufiksem "A" lub "W" w zależności od wartości `CharSet` ustawienie ("A", aby uzyskać `CharSet.Ansi` i "T" dla `CharSet.Unicode`).</span><span class="sxs-lookup"><span data-stu-id="01c5a-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="01c5a-133">Parametry ciągu</span><span class="sxs-lookup"><span data-stu-id="01c5a-133">String parameters</span></span>

<span data-ttu-id="01c5a-134">Gdy zestaw znaków jest Unicode lub argument jest jawnie oznaczona jako `[MarshalAs(UnmanagedType.LPWSTR)]` _i_ ten ciąg jest przekazywany przez wartość (nie `ref` lub `out`), ciąg zostanie przypięty i używana bezpośrednio przez kod natywny (zamiast skopiowany).</span><span class="sxs-lookup"><span data-stu-id="01c5a-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="01c5a-135">Pamiętaj, aby oznaczyć `[DllImport]` jako `Charset.Unicode` , chyba że jawnie ma ANSI postępowanie z Twoimi ciągami.</span><span class="sxs-lookup"><span data-stu-id="01c5a-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="01c5a-136">**NIE OBSŁUGUJĄ ❌** użyj `[Out] string` parametrów.</span><span class="sxs-lookup"><span data-stu-id="01c5a-136">**❌ DO NOT** use `[Out] string` parameters.</span></span> <span data-ttu-id="01c5a-137">Ciąg parametrów przekazywanych przez wartość z `[Out]` atrybutu mogą destabilizować środowisko wykonawcze, jeśli ciąg jest ciągiem interned.</span><span class="sxs-lookup"><span data-stu-id="01c5a-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="01c5a-138">Zobacz więcej informacji na temat w dokumentacji dotyczącej wewnętrzne przygotowanie ciągu <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01c5a-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="01c5a-139">**Należy UNIKAĆ ❌** `StringBuilder` parametrów.</span><span class="sxs-lookup"><span data-stu-id="01c5a-139">**❌ AVOID** `StringBuilder` parameters.</span></span> <span data-ttu-id="01c5a-140">`StringBuilder` kierowania *zawsze* tworzona jest kopia natywnych buforu.</span><span class="sxs-lookup"><span data-stu-id="01c5a-140">`StringBuilder` marshalling *always* creates a native buffer copy.</span></span> <span data-ttu-id="01c5a-141">W efekcie może być bardzo mało wydajne.</span><span class="sxs-lookup"><span data-stu-id="01c5a-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="01c5a-142">Wykonaj typowy scenariusz wywołania interfejsu API Windows, która przyjmuje ciąg:</span><span class="sxs-lookup"><span data-stu-id="01c5a-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="01c5a-143">Utwórz SB żądaną wydajność (przydziela pojemność zarządzanego) **{1}**</span><span class="sxs-lookup"><span data-stu-id="01c5a-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="01c5a-144">wywoływanie</span><span class="sxs-lookup"><span data-stu-id="01c5a-144">Invoke</span></span>
   1. <span data-ttu-id="01c5a-145">Przydziela bufor natywne **{2}**</span><span class="sxs-lookup"><span data-stu-id="01c5a-145">Allocates a native buffer **{2}**</span></span>  
   2. <span data-ttu-id="01c5a-146">Kopiuje zawartość, jeśli `[In]` _(wartość domyślna dla `StringBuilder` parametru)_</span><span class="sxs-lookup"><span data-stu-id="01c5a-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>  
   3. <span data-ttu-id="01c5a-147">Kopiuje bufor natywnej do nowo przydzielonego tablicy zarządzanej, jeśli `[Out]` **{3}** _(również wartość domyślna dla `StringBuilder`)_</span><span class="sxs-lookup"><span data-stu-id="01c5a-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>  
3. <span data-ttu-id="01c5a-148">`ToString()` przydziela kolejny tablicy zarządzanej **{4}**</span><span class="sxs-lookup"><span data-stu-id="01c5a-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="01c5a-149">Oznacza to *{4}* alokacji można pobrać parametrów z kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="01c5a-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="01c5a-150">Najlepiej, można zrobić, aby ograniczyć to jest to ponowne użycie `StringBuilder` w inne połączenie, ale nadal tylko pozwala to zaoszczędzić *1* alokacji.</span><span class="sxs-lookup"><span data-stu-id="01c5a-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="01c5a-151">Znacznie lepiej używać i pamięci podręcznej buforu znaków, z `ArrayPool`-następnie można uzyskać w dół do właśnie alokacji dla `ToString()` w kolejnych wywołaniach.</span><span class="sxs-lookup"><span data-stu-id="01c5a-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="01c5a-152">Problem z `StringBuilder` jest zawsze kopiuje buforze kopii zapasowej pierwszej wartości null.</span><span class="sxs-lookup"><span data-stu-id="01c5a-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="01c5a-153">Jeśli przekazany ciąg Wstecz nie jest zakończony lub ciąg przerwany wartością null podwójnej precyzji, metody P/Invoke, jest ona niepoprawna w najlepszym.</span><span class="sxs-lookup"><span data-stu-id="01c5a-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="01c5a-154">Jeśli możesz *czy* użyj `StringBuilder`, jeden ostatnie problemy jest, że pojemność nie **nie** obejmują ukryte wartość null, co jest zawsze uwzględnione w międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="01c5a-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="01c5a-155">Często użytkownicy będą mogli uzyskać dostęp do tej nieprawidłowy, ponieważ większość interfejsów API mają rozmiar buforu *tym* o wartości null.</span><span class="sxs-lookup"><span data-stu-id="01c5a-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="01c5a-156">Może to spowodować zmarnowany niepotrzebnych alokacji.</span><span class="sxs-lookup"><span data-stu-id="01c5a-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="01c5a-157">Ponadto to problemy zapobiega środowiska uruchomieniowego optymalizacji `StringBuilder` zarządzany, aby zminimalizować kopii.</span><span class="sxs-lookup"><span data-stu-id="01c5a-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshalling to minimize copies.</span></span>

<span data-ttu-id="01c5a-158">**ROZWAŻ ✔️** przy użyciu `char[]`s z `ArrayPool`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-158">**✔️ CONSIDER** using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="01c5a-159">Aby uzyskać więcej informacji na temat kierowania ciągu, zobacz [domyślne kierowania dla ciągów](../../framework/interop/default-marshaling-for-strings.md) i [Dostosowywanie kierowania ciągu](customize-parameter-marshalling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="01c5a-159">For more information on string marshalling, see [Default Marshalling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshalling](customize-parameter-marshalling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="01c5a-160">__Windows określonego__</span><span class="sxs-lookup"><span data-stu-id="01c5a-160">__Windows Specific__</span></span>  
> <span data-ttu-id="01c5a-161">Dla `[Out]` użyje ciągi CLR `CoTaskMemFree` domyślnie, aby zwolnić ciągów lub `SysStringFree` dla ciągów, które są oznaczone jako `UnmanagedType.BSTR`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-161">For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>  
<span data-ttu-id="01c5a-162">**Dla większości interfejsów API za pomocą buforu ciągu wyjściowego:**</span><span class="sxs-lookup"><span data-stu-id="01c5a-162">**For most APIs with an output string buffer:**</span></span>  
> <span data-ttu-id="01c5a-163">Przekazany w znaku count musi zawierać wartości null.</span><span class="sxs-lookup"><span data-stu-id="01c5a-163">The passed in character count must include the null.</span></span> <span data-ttu-id="01c5a-164">Jeśli zwracana wartość jest mniejsza niż przekazany w liczba znaków wywołanie zakończy się pomyślnie, jak i wartość jest liczbą znaków *bez* końcową wartość null.</span><span class="sxs-lookup"><span data-stu-id="01c5a-164">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="01c5a-165">W przeciwnym razie licznik jest wymagany rozmiar buforu *tym* znaku null.</span><span class="sxs-lookup"><span data-stu-id="01c5a-165">Otherwise the count is the required size of the buffer *including* the null character.</span></span>  
> - <span data-ttu-id="01c5a-166">Przekaż 5, Pobierz 4: Ten ciąg jest 4 znaków długo z końcową wartość null.</span><span class="sxs-lookup"><span data-stu-id="01c5a-166">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="01c5a-167">Przekaż 5, Pobierz 6: Ten ciąg jest 5 znaków muszą 6 znaków bufor do przechowywania wartości null.</span><span class="sxs-lookup"><span data-stu-id="01c5a-167">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>  
> [<span data-ttu-id="01c5a-168">Typy danych Windows dla ciągów</span><span class="sxs-lookup"><span data-stu-id="01c5a-168">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="01c5a-169">Wartość logiczna parametry i pola</span><span class="sxs-lookup"><span data-stu-id="01c5a-169">Boolean parameters and fields</span></span>

<span data-ttu-id="01c5a-170">Wartości logiczne są łatwe do awarię.</span><span class="sxs-lookup"><span data-stu-id="01c5a-170">Booleans are easy to mess up.</span></span> <span data-ttu-id="01c5a-171">Domyślnie .NET `bool` jest skierowany do Windows `BOOL`, gdzie jest to wartość 4-bajtowe.</span><span class="sxs-lookup"><span data-stu-id="01c5a-171">By default, a .NET `bool` is marshalled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="01c5a-172">Jednak `_Bool`, i `bool` typy w językach C i C++ są *pojedynczego* bajtów.</span><span class="sxs-lookup"><span data-stu-id="01c5a-172">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="01c5a-173">Może to prowadzić do trudne do śledzenia usterek jako pół wartość zwracaną zostaną odrzucone, który będzie tylko *potencjalnie* zmienić wynik.</span><span class="sxs-lookup"><span data-stu-id="01c5a-173">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="01c5a-174">Aby uzyskać więcej informacji na temat kierowania .NET `bool` wartości języka C lub C++ `bool` typów, zobacz dokumentację na [Dostosowywanie pola logicznych kierowania](customize-struct-marshalling.md#customizing-boolean-field-marshalling).</span><span class="sxs-lookup"><span data-stu-id="01c5a-174">For more for information on marshalling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshalling](customize-struct-marshalling.md#customizing-boolean-field-marshalling).</span></span>

## <a name="guids"></a><span data-ttu-id="01c5a-175">Identyfikatory GUID</span><span class="sxs-lookup"><span data-stu-id="01c5a-175">GUIDs</span></span>

<span data-ttu-id="01c5a-176">Identyfikatory GUID są użyteczne bezpośrednio w sygnaturach.</span><span class="sxs-lookup"><span data-stu-id="01c5a-176">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="01c5a-177">Wiele interfejsów API Windows `GUID&` aliasów, takich jak typów `REFIID`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-177">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="01c5a-178">W przypadku przekazywany przez odwołanie, ich można albo być przekazywany `ref` lub `[MarshalAs(UnmanagedType.LPStruct)]` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="01c5a-178">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="01c5a-179">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="01c5a-179">GUID</span></span> | <span data-ttu-id="01c5a-180">Identyfikator GUID przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="01c5a-180">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="01c5a-181">**NIE OBSŁUGUJĄ ❌** użyj `[MarshalAs(UnmanagedType.LPStruct)]` dla żadnych innych niż `ref` parametrów identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="01c5a-181">**❌ DO NOT** Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="01c5a-182">Typy Kopiowalne</span><span class="sxs-lookup"><span data-stu-id="01c5a-182">Blittable types</span></span>

<span data-ttu-id="01c5a-183">Typy Kopiowalne są typy, które mają tę samą reprezentację bitowy poziom w kodu zarządzanego i natywnego.</span><span class="sxs-lookup"><span data-stu-id="01c5a-183">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="01c5a-184">Jako takie nie należy do innego formatu w celu skierowany, do i z kodu natywnego, a ponieważ zwiększa to wydajność powinna być preferowane.</span><span class="sxs-lookup"><span data-stu-id="01c5a-184">As such they do not need to be converted to another format to be marshalled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="01c5a-185">**Typy Kopiowalne:**</span><span class="sxs-lookup"><span data-stu-id="01c5a-185">**Blittable types:**</span></span>

- <span data-ttu-id="01c5a-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="01c5a-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="01c5a-187">tablice jednowymiarowe-nested typy danych kopiowalnych (na przykład `int[]`)</span><span class="sxs-lookup"><span data-stu-id="01c5a-187">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="01c5a-188">struktur i klas o stałym układzie, na których znajduje się wartość danych kopiowalnych na przykład typy pól</span><span class="sxs-lookup"><span data-stu-id="01c5a-188">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="01c5a-189">wymaga stałym układzie `[StructLayout(LayoutKind.Sequential)]` lub `[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="01c5a-189">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="01c5a-190">struktury są `LayoutKind.Sequential` są domyślnie klasy `LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="01c5a-190">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="01c5a-191">**NIE kopiowalne:**</span><span class="sxs-lookup"><span data-stu-id="01c5a-191">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="01c5a-192">**CZASAMI kopiowalne:**</span><span class="sxs-lookup"><span data-stu-id="01c5a-192">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="01c5a-193">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="01c5a-193">`char`, `string`</span></span>

<span data-ttu-id="01c5a-194">Gdy typy danych kopiowalnych są przekazywane przez odwołanie, są one po prostu przypiętych przez szeregujący zamiast kopiowane do pośredniego buforu.</span><span class="sxs-lookup"><span data-stu-id="01c5a-194">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="01c5a-195">(Klasy natury są przekazywane przez odwołanie, struktur są przekazywane przez odwołanie, gdy jest używane z `ref` lub `out`.)</span><span class="sxs-lookup"><span data-stu-id="01c5a-195">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="01c5a-196">`char` jest możliwość kopiowania w tablicy jednowymiarowej **lub** Jeśli jest on częścią typu, który zawiera on jest jawnie oznaczona za pomocą `[StructLayout]` z `CharSet = CharSet.Unicode`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-196">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="01c5a-197">`string` jest możliwość kopiowania, jeśli nie jest on zawarty w innym typem i jest przekazywany jako argument, który jest oznaczony przy użyciu `[MarshalAs(UnmanagedType.LPWStr)]` lub `[DllImport]` ma `CharSet = CharSet.Unicode` zestawu.</span><span class="sxs-lookup"><span data-stu-id="01c5a-197">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="01c5a-198">Zostanie wyświetlony, jeśli typ jest danych kopiowalnych, próbując utworzyć z przypiętym `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-198">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="01c5a-199">Jeśli typ nie jest ciągiem lub uznawane za danych kopiowalnych, `GCHandle.Alloc` zgłosi `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-199">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="01c5a-200">**CZY ✔️** wprowadzić swoje struktur danych kopiowalnych, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="01c5a-200">**✔️ DO** make your structures blittable when possible.</span></span>

<span data-ttu-id="01c5a-201">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="01c5a-201">For more information, see:</span></span>

- [<span data-ttu-id="01c5a-202">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="01c5a-202">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)  
- [<span data-ttu-id="01c5a-203">Typ zarządzany</span><span class="sxs-lookup"><span data-stu-id="01c5a-203">Type Marshalling</span></span>](type-marshalling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="01c5a-204">Utrzymywanie zarządzane obiekty aktywne</span><span class="sxs-lookup"><span data-stu-id="01c5a-204">Keeping managed objects alive</span></span>

<span data-ttu-id="01c5a-205">`GC.KeepAlive()` pewność, że obiekt pozostaje w zakresie, dopóki nie zostanie osiągnięty jako metoda utrzymywania aktywności.</span><span class="sxs-lookup"><span data-stu-id="01c5a-205">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="01c5a-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) Umożliwia szeregujący zapewnienie obiekt podtrzymania połączenia dla czasu trwania elementu P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="01c5a-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="01c5a-207">Mogą być używane zamiast `IntPtr` w podpisy metod.</span><span class="sxs-lookup"><span data-stu-id="01c5a-207">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="01c5a-208">`SafeHandle` skutecznie zastępuje tej klasy i powinny być używane zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="01c5a-208">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="01c5a-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) Umożliwia przypinanie obiektu zarządzanego i uzyskiwania wskaźnik natywny.</span><span class="sxs-lookup"><span data-stu-id="01c5a-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="01c5a-210">Podstawowy wzorzec jest:</span><span class="sxs-lookup"><span data-stu-id="01c5a-210">The basic pattern is:</span></span>  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="01c5a-211">Przypinanie nie jest ustawieniem domyślnym dla `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-211">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="01c5a-212">Główne wzorzec dotyczy przekazywaniem odwołań do obiektu zarządzanego za pośrednictwem kodu natywnego i powrót do kodu zarządzanego, zwykle za pomocą wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="01c5a-212">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="01c5a-213">Poniżej przedstawiono wzorzec:</span><span class="sxs-lookup"><span data-stu-id="01c5a-213">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="01c5a-214">Nie należy zapominać, że `GCHandle` musi jawnie zwolniona w celu uniknięcia przecieków pamięci.</span><span class="sxs-lookup"><span data-stu-id="01c5a-214">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="01c5a-215">Standardowe typy danych Windows</span><span class="sxs-lookup"><span data-stu-id="01c5a-215">Common Windows data types</span></span>

<span data-ttu-id="01c5a-216">W tym miejscu znajduje się lista typów danych najczęściej używanych interfejsów API Windows, które C# typów do użycia podczas wywoływania w kodzie Windows.</span><span class="sxs-lookup"><span data-stu-id="01c5a-216">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="01c5a-217">Taki sam rozmiar na 32-bitowych i 64-bitowych Windows, niezależnie od ich nazwy są następujące typy.</span><span class="sxs-lookup"><span data-stu-id="01c5a-217">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="01c5a-218">Szerokość</span><span class="sxs-lookup"><span data-stu-id="01c5a-218">Width</span></span> | <span data-ttu-id="01c5a-219">Windows</span><span class="sxs-lookup"><span data-stu-id="01c5a-219">Windows</span></span>          | <span data-ttu-id="01c5a-220">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="01c5a-220">C (Windows)</span></span>          | <span data-ttu-id="01c5a-221">C#</span><span class="sxs-lookup"><span data-stu-id="01c5a-221">C#</span></span>       | <span data-ttu-id="01c5a-222">Alternatywna</span><span class="sxs-lookup"><span data-stu-id="01c5a-222">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="01c5a-223">32</span><span class="sxs-lookup"><span data-stu-id="01c5a-223">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="01c5a-224">8</span><span class="sxs-lookup"><span data-stu-id="01c5a-224">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="01c5a-225">8</span><span class="sxs-lookup"><span data-stu-id="01c5a-225">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="01c5a-226">8</span><span class="sxs-lookup"><span data-stu-id="01c5a-226">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="01c5a-227">8</span><span class="sxs-lookup"><span data-stu-id="01c5a-227">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="01c5a-228">16</span><span class="sxs-lookup"><span data-stu-id="01c5a-228">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="01c5a-229">16</span><span class="sxs-lookup"><span data-stu-id="01c5a-229">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="01c5a-230">16</span><span class="sxs-lookup"><span data-stu-id="01c5a-230">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="01c5a-231">16</span><span class="sxs-lookup"><span data-stu-id="01c5a-231">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="01c5a-232">16</span><span class="sxs-lookup"><span data-stu-id="01c5a-232">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="01c5a-233">32</span><span class="sxs-lookup"><span data-stu-id="01c5a-233">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="01c5a-234">32</span><span class="sxs-lookup"><span data-stu-id="01c5a-234">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="01c5a-235">32</span><span class="sxs-lookup"><span data-stu-id="01c5a-235">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="01c5a-236">32</span><span class="sxs-lookup"><span data-stu-id="01c5a-236">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="01c5a-237">64</span><span class="sxs-lookup"><span data-stu-id="01c5a-237">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="01c5a-238">64</span><span class="sxs-lookup"><span data-stu-id="01c5a-238">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="01c5a-239">64</span><span class="sxs-lookup"><span data-stu-id="01c5a-239">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="01c5a-240">64</span><span class="sxs-lookup"><span data-stu-id="01c5a-240">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="01c5a-241">64</span><span class="sxs-lookup"><span data-stu-id="01c5a-241">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="01c5a-242">32</span><span class="sxs-lookup"><span data-stu-id="01c5a-242">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="01c5a-243">32</span><span class="sxs-lookup"><span data-stu-id="01c5a-243">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="01c5a-244">Następujące typy, są wskaźnikami, postępuj zgodnie z szerokość platformy.</span><span class="sxs-lookup"><span data-stu-id="01c5a-244">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="01c5a-245">Użyj `IntPtr` / `UIntPtr` tych.</span><span class="sxs-lookup"><span data-stu-id="01c5a-245">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="01c5a-246">Podpisana typów wskaźnika (Użyj `IntPtr`)</span><span class="sxs-lookup"><span data-stu-id="01c5a-246">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="01c5a-247">Niepodpisanych typów wskaźnika (Użyj `UIntPtr`)</span><span class="sxs-lookup"><span data-stu-id="01c5a-247">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="01c5a-248">Windows `PVOID` czyli C `void*` może być organizowany jako `IntPtr` lub `UIntPtr`, ale wolisz `void*` gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="01c5a-248">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="01c5a-249">Typy danych Windows</span><span class="sxs-lookup"><span data-stu-id="01c5a-249">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="01c5a-250">Zakresy typu danych</span><span class="sxs-lookup"><span data-stu-id="01c5a-250">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="01c5a-251">Struktury</span><span class="sxs-lookup"><span data-stu-id="01c5a-251">Structs</span></span>

<span data-ttu-id="01c5a-252">Zarządzane struktury są tworzone na stosie i nie są usuwane, dopóki metoda zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="01c5a-252">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="01c5a-253">Zgodnie z definicją następnie one są "przypięte" (go nie uzyskać przeniesione, GC).</span><span class="sxs-lookup"><span data-stu-id="01c5a-253">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="01c5a-254">Możesz też po prostu korzystać z adresu w niebezpieczny kod bloki kodu natywnego nie użycia wskaźnika poza końcem bieżącej metody.</span><span class="sxs-lookup"><span data-stu-id="01c5a-254">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="01c5a-255">Struktury danych Kopiowalnych są znacznie wydajniej zgodnie z ich zastosowania po prostu bezpośrednio przez zarządzany warstwy.</span><span class="sxs-lookup"><span data-stu-id="01c5a-255">Blittable structs are much more performant as they can simply be used directly by the marshalling layer.</span></span> <span data-ttu-id="01c5a-256">Spróbuj poprowadzić struktur danych kopiowalnych (na przykład należy unikać `bool`).</span><span class="sxs-lookup"><span data-stu-id="01c5a-256">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="01c5a-257">Aby uzyskać więcej informacji, zobacz [Kopiowalnymi](#blittable-types) sekcji.</span><span class="sxs-lookup"><span data-stu-id="01c5a-257">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="01c5a-258">*Jeśli* struktury jest możliwość kopiowania, użyj `sizeof()` zamiast `Marshal.SizeOf<MyStruct>()` zapewnienia lepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="01c5a-258">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="01c5a-259">Jak wspomniano powyżej, można sprawdzić, czy typ jest możliwość kopiowania, próbując utworzyć z przypiętym `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-259">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="01c5a-260">Jeśli typ nie jest ciągiem lub uznawane za danych kopiowalnych, `GCHandle.Alloc` zgłosi `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-260">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="01c5a-261">Wskaźniki do struktur w definicjach albo muszą być przekazywane przez `ref` lub użyj `unsafe` i `*`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-261">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="01c5a-262">**CZY ✔️** dopasowania możliwie najlepszy sposób na kształt i nazw, które są używane w nagłówku lub dokumentacji oficjalnego platformy zarządzanej struktury.</span><span class="sxs-lookup"><span data-stu-id="01c5a-262">**✔️ DO** match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="01c5a-263">**CZY ✔️** użyj C# `sizeof()` zamiast `Marshal.SizeOf<MyStruct>()` dla struktur danych kopiowalnych zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="01c5a-263">**✔️ DO** use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="01c5a-264">Tablica, takich jak `INT_PTR Reserved1[2]` musi być przekazywane do dwóch `IntPtr` pól `Reserved1a` i `Reserved1b`.</span><span class="sxs-lookup"><span data-stu-id="01c5a-264">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="01c5a-265">Gdy natywna tablica jest typ pierwotny, możemy użyć `fixed` — słowo kluczowe, aby zapisać go na nieco bardziej.</span><span class="sxs-lookup"><span data-stu-id="01c5a-265">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="01c5a-266">Na przykład `SYSTEM_PROCESS_INFORMATION` wygląda podobnie do następującego w nagłówku native:</span><span class="sxs-lookup"><span data-stu-id="01c5a-266">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="01c5a-267">W C#, napiszemy ją następująco:</span><span class="sxs-lookup"><span data-stu-id="01c5a-267">In C#, we can write it like this:</span></span>

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

<span data-ttu-id="01c5a-268">Istnieją jednak pewne pytań za pomocą stałych buforów.</span><span class="sxs-lookup"><span data-stu-id="01c5a-268">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="01c5a-269">Stałe bufory typów niekopiowalnych nie będą poprawnie skierowany, więc musi tablicy w miejscu, do wyodrębnienia się do wielu poszczególnych pól.</span><span class="sxs-lookup"><span data-stu-id="01c5a-269">Fixed buffers of non-blittable types won't be correctly marshalled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="01c5a-270">Ponadto w .NET Framework i .NET Core przed 3.0, jeśli struktury zawierającej pole ustalony bufor jest zagnieżdżony w obrębie struktury niekopiowalnych pola ustalony bufor nie będzie można poprawnie skierowany do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="01c5a-270">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshalled to native code.</span></span>
