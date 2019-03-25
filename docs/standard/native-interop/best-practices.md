---
title: Współdziałanie natywne najlepsze rozwiązania — .NET
description: Dowiedz się, najlepsze rozwiązania dotyczące komunikacji z usługą składnikami macierzystymi na platformie .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 5b65f80d3a81fab0d74ce26aec3b454c716a5d51
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412061"
---
# <a name="native-interoperability-best-practices"></a>Współdziałanie natywne najlepszych rozwiązań

.NET zapewnia szereg sposobów dostosowywania kodu interoperacyjności macierzystej. Ten artykuł zawiera wskazówki, które zespoły .NET firmy Microsoft należy wykonać w przypadku interoperacyjności macierzystej.

## <a name="general-guidance"></a>Ogólne wskazówki

Wskazówki zawarte w tej sekcji ma zastosowanie do wszystkich scenariuszy międzyoperacyjnego.

- **CZY ✔️** użyć tych samych nazw i wielkości liter dla metody i parametrów jako metodę natywną ma zostać wywołana.
- **ROZWAŻ ✔️** przy użyciu tych samych nazw i wielkości liter dla wartości stałych.
- **CZY ✔️** używanie typów .NET, znajdujący się najbliżej mapowane na typ macierzysty. Na przykład w C#, użyj `uint` po typ natywny `unsigned int`.
- **CZY ✔️** składać się tylko `[In]` i `[Out]` atrybuty, gdy zachowanie zostanie różni się od zachowanie domyślne.
- **ROZWAŻ ✔️** przy użyciu <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> do puli buforów Twoja natywna tablica.
- **ROZWAŻ ✔️** opakowujące aplikacje usługi deklaracje P/Invoke w klasie za pomocą tej samej nazwie i wielkość liter jak natywne biblioteki.
  - Dzięki temu Twoje `[DllImport]` atrybutów, które mają używać C# `nameof` funkcji języka, aby przekazać nazwę bibliotekę natywną i upewnij się, że nie wpiszesz nazwę bibliotekę natywną.

## <a name="dllimport-attribute-settings"></a>Ustawienia atrybut DllImport

| Ustawienie | Domyślny | Zalecenie | Szczegóły |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  Zachowaj domyślne  | Jeśli jawnie ustawiono na zwracane wartości HRESULT false, zakończone niepowodzeniem, zostanie włączony do wyjątków (i wartość zwracana w definicji staje się wartości null w wyniku).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | zależy od interfejsu API  | Ustaw na wartość true, jeśli interfejs API korzysta GetLastError i użyj Marshal.GetLastWin32Error, aby uzyskać wartość. Jeśli interfejs API określa warunek, stwierdzający, że ma błąd, komunikat o błędzie przed wprowadzeniem innych wywołań, aby uniknąć przypadkowego on zastąpiony.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, która przechodzi do `CharSet.Ansi` zachowanie  | Jawnie użyć `CharSet.Unicode` lub `CharSet.Ansi` kiedy ciągów lub znaki są obecne w definicji | Określa zachowanie kierujące ciągi i co `ExactSpelling` gdy `false`. Należy pamiętać, że `CharSet.Ansi` jest faktycznie UTF8 w systemach Unix. _Większość_ czasu Windows używa Unicode, podczas gdy Unix używa UTF8. Zobacz więcej informacji na [dokumentację dotyczącą zestawów znaków](./charset.md). |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Ustaw tę wartość true, i uzyskać korzyści wydajności niewielkie, ponieważ środowisko wykonawcze nie będzie szukać funkcji alternatywne nazwy z sufiksem "A" lub "W" w zależności od wartości `CharSet` ustawienie ("A", aby uzyskać `CharSet.Ansi` i "T" dla `CharSet.Unicode`). |

## <a name="string-parameters"></a>Parametry ciągu

Gdy zestaw znaków jest Unicode lub argument jest jawnie oznaczona jako `[MarshalAs(UnmanagedType.LPWSTR)]` _i_ ten ciąg jest przekazywany przez wartość (nie `ref` lub `out`), ciąg zostanie przypięty i używana bezpośrednio przez kod natywny (zamiast skopiowany).

Pamiętaj, aby oznaczyć `[DllImport]` jako `Charset.Unicode` , chyba że jawnie ma ANSI postępowanie z Twoimi ciągami.

**NIE OBSŁUGUJĄ ❌** użyj `[Out] string` parametrów. Ciąg parametrów przekazywanych przez wartość z `[Out]` atrybutu mogą destabilizować środowisko wykonawcze, jeśli ciąg jest ciągiem interned. Zobacz więcej informacji na temat w dokumentacji dotyczącej wewnętrzne przygotowanie ciągu <xref:System.String.Intern%2A?displayProperty=nameWithType>.

**Należy UNIKAĆ ❌** `StringBuilder` parametrów. `StringBuilder` kierowania *zawsze* tworzona jest kopia natywnych buforu. W efekcie może być bardzo mało wydajne. Wykonaj typowy scenariusz wywołania interfejsu API Windows, która przyjmuje ciąg:

1. Utwórz SB żądaną wydajność (przydziela pojemność zarządzanego) **{1}**
2. wywoływanie
   1. Przydziela bufor natywne **{2}**  
   2. Kopiuje zawartość, jeśli `[In]` _(wartość domyślna dla `StringBuilder` parametru)_  
   3. Kopiuje bufor natywnej do nowo przydzielonego tablicy zarządzanej, jeśli `[Out]` **{3}** _(również wartość domyślna dla `StringBuilder`)_  
3. `ToString()` przydziela kolejny tablicy zarządzanej **{4}**

Oznacza to *{4}* alokacji można pobrać parametrów z kodu natywnego. Najlepiej, można zrobić, aby ograniczyć to jest to ponowne użycie `StringBuilder` w inne połączenie, ale nadal tylko pozwala to zaoszczędzić *1* alokacji. Znacznie lepiej używać i pamięci podręcznej buforu znaków, z `ArrayPool`-następnie można uzyskać w dół do właśnie alokacji dla `ToString()` w kolejnych wywołaniach.

Problem z `StringBuilder` jest zawsze kopiuje buforze kopii zapasowej pierwszej wartości null. Jeśli przekazany ciąg Wstecz nie jest zakończony lub ciąg przerwany wartością null podwójnej precyzji, metody P/Invoke, jest ona niepoprawna w najlepszym.

Jeśli możesz *czy* użyj `StringBuilder`, jeden ostatnie problemy jest, że pojemność nie **nie** obejmują ukryte wartość null, co jest zawsze uwzględnione w międzyoperacyjności. Często użytkownicy będą mogli uzyskać dostęp do tej nieprawidłowy, ponieważ większość interfejsów API mają rozmiar buforu *tym* o wartości null. Może to spowodować zmarnowany niepotrzebnych alokacji. Ponadto to problemy zapobiega środowiska uruchomieniowego optymalizacji `StringBuilder` zarządzany, aby zminimalizować kopii.

**ROZWAŻ ✔️** przy użyciu `char[]`s z `ArrayPool`.

Aby uzyskać więcej informacji na temat kierowania ciągu, zobacz [domyślne kierowania dla ciągów](../../framework/interop/default-marshaling-for-strings.md) i [Dostosowywanie kierowania ciągu](customize-parameter-marshalling.md#customizing-string-parameters).

> __Windows określonego__  
> Dla `[Out]` użyje ciągi CLR `CoTaskMemFree` domyślnie, aby zwolnić ciągów lub `SysStringFree` dla ciągów, które są oznaczone jako `UnmanagedType.BSTR`.  
**Dla większości interfejsów API za pomocą buforu ciągu wyjściowego:**  
> Przekazany w znaku count musi zawierać wartości null. Jeśli zwracana wartość jest mniejsza niż przekazany w liczba znaków wywołanie zakończy się pomyślnie, jak i wartość jest liczbą znaków *bez* końcową wartość null. W przeciwnym razie licznik jest wymagany rozmiar buforu *tym* znaku null.  
> - Przekaż 5, Pobierz 4: Ten ciąg jest 4 znaków długo z końcową wartość null.
> - Przekaż 5, Pobierz 6: Ten ciąg jest 5 znaków muszą 6 znaków bufor do przechowywania wartości null.  
> [Typy danych Windows dla ciągów](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Wartość logiczna parametry i pola

Wartości logiczne są łatwe do awarię. Domyślnie .NET `bool` jest skierowany do Windows `BOOL`, gdzie jest to wartość 4-bajtowe. Jednak `_Bool`, i `bool` typy w językach C i C++ są *pojedynczego* bajtów. Może to prowadzić do trudne do śledzenia usterek jako pół wartość zwracaną zostaną odrzucone, który będzie tylko *potencjalnie* zmienić wynik. Aby uzyskać więcej informacji na temat kierowania .NET `bool` wartości języka C lub C++ `bool` typów, zobacz dokumentację na [Dostosowywanie pola logicznych kierowania](customize-struct-marshalling.md#customizing-boolean-field-marshalling).

## <a name="guids"></a>Identyfikatory GUID

Identyfikatory GUID są użyteczne bezpośrednio w sygnaturach. Wiele interfejsów API Windows `GUID&` aliasów, takich jak typów `REFIID`. W przypadku przekazywany przez odwołanie, ich można albo być przekazywany `ref` lub `[MarshalAs(UnmanagedType.LPStruct)]` atrybutu.

| Identyfikator GUID | Identyfikator GUID przez odwołanie |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

**NIE OBSŁUGUJĄ ❌** użyj `[MarshalAs(UnmanagedType.LPStruct)]` dla żadnych innych niż `ref` parametrów identyfikatora GUID.

## <a name="blittable-types"></a>Typy Kopiowalne

Typy Kopiowalne są typy, które mają tę samą reprezentację bitowy poziom w kodu zarządzanego i natywnego. Jako takie nie należy do innego formatu w celu skierowany, do i z kodu natywnego, a ponieważ zwiększa to wydajność powinna być preferowane.

**Typy Kopiowalne:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- tablice jednowymiarowe-nested typy danych kopiowalnych (na przykład `int[]`)
- struktur i klas o stałym układzie, na których znajduje się wartość danych kopiowalnych na przykład typy pól
  - wymaga stałym układzie `[StructLayout(LayoutKind.Sequential)]` lub `[StructLayout(LayoutKind.Explicit)]`
  - struktury są `LayoutKind.Sequential` są domyślnie klasy `LayoutKind.Auto`

**NIE kopiowalne:**

- `bool`

**CZASAMI kopiowalne:**

- `char`, `string`

Gdy typy danych kopiowalnych są przekazywane przez odwołanie, są one po prostu przypiętych przez szeregujący zamiast kopiowane do pośredniego buforu. (Klasy natury są przekazywane przez odwołanie, struktur są przekazywane przez odwołanie, gdy jest używane z `ref` lub `out`.)

`char` jest możliwość kopiowania w tablicy jednowymiarowej **lub** Jeśli jest on częścią typu, który zawiera on jest jawnie oznaczona za pomocą `[StructLayout]` z `CharSet = CharSet.Unicode`.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string` jest możliwość kopiowania, jeśli nie jest on zawarty w innym typem i jest przekazywany jako argument, który jest oznaczony przy użyciu `[MarshalAs(UnmanagedType.LPWStr)]` lub `[DllImport]` ma `CharSet = CharSet.Unicode` zestawu.

Zostanie wyświetlony, jeśli typ jest danych kopiowalnych, próbując utworzyć z przypiętym `GCHandle`. Jeśli typ nie jest ciągiem lub uznawane za danych kopiowalnych, `GCHandle.Alloc` zgłosi `ArgumentException`.

**CZY ✔️** wprowadzić swoje struktur danych kopiowalnych, gdy jest to możliwe.

Aby uzyskać więcej informacji, zobacz:

- [Typy kopiowalne i niekopiowalne](../../framework/interop/blittable-and-non-blittable-types.md)  
- [Typ zarządzany](type-marshalling.md)

## <a name="keeping-managed-objects-alive"></a>Utrzymywanie zarządzane obiekty aktywne

`GC.KeepAlive()` pewność, że obiekt pozostaje w zakresie, dopóki nie zostanie osiągnięty jako metoda utrzymywania aktywności.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) Umożliwia szeregujący zapewnienie obiekt podtrzymania połączenia dla czasu trwania elementu P/Invoke. Mogą być używane zamiast `IntPtr` w podpisy metod. `SafeHandle` skutecznie zastępuje tej klasy i powinny być używane zamiast tego.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) Umożliwia przypinanie obiektu zarządzanego i uzyskiwania wskaźnik natywny. Podstawowy wzorzec jest:  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Przypinanie nie jest ustawieniem domyślnym dla `GCHandle`. Główne wzorzec dotyczy przekazywaniem odwołań do obiektu zarządzanego za pośrednictwem kodu natywnego i powrót do kodu zarządzanego, zwykle za pomocą wywołania zwrotnego. Poniżej przedstawiono wzorzec:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Nie należy zapominać, że `GCHandle` musi jawnie zwolniona w celu uniknięcia przecieków pamięci.

## <a name="common-windows-data-types"></a>Standardowe typy danych Windows

W tym miejscu znajduje się lista typów danych najczęściej używanych interfejsów API Windows, które C# typów do użycia podczas wywoływania w kodzie Windows.

Taki sam rozmiar na 32-bitowych i 64-bitowych Windows, niezależnie od ich nazwy są następujące typy.

| Szerokość | Windows          | C (Windows)          | C#       | Alternatywna                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| 32    | `BOOL`           | `int`                | `int`    | `bool`                               |
| 8     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| 8     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| 8     | `CHAR`           | `char`               | `sbyte`  |                                      |
| 8     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| 16    | `SHORT`          | `short`              | `short`  |                                      |
| 16    | `CSHORT`         | `short`              | `short`  |                                      |
| 16    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| 16    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| 16    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| 32    | `INT`            | `int`                | `int`    |                                      |
| 32    | `LONG`           | `long`               | `int`    |                                      |
| 32    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| 32    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| 64    | `QWORD`          | `long long`          | `long`   |                                      |
| 64    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| 64    | `LONGLONG`       | `long long`          | `long`   |                                      |
| 64    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| 64    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| 32    | `HRESULT`        | `long`               | `int`    |                                      |
| 32    | `NTSTATUS`       | `long`               | `int`    |                                      |


Następujące typy, są wskaźnikami, postępuj zgodnie z szerokość platformy. Użyj `IntPtr` / `UIntPtr` tych.

| Podpisana typów wskaźnika (Użyj `IntPtr`) | Niepodpisanych typów wskaźnika (Użyj `UIntPtr`) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

Windows `PVOID` czyli C `void*` może być organizowany jako `IntPtr` lub `UIntPtr`, ale wolisz `void*` gdy jest to możliwe.

[Typy danych Windows](/windows/desktop/WinProg/windows-data-types)

[Zakresy typu danych](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Struktury

Zarządzane struktury są tworzone na stosie i nie są usuwane, dopóki metoda zwraca wartość. Zgodnie z definicją następnie one są "przypięte" (go nie uzyskać przeniesione, GC). Możesz też po prostu korzystać z adresu w niebezpieczny kod bloki kodu natywnego nie użycia wskaźnika poza końcem bieżącej metody.

Struktury danych Kopiowalnych są znacznie wydajniej zgodnie z ich zastosowania po prostu bezpośrednio przez zarządzany warstwy. Spróbuj poprowadzić struktur danych kopiowalnych (na przykład należy unikać `bool`). Aby uzyskać więcej informacji, zobacz [Kopiowalnymi](#blittable-types) sekcji.

*Jeśli* struktury jest możliwość kopiowania, użyj `sizeof()` zamiast `Marshal.SizeOf<MyStruct>()` zapewnienia lepszej wydajności. Jak wspomniano powyżej, można sprawdzić, czy typ jest możliwość kopiowania, próbując utworzyć z przypiętym `GCHandle`. Jeśli typ nie jest ciągiem lub uznawane za danych kopiowalnych, `GCHandle.Alloc` zgłosi `ArgumentException`.

Wskaźniki do struktur w definicjach albo muszą być przekazywane przez `ref` lub użyj `unsafe` i `*`.

**CZY ✔️** dopasowania możliwie najlepszy sposób na kształt i nazw, które są używane w nagłówku lub dokumentacji oficjalnego platformy zarządzanej struktury.

**CZY ✔️** użyj C# `sizeof()` zamiast `Marshal.SizeOf<MyStruct>()` dla struktur danych kopiowalnych zwiększyć wydajność.

Tablica, takich jak `INT_PTR Reserved1[2]` musi być przekazywane do dwóch `IntPtr` pól `Reserved1a` i `Reserved1b`. Gdy natywna tablica jest typ pierwotny, możemy użyć `fixed` — słowo kluczowe, aby zapisać go na nieco bardziej. Na przykład `SYSTEM_PROCESS_INFORMATION` wygląda podobnie do następującego w nagłówku native:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

W C#, napiszemy ją następująco:

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

Istnieją jednak pewne pytań za pomocą stałych buforów. Stałe bufory typów niekopiowalnych nie będą poprawnie skierowany, więc musi tablicy w miejscu, do wyodrębnienia się do wielu poszczególnych pól. Ponadto w .NET Framework i .NET Core przed 3.0, jeśli struktury zawierającej pole ustalony bufor jest zagnieżdżony w obrębie struktury niekopiowalnych pola ustalony bufor nie będzie można poprawnie skierowany do kodu macierzystego.
