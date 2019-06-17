---
title: Wpisz marshaling — .NET
description: Dowiedz się, jak .NET kieruje typów na natywną reprezentację.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2cb8898b52b4b4afba1184a886e16c9f7f68f03a
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041785"
---
# <a name="type-marshaling"></a><span data-ttu-id="0e028-103">Marshaling typów</span><span class="sxs-lookup"><span data-stu-id="0e028-103">Type marshaling</span></span>

<span data-ttu-id="0e028-104">**Marshaling** jest procesem przekształcania typów, kiedy ich potrzebują do wielu między kodu zarządzanego i natywnego.</span><span class="sxs-lookup"><span data-stu-id="0e028-104">**Marshaling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="0e028-105">Marshaling jest niezbędne, ponieważ różnią się typami w kodzie zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="0e028-105">Marshaling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="0e028-106">W kodzie zarządzanym, na przykład masz `String`, natomiast w świecie niezarządzanych ciągi mogą być Unicode ("szerokiego"), innego niż Unicode, zakończony wartością null ASCII, itp. Domyślnie próbuje postępują właściwie na podstawie zachowania domyślnego, opisane w tym artykule podsystemu P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="0e028-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="0e028-107">Jednak w tych sytuacjach, gdy potrzebujesz dodatkowych kontroli, zostanie zastosowana [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) atrybutu, aby określić, co to jest oczekiwany typ w niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="0e028-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="0e028-108">Na przykład jeśli chcesz, aby ciąg do wysłania jako ciąg znaków zakończony znakiem null ANSI, nakładu pracy następująco:</span><span class="sxs-lookup"><span data-stu-id="0e028-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a><span data-ttu-id="0e028-109">Reguły domyślne dla marshaling typów wspólnych</span><span class="sxs-lookup"><span data-stu-id="0e028-109">Default rules for marshaling common types</span></span>

<span data-ttu-id="0e028-110">Ogólnie rzecz biorąc, środowisko wykonawcze stara się zrobić "dobre" podczas organizowania, aby wymagać minimalnej liczbie wysiłku z Twojej strony.</span><span class="sxs-lookup"><span data-stu-id="0e028-110">Generally, the runtime tries to do the "right thing" when marshaling to require the least amount of work from you.</span></span> <span data-ttu-id="0e028-111">W poniższych tabelach opisano, jak zorganizować każdego typu, domyślnie, gdy są używane w parametrze lub pola.</span><span class="sxs-lookup"><span data-stu-id="0e028-111">The following tables describe how each type is marshaled by default when used in a parameter or field.</span></span> <span data-ttu-id="0e028-112">C99 / C ++ 11 całkowitą stałej szerokości i typy znaków, które są używane do upewnij się, że Poniższa tabela jest prawidłowy dla wszystkich platform.</span><span class="sxs-lookup"><span data-stu-id="0e028-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="0e028-113">Można użyć dowolnego typu natywnego, która ma takie samo wyrównanie i wymagania dotyczące rozmiaru, jak te typy.</span><span class="sxs-lookup"><span data-stu-id="0e028-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="0e028-114">Pierwsza tabela zawiera opis mapowania dla różnych typów, dla których marshaling jest taka sama dla metody P/Invoke i organizowanie pola.</span><span class="sxs-lookup"><span data-stu-id="0e028-114">This first table describes the mappings for various types for whom the marshaling is the same for both P/Invoke and field marshaling.</span></span>

| <span data-ttu-id="0e028-115">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="0e028-115">.NET Type</span></span> | <span data-ttu-id="0e028-116">Typ natywny</span><span class="sxs-lookup"><span data-stu-id="0e028-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="0e028-117">Albo `char` lub `char16_t` w zależności od `CharSet` P/Invoke lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0e028-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="0e028-118">Zobacz [dokumentacji charset](charset.md).</span><span class="sxs-lookup"><span data-stu-id="0e028-118">See the [charset documentation](charset.md).</span></span> |
| `string`  | <span data-ttu-id="0e028-119">Albo `char*` lub `char16_t*` w zależności od `CharSet` P/Invoke lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0e028-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="0e028-120">Zobacz [dokumentacji charset](charset.md).</span><span class="sxs-lookup"><span data-stu-id="0e028-120">See the [charset documentation](charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="0e028-121">Typy wskaźników .NET (np.)</span><span class="sxs-lookup"><span data-stu-id="0e028-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="0e028-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="0e028-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="0e028-123">Typ pochodzący od `System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="0e028-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="0e028-124">Typ pochodzący od `System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="0e028-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="0e028-125">Win32 `BOOL` typu</span><span class="sxs-lookup"><span data-stu-id="0e028-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="0e028-126">COM `DECIMAL` — struktura</span><span class="sxs-lookup"><span data-stu-id="0e028-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="0e028-127">.NET Delegate</span><span class="sxs-lookup"><span data-stu-id="0e028-127">.NET Delegate</span></span> | <span data-ttu-id="0e028-128">Wskaźnik funkcji natywnej</span><span class="sxs-lookup"><span data-stu-id="0e028-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="0e028-129">Win32 `DATE` typu</span><span class="sxs-lookup"><span data-stu-id="0e028-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="0e028-130">Win32 `GUID` typu</span><span class="sxs-lookup"><span data-stu-id="0e028-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="0e028-131">Kilku kategorii marshalingu mają różne wartości domyślne, jeśli masz kierowanie jako parametr lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0e028-131">A few categories of marshaling have different defaults if you're marshaling as a parameter or structure.</span></span>

| <span data-ttu-id="0e028-132">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="0e028-132">.NET Type</span></span> | <span data-ttu-id="0e028-133">Typ macierzysty (parametr)</span><span class="sxs-lookup"><span data-stu-id="0e028-133">Native Type (Parameter)</span></span> | <span data-ttu-id="0e028-134">Typ macierzysty (pole)</span><span class="sxs-lookup"><span data-stu-id="0e028-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="0e028-135">Tablica platformy .NET</span><span class="sxs-lookup"><span data-stu-id="0e028-135">.NET array</span></span> | <span data-ttu-id="0e028-136">Wskaźnik do początku tablicy natywnej reprezentujących elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="0e028-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="0e028-137">Niedozwolona bez `[MarshalAs]` atrybutu</span><span class="sxs-lookup"><span data-stu-id="0e028-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="0e028-138">Klasa z `LayoutKind` z `Sequential` lub `Explicit`</span><span class="sxs-lookup"><span data-stu-id="0e028-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="0e028-139">Wskaźnik do natywna reprezentacja klasy</span><span class="sxs-lookup"><span data-stu-id="0e028-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="0e028-140">Natywna reprezentacja klasy</span><span class="sxs-lookup"><span data-stu-id="0e028-140">The native representation of the class</span></span> |

<span data-ttu-id="0e028-141">Poniższa tabela zawiera domyślny marshaling reguł, które są tylko do Windows.</span><span class="sxs-lookup"><span data-stu-id="0e028-141">The following table includes the default marshaling rules that are Windows-only.</span></span> <span data-ttu-id="0e028-142">Na platformach innych niż Windows nie można kierować te typy.</span><span class="sxs-lookup"><span data-stu-id="0e028-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="0e028-143">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="0e028-143">.NET Type</span></span> | <span data-ttu-id="0e028-144">Typ macierzysty (parametr)</span><span class="sxs-lookup"><span data-stu-id="0e028-144">Native Type (Parameter)</span></span> | <span data-ttu-id="0e028-145">Typ macierzysty (pole)</span><span class="sxs-lookup"><span data-stu-id="0e028-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="0e028-146">Interfejs modelu COM</span><span class="sxs-lookup"><span data-stu-id="0e028-146">COM interface</span></span> | <span data-ttu-id="0e028-147">Niedozwolona bez `[MarshalAs]` atrybutu</span><span class="sxs-lookup"><span data-stu-id="0e028-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="0e028-148">Niedozwolone</span><span class="sxs-lookup"><span data-stu-id="0e028-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="0e028-149">Niedozwolone</span><span class="sxs-lookup"><span data-stu-id="0e028-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="0e028-150">Niedozwolone</span><span class="sxs-lookup"><span data-stu-id="0e028-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="0e028-151">`int64_t` reprezentuje liczbę znaczników, od północy 1 stycznia 1601</span><span class="sxs-lookup"><span data-stu-id="0e028-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="0e028-152">`int64_t` reprezentuje liczbę znaczników, od północy 1 stycznia 1601</span><span class="sxs-lookup"><span data-stu-id="0e028-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="0e028-153">Niektóre typy mogą być organizowane wyłącznie jako parametry, a nie pola.</span><span class="sxs-lookup"><span data-stu-id="0e028-153">Some types can only be marshaled as parameters and not as fields.</span></span> <span data-ttu-id="0e028-154">Te typy są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="0e028-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="0e028-155">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="0e028-155">.NET Type</span></span> | <span data-ttu-id="0e028-156">Typ macierzysty (tylko parametr)</span><span class="sxs-lookup"><span data-stu-id="0e028-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="0e028-157">Albo `char*` lub `char16_t*` w zależności od `CharSet` elementu P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="0e028-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="0e028-158">Zobacz [dokumentacji charset](charset.md).</span><span class="sxs-lookup"><span data-stu-id="0e028-158">See the [charset documentation](charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="0e028-159">`va_list` (na Windows x86/x64/arm64 tylko)</span><span class="sxs-lookup"><span data-stu-id="0e028-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="0e028-160">Jeśli te ustawienia domyślne nie są dokładnie chcesz, możesz dostosować, jak parametry są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="0e028-160">If these defaults don't do exactly what you want, you can customize how parameters are marshaled.</span></span> <span data-ttu-id="0e028-161">[Kierowanie parametru](customize-parameter-marshaling.md) artykuł przeszukiwania Cię sposobu dostosowywania jak różne typy parametrów są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="0e028-161">The [parameter marshaling](customize-parameter-marshaling.md) article walks you through how to customize how different parameter types are marshaled.</span></span>

## <a name="default-marshaling-in-com-scenarios"></a><span data-ttu-id="0e028-162">Domyślny marshaling w scenariuszach COM</span><span class="sxs-lookup"><span data-stu-id="0e028-162">Default marshaling in COM scenarios</span></span>

<span data-ttu-id="0e028-163">Wywołując metod obiektów COM na platformie .NET, środowisko uruchomieniowe platformy .NET zmienia domyślny marshaling reguł wspólne COM semantyki.</span><span class="sxs-lookup"><span data-stu-id="0e028-163">When you are calling methods on COM objects in .NET, the .NET runtime changes the default marshaling rules to match common COM semantics.</span></span> <span data-ttu-id="0e028-164">Poniższa tabela zawiera listę reguł, które korzysta z środowiska uruchomieniowe platformy .NET w scenariuszach COM:</span><span class="sxs-lookup"><span data-stu-id="0e028-164">The following table lists the rules that .NET runtimes uses in COM scenarios:</span></span>

| <span data-ttu-id="0e028-165">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="0e028-165">.NET Type</span></span> | <span data-ttu-id="0e028-166">Typ macierzysty (COM wywołania metody)</span><span class="sxs-lookup"><span data-stu-id="0e028-166">Native Type (COM method calls)</span></span> |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| <span data-ttu-id="0e028-167">Typy delegatów</span><span class="sxs-lookup"><span data-stu-id="0e028-167">Delegate types</span></span> | <span data-ttu-id="0e028-168">`_Delegate*` w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0e028-168">`_Delegate*` in .NET Framework.</span></span> <span data-ttu-id="0e028-169">Niedozwolone w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0e028-169">Disallowed in .NET Core.</span></span> |
| `System.Drawing.Color` | `OLECOLOR`        |
| <span data-ttu-id="0e028-170">Tablica platformy .NET</span><span class="sxs-lookup"><span data-stu-id="0e028-170">.NET array</span></span> | `SAFEARRAY`                   |
| `string[]` | <span data-ttu-id="0e028-171">`SAFEARRAY` z `BSTR`s</span><span class="sxs-lookup"><span data-stu-id="0e028-171">`SAFEARRAY` of `BSTR`s</span></span>        |

## <a name="marshaling-classes-and-structs"></a><span data-ttu-id="0e028-172">Marshaling klas i struktur</span><span class="sxs-lookup"><span data-stu-id="0e028-172">Marshaling classes and structs</span></span>

<span data-ttu-id="0e028-173">Innym aspektem marshalingu typu jest sposób przekazywania w strukturze metody niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0e028-173">Another aspect of type marshaling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="0e028-174">Na przykład niektóre z niezarządzanych metod wymagają struktury jako parametr.</span><span class="sxs-lookup"><span data-stu-id="0e028-174">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="0e028-175">W takich przypadkach należy utworzyć odpowiednie struktury lub klasy w zarządzanych części świata, który będzie używany jako parametr.</span><span class="sxs-lookup"><span data-stu-id="0e028-175">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="0e028-176">Jednak po prostu Definiowanie klasy nie jest wystarczająco dużo, trzeba będzie również poinstruować Organizator sposób mapowania pól w klasie do struktury niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0e028-176">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="0e028-177">W tym miejscu `StructLayout` atrybutu staje się przydatne.</span><span class="sxs-lookup"><span data-stu-id="0e028-177">Here the `StructLayout` attribute becomes useful.</span></span>

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

<span data-ttu-id="0e028-178">Poprzedni kod pokazuje prosty przykład wywołanie `GetSystemTime()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="0e028-178">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="0e028-179">Bit interesujące znajduje się w wierszu 4.</span><span class="sxs-lookup"><span data-stu-id="0e028-179">The interesting bit is on line 4.</span></span> <span data-ttu-id="0e028-180">Ten atrybut określa, że pola klasy powinno zostać zamapowane sekwencyjnie struktury z drugiej strony (niezarządzanego).</span><span class="sxs-lookup"><span data-stu-id="0e028-180">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="0e028-181">Oznacza to, że nazwy pól nie są ważne, tylko ich kolejność jest ważna, w przypadku, gdy musi odpowiadać niezarządzane struktury, pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0e028-181">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

<span data-ttu-id="0e028-182">Czasami domyślny marshaling dla struktury nie robi, co jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="0e028-182">Sometimes the default marshaling for your structure doesn't do what you need.</span></span> <span data-ttu-id="0e028-183">[Dostosowywanie struktury marshaling](./customize-struct-marshaling.md) artykuł nauczy Cię, jak dostosować, jak jest organizowana strukturę.</span><span class="sxs-lookup"><span data-stu-id="0e028-183">The [Customizing structure marshaling](./customize-struct-marshaling.md) article teaches you how to customize how your structure is marshaled.</span></span>
