---
title: Typ zarządzany — .NET
description: Dowiedz się, jak .NET kieruje typów na natywną reprezentację.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2c62581d34e77f208b7764f955dfa37613615ee4
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416246"
---
# <a name="type-marshalling"></a><span data-ttu-id="cdc11-103">Typ zarządzany</span><span class="sxs-lookup"><span data-stu-id="cdc11-103">Type marshalling</span></span>

<span data-ttu-id="cdc11-104">**Kierowania** jest procesem przekształcania typów, kiedy ich potrzebują do wielu między kodu zarządzanego i natywnego.</span><span class="sxs-lookup"><span data-stu-id="cdc11-104">**Marshalling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="cdc11-105">Kierowania jest niezbędne, ponieważ różnią się typami w kodzie zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="cdc11-105">Marshalling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="cdc11-106">W kodzie zarządzanym, na przykład masz `String`, natomiast w świecie niezarządzanych ciągi mogą być Unicode ("szerokiego"), innego niż Unicode, zakończony wartością null ASCII, itp. Domyślnie próbuje postępują właściwie na podstawie zachowania domyślnego, opisane w tym artykule podsystemu P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="cdc11-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="cdc11-107">Jednak w tych sytuacjach, gdy potrzebujesz dodatkowych kontroli, zostanie zastosowana [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) atrybutu, aby określić, co to jest oczekiwany typ w niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="cdc11-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="cdc11-108">Na przykład jeśli chcesz, aby ciąg do wysłania jako ciąg znaków zakończony znakiem null ANSI, nakładu pracy następująco:</span><span class="sxs-lookup"><span data-stu-id="cdc11-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshalling-common-types"></a><span data-ttu-id="cdc11-109">Reguły domyślne dla kierowania popularnych typów</span><span class="sxs-lookup"><span data-stu-id="cdc11-109">Default rules for marshalling common types</span></span>

<span data-ttu-id="cdc11-110">Ogólnie rzecz biorąc, środowisko wykonawcze stara się zrobić "dobre", gdy zarządzany, aby wymagać minimalnej liczbie wysiłku z Twojej strony.</span><span class="sxs-lookup"><span data-stu-id="cdc11-110">Generally, the runtime tries to do the "right thing" when marshalling to require the least amount of work from you.</span></span> <span data-ttu-id="cdc11-111">W poniższych tabelach opisano, jak każdy typ jest skierowany domyślnie, gdy są używane w parametrze lub pola.</span><span class="sxs-lookup"><span data-stu-id="cdc11-111">The following tables describe how each type is marshalled by default when used in a parameter or field.</span></span> <span data-ttu-id="cdc11-112">C99 / C ++ 11 całkowitą stałej szerokości i typy znaków, które są używane do upewnij się, że Poniższa tabela jest prawidłowy dla wszystkich platform.</span><span class="sxs-lookup"><span data-stu-id="cdc11-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="cdc11-113">Można użyć dowolnego typu natywnego, która ma takie samo wyrównanie i wymagania dotyczące rozmiaru, jak te typy.</span><span class="sxs-lookup"><span data-stu-id="cdc11-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="cdc11-114">Pierwsza tabela zawiera opis mapowania dla różnych typów, dla których kierowania jest taka sama dla metody P/Invoke i kierowania pola.</span><span class="sxs-lookup"><span data-stu-id="cdc11-114">This first table describes the mappings for various types for whom the marshalling is the same for both P/Invoke and field marshalling.</span></span>

| <span data-ttu-id="cdc11-115">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="cdc11-115">.NET Type</span></span> | <span data-ttu-id="cdc11-116">Typ natywny</span><span class="sxs-lookup"><span data-stu-id="cdc11-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="cdc11-117">Albo `char` lub `char16_t` w zależności od `CharSet` P/Invoke lub struktury.</span><span class="sxs-lookup"><span data-stu-id="cdc11-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="cdc11-118">Zobacz [dokumentacji charset](/.charset.md).</span><span class="sxs-lookup"><span data-stu-id="cdc11-118">See the [charset documentation](/.charset.md).</span></span> |
| `string`  | <span data-ttu-id="cdc11-119">Albo `char*` lub `char16_t*` w zależności od `CharSet` P/Invoke lub struktury.</span><span class="sxs-lookup"><span data-stu-id="cdc11-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="cdc11-120">Zobacz [dokumentacji charset](/.charset.md).</span><span class="sxs-lookup"><span data-stu-id="cdc11-120">See the [charset documentation](/.charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="cdc11-121">Typy wskaźników .NET (np.)</span><span class="sxs-lookup"><span data-stu-id="cdc11-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="cdc11-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="cdc11-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="cdc11-123">Typ pochodzący od `System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="cdc11-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="cdc11-124">Typ pochodzący od `System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="cdc11-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="cdc11-125">Win32 `BOOL` typu</span><span class="sxs-lookup"><span data-stu-id="cdc11-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="cdc11-126">COM `DECIMAL` — struktura</span><span class="sxs-lookup"><span data-stu-id="cdc11-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="cdc11-127">.NET Delegate</span><span class="sxs-lookup"><span data-stu-id="cdc11-127">.NET Delegate</span></span> | <span data-ttu-id="cdc11-128">Wskaźnik funkcji natywnej</span><span class="sxs-lookup"><span data-stu-id="cdc11-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="cdc11-129">Win32 `DATE` typu</span><span class="sxs-lookup"><span data-stu-id="cdc11-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="cdc11-130">Win32 `GUID` typu</span><span class="sxs-lookup"><span data-stu-id="cdc11-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="cdc11-131">Kilka kategorii kierowania mają różne wartości domyślne, jeśli jest organizowana jako parametr lub struktury.</span><span class="sxs-lookup"><span data-stu-id="cdc11-131">A few categories of marshalling have different defaults if you're marshalling as a parameter or structure.</span></span>

| <span data-ttu-id="cdc11-132">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="cdc11-132">.NET Type</span></span> | <span data-ttu-id="cdc11-133">Typ macierzysty (parametr)</span><span class="sxs-lookup"><span data-stu-id="cdc11-133">Native Type (Parameter)</span></span> | <span data-ttu-id="cdc11-134">Typ macierzysty (pole)</span><span class="sxs-lookup"><span data-stu-id="cdc11-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="cdc11-135">Tablica platformy .NET</span><span class="sxs-lookup"><span data-stu-id="cdc11-135">.NET array</span></span> | <span data-ttu-id="cdc11-136">Wskaźnik do początku tablicy natywnej reprezentujących elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="cdc11-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="cdc11-137">Niedozwolona bez `[MarshalAs]` atrybutu</span><span class="sxs-lookup"><span data-stu-id="cdc11-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="cdc11-138">Klasa z `LayoutKind` z `Sequential` lub `Explicit`</span><span class="sxs-lookup"><span data-stu-id="cdc11-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="cdc11-139">Wskaźnik do natywna reprezentacja klasy</span><span class="sxs-lookup"><span data-stu-id="cdc11-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="cdc11-140">Natywna reprezentacja klasy</span><span class="sxs-lookup"><span data-stu-id="cdc11-140">The native representation of the class</span></span> |

<span data-ttu-id="cdc11-141">W poniższej tabeli przedstawiono domyślne kierowania reguł, które są tylko do Windows.</span><span class="sxs-lookup"><span data-stu-id="cdc11-141">The following table includes the default marshalling rules that are Windows-only.</span></span> <span data-ttu-id="cdc11-142">Na platformach innych niż Windows nie można kierować te typy.</span><span class="sxs-lookup"><span data-stu-id="cdc11-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="cdc11-143">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="cdc11-143">.NET Type</span></span> | <span data-ttu-id="cdc11-144">Typ macierzysty (parametr)</span><span class="sxs-lookup"><span data-stu-id="cdc11-144">Native Type (Parameter)</span></span> | <span data-ttu-id="cdc11-145">Typ macierzysty (pole)</span><span class="sxs-lookup"><span data-stu-id="cdc11-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="cdc11-146">Interfejs modelu COM</span><span class="sxs-lookup"><span data-stu-id="cdc11-146">COM interface</span></span> | <span data-ttu-id="cdc11-147">Niedozwolona bez `[MarshalAs]` atrybutu</span><span class="sxs-lookup"><span data-stu-id="cdc11-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="cdc11-148">Niedozwolone</span><span class="sxs-lookup"><span data-stu-id="cdc11-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="cdc11-149">Niedozwolone</span><span class="sxs-lookup"><span data-stu-id="cdc11-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="cdc11-150">Niedozwolone</span><span class="sxs-lookup"><span data-stu-id="cdc11-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="cdc11-151">`int64_t` reprezentuje liczbę znaczników, od północy 1 stycznia 1601</span><span class="sxs-lookup"><span data-stu-id="cdc11-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="cdc11-152">`int64_t` reprezentuje liczbę znaczników, od północy 1 stycznia 1601</span><span class="sxs-lookup"><span data-stu-id="cdc11-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="cdc11-153">Niektóre typy mogą tylko skierowany, jako parametry, a nie pola.</span><span class="sxs-lookup"><span data-stu-id="cdc11-153">Some types can only be marshalled as parameters and not as fields.</span></span> <span data-ttu-id="cdc11-154">Te typy są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="cdc11-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="cdc11-155">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="cdc11-155">.NET Type</span></span> | <span data-ttu-id="cdc11-156">Typ macierzysty (tylko parametr)</span><span class="sxs-lookup"><span data-stu-id="cdc11-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="cdc11-157">Albo `char*` lub `char16_t*` w zależności od `CharSet` elementu P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="cdc11-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="cdc11-158">Zobacz [dokumentacji charset](/.charset.md).</span><span class="sxs-lookup"><span data-stu-id="cdc11-158">See the [charset documentation](/.charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="cdc11-159">`va_list` (na Windows x86/x64/arm64 tylko)</span><span class="sxs-lookup"><span data-stu-id="cdc11-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="cdc11-160">Te ustawienia domyślne nie są dokładnie ma, można dostosować, jak/parametrów wycofany.</span><span class="sxs-lookup"><span data-stu-id="cdc11-160">If these defaults don't do exactly what you want, you can customize how parameters are marshalled.</span></span> <span data-ttu-id="cdc11-161">[Kierowania parametr](customize-parameter-marshalling.md) artykuł przeszukiwania Cię sposobu dostosowywania jak różne typy parametrów/wycofany.</span><span class="sxs-lookup"><span data-stu-id="cdc11-161">The [parameter marshalling](customize-parameter-marshalling.md) article walks you through how to customize how different parameter types are marshalled.</span></span>

## <a name="marshalling-classes-and-structs"></a><span data-ttu-id="cdc11-162">Kierowania klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="cdc11-162">Marshalling classes and structs</span></span>

<span data-ttu-id="cdc11-163">Innym aspektem kierowania typu jest sposób przekazywania w strukturze metody niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="cdc11-163">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="cdc11-164">Na przykład niektóre z niezarządzanych metod wymagają struktury jako parametr.</span><span class="sxs-lookup"><span data-stu-id="cdc11-164">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="cdc11-165">W takich przypadkach należy utworzyć odpowiednie struktury lub klasy w zarządzanych części świata, który będzie używany jako parametr.</span><span class="sxs-lookup"><span data-stu-id="cdc11-165">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="cdc11-166">Jednak po prostu Definiowanie klasy nie jest wystarczająco dużo, trzeba będzie również poinstruować Organizator sposób mapowania pól w klasie do struktury niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="cdc11-166">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="cdc11-167">W tym miejscu `StructLayout` atrybutu staje się przydatne.</span><span class="sxs-lookup"><span data-stu-id="cdc11-167">Here the `StructLayout` attribute becomes useful.</span></span>

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

<span data-ttu-id="cdc11-168">Poprzedni kod pokazuje prosty przykład wywołanie `GetSystemTime()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="cdc11-168">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="cdc11-169">Bit interesujące znajduje się w wierszu 4.</span><span class="sxs-lookup"><span data-stu-id="cdc11-169">The interesting bit is on line 4.</span></span> <span data-ttu-id="cdc11-170">Ten atrybut określa, że pola klasy powinno zostać zamapowane sekwencyjnie struktury z drugiej strony (niezarządzanego).</span><span class="sxs-lookup"><span data-stu-id="cdc11-170">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="cdc11-171">Oznacza to, że nazwy pól nie są ważne, tylko ich kolejność jest ważna, w przypadku, gdy musi odpowiadać niezarządzane struktury, pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cdc11-171">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

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

<span data-ttu-id="cdc11-172">Czasami domyślnie kierowania dla Twojej struktury nie robi, co jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="cdc11-172">Sometimes the default marshalling for your structure doesn't do what you need.</span></span> <span data-ttu-id="cdc11-173">[Dostosowywanie struktury kierowania](./customize-struct-marshalling.md) artykuł nauczy Cię, jak dostosować, jak jest organizowana strukturę.</span><span class="sxs-lookup"><span data-stu-id="cdc11-173">The [Customizing structure marshalling](./customize-struct-marshalling.md) article teaches you how to customize how your structure is marshaled.</span></span>
