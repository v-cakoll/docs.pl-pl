---
title: Typ zarządzany — .NET
description: Dowiedz się, jak .NET kieruje typów na natywną reprezentację.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: b4846f2e6cd945a25ec6a747c9038d48fe115559
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973509"
---
# <a name="type-marshalling"></a>Typ zarządzany

**Kierowania** jest procesem przekształcania typów, kiedy ich potrzebują do wielu między kodu zarządzanego i natywnego.

Kierowania jest niezbędne, ponieważ różnią się typami w kodzie zarządzanym i niezarządzanym. W kodzie zarządzanym, na przykład masz `String`, natomiast w świecie niezarządzanych ciągi mogą być Unicode ("szerokiego"), innego niż Unicode, zakończony wartością null ASCII, itp. Domyślnie próbuje postępują właściwie na podstawie zachowania domyślnego, opisane w tym artykule podsystemu P/Invoke. Jednak w tych sytuacjach, gdy potrzebujesz dodatkowych kontroli, zostanie zastosowana [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) atrybutu, aby określić, co to jest oczekiwany typ w niezarządzanym. Na przykład jeśli chcesz, aby ciąg do wysłania jako ciąg znaków zakończony znakiem null ANSI, nakładu pracy następująco:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshalling-common-types"></a>Reguły domyślne dla kierowania popularnych typów

Ogólnie rzecz biorąc, środowisko wykonawcze stara się zrobić "dobre", gdy zarządzany, aby wymagać minimalnej liczbie wysiłku z Twojej strony. W poniższych tabelach opisano, jak każdy typ jest skierowany domyślnie, gdy są używane w parametrze lub pola. C99 / C ++ 11 całkowitą stałej szerokości i typy znaków, które są używane do upewnij się, że Poniższa tabela jest prawidłowy dla wszystkich platform. Można użyć dowolnego typu natywnego, która ma takie samo wyrównanie i wymagania dotyczące rozmiaru, jak te typy.

Pierwsza tabela zawiera opis mapowania dla różnych typów, dla których kierowania jest taka sama dla metody P/Invoke i kierowania pola.

| Typ architektury .NET | Typ natywny  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | Albo `char` lub `char16_t` w zależności od `CharSet` P/Invoke lub struktury. Zobacz [dokumentacji charset](charset.md). |
| `string`  | Albo `char*` lub `char16_t*` w zależności od `CharSet` P/Invoke lub struktury. Zobacz [dokumentacji charset](charset.md). |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| Typy wskaźników .NET (np.) `void*`)  | `void*` |
| Typ pochodzący od `System.Runtime.InteropServices.SafeHandle` | `void*` |
| Typ pochodzący od `System.Runtime.InteropServices.CriticalHandle` | `void*`          |
| `bool`    | Win32 `BOOL` typu       |
| `decimal` | COM `DECIMAL` — struktura |
| .NET Delegate | Wskaźnik funkcji natywnej |
| `System.DateTime` | Win32 `DATE` typu |
| `System.Guid` | Win32 `GUID` typu |

Kilka kategorii kierowania mają różne wartości domyślne, jeśli jest organizowana jako parametr lub struktury.

| Typ architektury .NET | Typ macierzysty (parametr) | Typ macierzysty (pole) |
|-----------|-------------------------|---------------------|
| Tablica platformy .NET | Wskaźnik do początku tablicy natywnej reprezentujących elementy tablicy. | Niedozwolona bez `[MarshalAs]` atrybutu|
| Klasa z `LayoutKind` z `Sequential` lub `Explicit` | Wskaźnik do natywna reprezentacja klasy | Natywna reprezentacja klasy |

W poniższej tabeli przedstawiono domyślne kierowania reguł, które są tylko do Windows. Na platformach innych niż Windows nie można kierować te typy.

| Typ architektury .NET | Typ macierzysty (parametr) | Typ macierzysty (pole) |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | Interfejs modelu COM | Niedozwolona bez `[MarshalAs]` atrybutu |
| `System.ArgIterator` | `va_list` | Niedozwolone |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | Niedozwolone |
| `System.Collections.IEnumerable` | `IDispatch*` | Niedozwolone |
| `System.DateTimeOffset` | `int64_t` reprezentuje liczbę znaczników, od północy 1 stycznia 1601 || `int64_t` reprezentuje liczbę znaczników, od północy 1 stycznia 1601 |

Niektóre typy mogą tylko skierowany, jako parametry, a nie pola. Te typy są wymienione w poniższej tabeli:

| Typ architektury .NET | Typ macierzysty (tylko parametr) |
|-----------|------------------------------|
| `System.Text.StringBuilder` | Albo `char*` lub `char16_t*` w zależności od `CharSet` elementu P/Invoke.  Zobacz [dokumentacji charset](charset.md). |
| `System.ArgIterator` | `va_list` (na Windows x86/x64/arm64 tylko) |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

Te ustawienia domyślne nie są dokładnie ma, można dostosować, jak/parametrów wycofany. [Kierowania parametr](customize-parameter-marshalling.md) artykuł przeszukiwania Cię sposobu dostosowywania jak różne typy parametrów/wycofany.

## <a name="marshalling-classes-and-structs"></a>Kierowania klasy i struktury

Innym aspektem kierowania typu jest sposób przekazywania w strukturze metody niezarządzanego. Na przykład niektóre z niezarządzanych metod wymagają struktury jako parametr. W takich przypadkach należy utworzyć odpowiednie struktury lub klasy w zarządzanych części świata, który będzie używany jako parametr. Jednak po prostu Definiowanie klasy nie jest wystarczająco dużo, trzeba będzie również poinstruować Organizator sposób mapowania pól w klasie do struktury niezarządzanej. W tym miejscu `StructLayout` atrybutu staje się przydatne.

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

Poprzedni kod pokazuje prosty przykład wywołanie `GetSystemTime()` funkcji. Bit interesujące znajduje się w wierszu 4. Ten atrybut określa, że pola klasy powinno zostać zamapowane sekwencyjnie struktury z drugiej strony (niezarządzanego). Oznacza to, że nazwy pól nie są ważne, tylko ich kolejność jest ważna, w przypadku, gdy musi odpowiadać niezarządzane struktury, pokazano w poniższym przykładzie:

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

Czasami domyślnie kierowania dla Twojej struktury nie robi, co jest potrzebne. [Dostosowywanie struktury kierowania](./customize-struct-marshalling.md) artykuł nauczy Cię, jak dostosować, jak jest organizowana strukturę.
