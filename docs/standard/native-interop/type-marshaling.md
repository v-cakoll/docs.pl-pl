---
title: Kierowanie typów — .NET
description: Dowiedz się, w jaki sposób platforma .NET umożliwia kierowanie typów do natywnej reprezentacji.
ms.date: 01/18/2019
ms.openlocfilehash: 91b8f3d6cb53fd7a0adea7ea9669e7459e81445f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706269"
---
# <a name="type-marshaling"></a>Marshaling typów

**Kierowanie** jest procesem przekształcania typów, gdy muszą one przecinać się między kodem zarządzanym i natywnym.

Organizowanie jest niezbędna, ponieważ typy w kodzie zarządzanym i niezarządzanym są różne. W kodzie zarządzanym, na przykład, posiadasz `String`, natomiast w niezarządzanych ciągach świata mogą być Unicode ("szerokie"), inne niż Unicode, zakończonych znakiem null, ASCII itd. Domyślnie podsystem P/Invoke próbuje wykonać właściwe czynności na podstawie domyślnego zachowania opisanego w tym artykule. Jednak dla tych sytuacji, gdy potrzebna jest dodatkowa kontrola, można użyć atrybutu [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) , aby określić, jaki jest oczekiwany typ na stronie niezarządzanej. Na przykład, jeśli chcesz, aby ciąg był wysyłany jako ciąg ANSI zakończony wartością null, można to zrobić w następujący sposób:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a>Domyślne reguły organizowania wspólnych typów

Ogólnie rzecz biorąc, środowisko uruchomieniowe próbuje wykonać "prawo" podczas organizowania, aby wymagać od Ciebie najmniejszej ilości pracy. W poniższych tabelach opisano, jak każdy typ jest zorganizowany domyślnie, gdy jest używany w parametrze lub polu. Typy całkowite i znaki stałej szerokości C99/C++ 11 są używane w celu upewnienia się, że Poniższa tabela jest poprawna dla wszystkich platform. Można użyć dowolnego typu natywnego, który ma takie same wymagania dotyczące wyrównania i rozmiaru co te typy.

W pierwszej tabeli opisano mapowania dla różnych typów, dla których kierowanie jest takie same dla obydwu P/Invoke i organizowania pól.

| Typ .NET | Typ natywny  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | Albo w zależności od `CharSet` typu P/Invoke lub struktury. `char` `char16_t` Zobacz [dokumentację zestawu znaków](charset.md). |
| `string`  | Albo w zależności od `CharSet` typu P/Invoke lub struktury. `char*` `char16_t*` Zobacz [dokumentację zestawu znaków](charset.md). |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| Typy wskaźników .NET (np. `void*`)  | `void*` |
| Typ pochodzący od`System.Runtime.InteropServices.SafeHandle` | `void*` |
| Typ pochodzący od`System.Runtime.InteropServices.CriticalHandle` | `void*`          |
| `bool`    | Typ `BOOL` Win32       |
| `decimal` | Struktura `DECIMAL` com |
| Delegat platformy .NET | Wskaźnik funkcji natywnej |
| `System.DateTime` | Typ `DATE` Win32 |
| `System.Guid` | Typ `GUID` Win32 |

Niektóre kategorie organizowania mają różne wartości domyślne, jeśli są organizowane jako parametry lub struktura.

| Typ .NET | Typ natywny (parametr) | Typ natywny (pole) |
|-----------|-------------------------|---------------------|
| Tablica .NET | Wskaźnik do początku tablicy natywnych reprezentacji elementów tablicy. | Niedozwolone bez `[MarshalAs]` atrybutu|
| Klasa z `LayoutKind` `Sequential` lub`Explicit` | Wskaźnik do natywnej reprezentacji klasy | Natywna Reprezentacja klasy |

Poniższa tabela zawiera domyślne reguły organizowania, które są przeznaczone tylko dla systemu Windows. Na platformach innych niż Windows nie można zorganizować tych typów.

| Typ .NET | Typ natywny (parametr) | Typ natywny (pole) |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | Interfejs COM | Niedozwolone bez `[MarshalAs]` atrybutu |
| `System.ArgIterator` | `va_list` | Niedozwolone |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | Niedozwolone |
| `System.Collections.IEnumerable` | `IDispatch*` | Niedozwolone |
| `System.DateTimeOffset` | `int64_t`reprezentująca liczbę taktów od północy 1 stycznia 1601 || `int64_t`reprezentująca liczbę taktów od północy 1 stycznia 1601 |

Niektóre typy mogą być organizowane tylko jako parametry, a nie jako pola. Te typy są wymienione w poniższej tabeli:

| Typ .NET | Typ natywny (tylko parametr) |
|-----------|------------------------------|
| `System.Text.StringBuilder` | `char16_t*` `CharSet` Albo `char*` w zależności od parametru P/Invoke.  Zobacz [dokumentację zestawu znaków](charset.md). |
| `System.ArgIterator` | `va_list`(tylko w systemie Windows x86/x64/arm64) |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

Jeśli te wartości domyślne nie wykonują dokładnie tego, co chcesz, możesz dostosować sposób organizowania parametrów. Artykuł dotyczący [organizowania parametrów](customize-parameter-marshaling.md) przeprowadzi Cię przez proces dostosowywania sposobu organizowania różnych typów parametrów.

## <a name="default-marshaling-in-com-scenarios"></a>Kierowanie domyślne w scenariuszach COM

Podczas wywoływania metod obiektów COM w programie .NET środowisko uruchomieniowe platformy .NET zmienia domyślne reguły organizowania w celu dopasowania do wspólnej semantyki modelu COM. W poniższej tabeli wymieniono reguły, których środowiska uruchomieniowe platformy .NET używają w scenariuszach COM:

| Typ .NET | Typ natywny (wywołania metody COM) |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| Typy delegatów | `_Delegate*`w .NET Framework. Niedozwolone w programie .NET Core. |
| `System.Drawing.Color` | `OLECOLOR`        |
| Tablica .NET | `SAFEARRAY`                   |
| `string[]` | `SAFEARRAY`z `BSTR`s        |

## <a name="marshaling-classes-and-structs"></a>Kierowanie klas i struktur

Innym aspektem organizowania typów jest sposób przekazywania struktury do niezarządzanej metody. Na przykład niektóre metody niezarządzane wymagają struktury jako parametru. W takich przypadkach należy utworzyć odpowiednią strukturę lub klasę w zarządzanej części świata, aby użyć jej jako parametru. Jednak tylko zdefiniowanie klasy jest niewystarczające, należy również poinstruować organizatora, jak mapować pola w klasie na niezarządzaną strukturę. W tym `StructLayout` miejscu atrybut jest przydatny.

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

Poprzedni kod pokazuje prosty przykład wywołania `GetSystemTime()` funkcji. Interesujący bit jest w wierszu 4. Ten atrybut określa, że pola klasy powinny być mapowane sekwencyjnie do struktury na drugiej (niezarządzanej) stronie. Oznacza to, że nazwy pól nie są ważne, tylko ich kolejność jest ważna, ponieważ musi odpowiadać strukturze niezarządzanej, pokazanej w następującym przykładzie:

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
} SYSTEMTIME, *PSYSTEMTIME;
```

Czasami domyślne kierowanie dla Twojej struktury nie robi tego, czego potrzebujesz. W artykule [Dostosowywanie struktury dostosowywania](./customize-struct-marshaling.md) przedstawiono sposób dostosowywania struktury struktur.
