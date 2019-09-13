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
# <a name="native-interoperability-best-practices"></a>Najlepsze rozwiązania w zakresie współdziałania natywnego

Program .NET oferuje różne sposoby dostosowywania natywnego kodu współdziałania. Ten artykuł zawiera wskazówki, które są zgodne z zespołem .NET firmy Microsoft dotyczącym natywnej współdziałania.

## <a name="general-guidance"></a>Wskazówki ogólne

Wskazówki zawarte w tej sekcji dotyczą wszystkich scenariuszy międzyoperacyjnych.

- **✔️** Użyj tej samej nazwy i wielkości liter dla metod i parametrów jako metody natywnej, którą chcesz wywołać.
- **✔️ rozważyć** użycie tego samego nazewnictwa i wielkich liter w przypadku wartości stałych.
- **✔️** Użyj typów .NET, które są mapowane bliżej typu natywnego. Na przykład, w C#, użyj `uint` , gdy typem natywnym `unsigned int`jest.
- **✔️ są** używane `[In]` i `[Out]` atrybuty tylko wtedy, gdy zachowanie jest inne niż domyślne zachowanie.
- **✔️ rozważyć** użycie <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> usługi do puli natywnych buforów tablicowych.
- **✔️ Rozważ** zapakowanie deklaracji P/Invoke w klasie o tej samej nazwie i wielkości liter jako biblioteki natywnej.
  - Dzięki `[DllImport]` temu atrybuty mogą C# `nameof` korzystać z funkcji języka w celu przekazania nazwy biblioteki natywnej i upewnienia się, że nie jest ona błędną nazwą biblioteki natywnej.

## <a name="dllimport-attribute-settings"></a>Ustawienia atrybutów DllImport

| Ustawienie | Domyślny | Zalecenie | Szczegóły |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  Zachowaj domyślne  | Jeśli ta opcja jest jawnie ustawiona na false, Niepowodzenie zwracanych wartości HRESULT spowoduje włączenie wyjątków (a wartość zwracana w definicji zmieni się na wartość null).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | zależy od interfejsu API  | Ustaw tę wartość na true, jeśli interfejs API używa wartości GetLastError i użyj Marshal. metodę GetLastWin32Error, aby pobrać wartość. Jeśli interfejs API ustawi warunek informujący o błędzie, należy uzyskać błąd przed wywołaniem innych wywołań, aby uniknąć niezamierzonego nadpisania.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, która powraca do `CharSet.Ansi` zachowania  | Jawne użycie `CharSet.Unicode` lub `CharSet.Ansi` gdy ciągi lub znaki są obecne w definicji | Określa to kierowanie zachowania ciągów i to, `ExactSpelling` co `false`robi. Pamiętaj, `CharSet.Ansi` że jest to w rzeczywistości UTF8 w systemie UNIX. _Większość_ czasu Windows używa standardu Unicode, podczas gdy w systemie UNIX używa kodowania UTF8. Więcej informacji na temat zestawów [znaków](./charset.md)można znaleźć w dokumentacji. |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Ustaw tę wartość na true i uzyskaj niewielką korzyść w zakresie wydajności, ponieważ środowisko uruchomieniowe nie będzie szukać alternatywnych nazw funkcji z sufiksem "a" lub "w" w zależności od wartości `CharSet` ustawienia ("a" dla `CharSet.Ansi` i "w" dla `CharSet.Unicode`). |

## <a name="string-parameters"></a>Parametry ciągu

Gdy zestaw znaków jest Unicode lub argument jest jawnie `[MarshalAs(UnmanagedType.LPWSTR)]` oznaczony jako _i_ ciąg jest przenoszona przez wartość (not `ref` lub `out`), ciąg zostanie przypięty i użyty bezpośrednio przez kod natywny (zamiast kopiować).

Pamiętaj, `[DllImport]` aby oznaczyć element `Charset.Unicode` jako, chyba że jawnie zachodzi konieczność traktowania ciągów znaków ANSI.

**❌ Nie** używać `[Out] string` parametrów. Parametry ciągu przesłane przez wartość z `[Out]` atrybutem mogą destabilizację środowiska uruchomieniowego, jeśli ciąg jest ciągiem z stażystami. Zobacz więcej informacji na temat sposobu informowania o ciągach w dokumentacji dotyczącej programu <xref:System.String.Intern%2A?displayProperty=nameWithType>.

**❌ Unikać** `StringBuilder` parametry. `StringBuilder`kierowanie *zawsze* tworzy natywną kopię buforu. W związku z tym może być wyjątkowo niewydajne. Zapoznaj się z typowym scenariuszem wywoływania interfejsu API systemu Windows, który pobiera ciąg:

1. Utwórz SB o żądanej pojemności (przydzieli zarządzaną pojemność) **{1}**
2. wywoływanie
   1. Przydziela bufor natywny **{2}**  
   2. Kopiuje zawartość, jeśli `[In]` _( `StringBuilder` wartość domyślna parametru)_  
   3. Kopiuje bufor macierzysty do nowo przydzielonej tablicy zarządzanej, jeśli `[Out]` **{3}** _(również `StringBuilder`domyślnie dla)_  
3. `ToString()`alokuje jeszcze inną zarządzaną tablicę **{4}**

Jest to *{4}* alokacje w celu pobrania ciągu z kodu natywnego. Najlepszym rozwiązaniem jest to, aby ograniczyć to użycie w innym wywołaniu `StringBuilder` , ale nadal tylko *1* przydział. Znacznie lepiej jest używać bufora `ArrayPool`znaków i pamięci podręcznej, a następnie można przejść do przydziału `ToString()` dla kolejnych wywołań.

Innym problemem `StringBuilder` jest to, że zawsze kopiuje kopię zapasową buforu powrotu do pierwszej wartości null. Jeśli przeszedł ciąg zakończony nieprzerwanie lub jest ciągiem o podwójnej wartości null, element P/Invoke jest niewłaściwy.

W `StringBuilder`przypadku *korzystania z* programu Gotcha, że pojemność nie obejmuje ukrytych wartości null, które zawsze **są uwzględniane w** ramach międzyoperacyjności. Jest to często używane w przypadku, gdy większość interfejsów API ma rozmiar buforu, *łącznie* z wartością null. Może to spowodować marnowanie/niepotrzebne alokacje. Ponadto ta Gotcha uniemożliwia środowisko uruchomieniowe optymalizacji `StringBuilder` organizowania, aby zminimalizować kopie.

**✔️ rozważyć** użycie `char[]`s z `ArrayPool`.

Aby uzyskać więcej informacji na temat organizowania ciągów, zobacz [domyślne kierowanie dla ciągów](../../framework/interop/default-marshaling-for-strings.md) i [Dostosowywanie organizowania ciągów](customize-parameter-marshaling.md#customizing-string-parameters).

> __Specyficzne dla systemu Windows__  
> Dla `[Out]` ciągów, które domyślnie są `CoTaskMemFree` używane przez środowisko CLR do zwalniania ciągów lub `SysStringFree` ciągów, które `UnmanagedType.BSTR`są oznaczone jako.  
**W przypadku większości interfejsów API z buforem ciągu wyjściowego:**  
> Liczba przesłanych znaków musi zawierać wartość null. Jeśli zwracana wartość jest mniejsza niż przekazana liczba znaków, wywołanie zakończyło się pomyślnie, a wartość jest liczbą znaków *bez* końcowej wartości null. W przeciwnym razie liczba jest wymaganym rozmiarem bufora, w *tym* znakiem null.  
>
> - Przekaż 5, Pobierz 4: Ciąg zawiera 4 znaki o długości końcowej null.
> - Przekaż 5, Pobierz 6: Ciąg ma długość 5 znaków, a potrzeba przechowania wartości null w buforze zawierającym 6 znaków.  
> [Typy danych systemu Windows dla ciągów](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Parametry i pola logiczne

Wartości logiczne są łatwe w obsłudze. Domyślnie środowisko .NET `bool` jest organizowane w systemie Windows `BOOL`, gdzie jest wartością 4-bajtową. Jednak, i `bool` typy w C i C++ są *pojedynczym* bajtem. `_Bool` Może to prowadzić do trudnej śledzenia błędów w postaci połowy wartości zwracanej zostanie odrzucone, co *spowoduje jedynie zmianę* wyniku. Aby uzyskać więcej informacji o kierowaniu wartości `bool` .NET do języka C C++ `bool` lub typów, zobacz dokumentację dotyczącą [dostosowywania kierowania pól logicznych](customize-struct-marshaling.md#customizing-boolean-field-marshaling).

## <a name="guids"></a>Identyfikatory GUID

Identyfikatory GUID można używać bezpośrednio w sygnaturach. Wiele interfejsów API `GUID&` systemu Windows korzysta z `REFIID`aliasów typu, takich jak. Gdy są przesyłane przez odwołanie, mogą być przesyłane przez `ref` lub `[MarshalAs(UnmanagedType.LPStruct)]` z atrybutem.

| Identyfikator GUID | Według-ref — identyfikator GUID |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

**❌ nie** Używać `[MarshalAs(UnmanagedType.LPStruct)]` dla elementów innych niż `ref` parametry GUID.

## <a name="blittable-types"></a>Typy danych kopiowalnych

Typy danych kopiowalnych są typami, które mają taką samą reprezentację na poziomie bitowym w kodzie zarządzanym i natywnym. W związku z tym nie trzeba przekonwertowane do innego formatu, który ma być zorganizowany do i z kodu natywnego, a w miarę zwiększania wydajności powinny one być preferowane.

**Typy danych kopiowalnych:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- niezagnieżdżone tablice jednowymiarowe typów danych kopiowalnych (na przykład `int[]`)
- struktury i klasy ze stałym układem, które mają tylko typy wartości danych kopiowalnych dla pól wystąpień
  - układ stały wymaga `[StructLayout(LayoutKind.Sequential)]` lub`[StructLayout(LayoutKind.Explicit)]`
  - struktury są `LayoutKind.Sequential` domyślnie, klasy są`LayoutKind.Auto`

**NIE danych kopiowalnych:**

- `bool`

**Czasami danych kopiowalnych:**

- `char`, `string`

Gdy typy danych kopiowalnych są przesyłane przez odwołanie, są one po prostu przypięte przez organizatora, zamiast kopiować do buforu pośredniego. (Klasy są z założenia przesyłane przez odwołanie, struktury są przesyłane przez odwołanie, gdy jest `ref` używany `out`z lub).

`char`jest danych kopiowalnych w tablicy jednowymiarowej **lub** , jeśli jest częścią typu, który zawiera, jest jawnie oznaczona `[StructLayout]` przy użyciu. `CharSet = CharSet.Unicode`

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string`jest danych kopiowalnych, jeśli nie jest zawarty w innym typie i jest przenoszona jako argument, który jest oznaczony za `[MarshalAs(UnmanagedType.LPWStr)]` pomocą `[DllImport]` lub ma `CharSet = CharSet.Unicode` ustawioną wartość.

Możesz sprawdzić, czy typ to danych kopiowalnych, próbując utworzyć przypięty `GCHandle`. Jeśli typ nie jest ciągiem lub jest traktowany jako `GCHandle.Alloc` danych kopiowalnych, zostanie `ArgumentException`zgłoszony.

**✔️** , gdy to możliwe, danych kopiowalnych struktury.

Aby uzyskać więcej informacji, zobacz:

- [Typy kopiowalne i niekopiowalne](../../framework/interop/blittable-and-non-blittable-types.md)  
- [Kierowanie typów](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Utrzymywanie aktywności obiektów zarządzanych

`GC.KeepAlive()`Upewnij się, że obiekt pozostaje w zakresie, dopóki nie zostanie osiągnięta Metoda utrzymywania aktywności.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)umożliwia Organizatorowi utrzymywanie obiektu na czas trwania elementu P/Invoke. Może być używany zamiast `IntPtr` podpisów metod. `SafeHandle`efektywnie zastępuje tę klasę i powinny być używane zamiast tego.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)umożliwia Przypinanie obiektu zarządzanego i uzyskanie wskaźnika natywnego do niego. Wzorzec podstawowy to:  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Przypinanie nie jest domyślne `GCHandle`dla elementu. Inny wzorzec główny polega na przekazaniu odwołania do zarządzanego obiektu za pomocą kodu natywnego i z powrotem do kodu zarządzanego, zazwyczaj przy użyciu wywołania zwrotnego. Oto wzorzec:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Nie zapomnij `GCHandle` , że musi być jawnie zwolnione, aby uniknąć przecieków pamięci.

## <a name="common-windows-data-types"></a>Typowe typy danych systemu Windows

Poniżej znajduje się lista typów danych używanych w interfejsach API systemu Windows, C# które mają być używane podczas wywoływania kodu systemu Windows.

Następujące typy są takie same, jak w przypadku systemu Windows 32-bitowego i 64-bitowego, niezależnie od ich nazw.

| Szerokość | Windows          | C (Windows)          | C#       | Różne                          |
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

Następujące typy, które są wskaźnikami, są zgodne z szerokością platformy. Użyj `IntPtr` / tego elementu`UIntPtr` .

| Typy wskaźników ze znakiem `IntPtr`(Użyj) | Niepodpisane typy wskaźnika ( `UIntPtr`Użyj) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

System Windows `PVOID` , który jest C `void*` , może `IntPtr` być zorganizowany jako lub `UIntPtr`, ale preferowany `void*` , jeśli jest to możliwe.

[Typy danych systemu Windows](/windows/desktop/WinProg/windows-data-types)

[Zakresy typu danych](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Struktury

Zarządzane struktury są tworzone na stosie i nie są usuwane, dopóki metoda nie zwróci metody. Według definicji są one "przypięte" (nie są przenoszone przez wykaz globalny). Można również po prostu przełączyć adres w niebezpieczny blok kodu, jeśli kod natywny nie będzie używać wskaźnika poza końcem bieżącej metody.

Struktury danych kopiowalnych są znacznie bardziej wydajne, ponieważ mogą być używane bezpośrednio przez warstwę kierującą. Spróbuj utworzyć struktury danych kopiowalnych (na przykład unikać `bool`). Aby uzyskać więcej informacji, zobacz sekcję [typy danych kopiowalnych](#blittable-types) .

*Jeśli* struktura jest danych kopiowalnych, użyj `sizeof()` zamiast niej `Marshal.SizeOf<MyStruct>()` , aby uzyskać lepszą wydajność. Jak wspomniano powyżej, można sprawdzić, czy typ to danych kopiowalnych, próbując utworzyć przypięty `GCHandle`. Jeśli typ nie jest ciągiem lub uznano za danych kopiowalnych, `GCHandle.Alloc` spowoduje to `ArgumentException`zgłoszenie.

Wskaźniki do struktur w definicjach muszą być przesyłane przez `ref` `unsafe` lub i `*`.

**✔️** być zgodna z zarządzaną strukturą jak najbliżej kształtu i nazw, które są używane w oficjalnej dokumentacji lub nagłówku platformy.

aby zwiększyć wydajność, C# `sizeof()` ✔️ używać `Marshal.SizeOf<MyStruct>()` danych kopiowalnych zamiast for for Structure.

Tablica, taka `INT_PTR Reserved1[2]` jak musi być organizowana do dwóch `IntPtr` pól, `Reserved1a` i `Reserved1b`. Gdy natywna tablica jest typem pierwotnym, możemy użyć `fixed` słowa kluczowego, aby napisać je nieco bardziej czysty. Na przykład `SYSTEM_PROCESS_INFORMATION` wygląda to w postaci natywnego nagłówka:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

W C#programie możemy napisać następujący element:

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

Istnieje jednak kilka pytania dotyczące usługi z stałymi buforami. Stałe bufory typów innych niż danych kopiowalnych nie będą poprawnie organizowane, więc tablica w miejscu musi być rozwijana do wielu pojedynczych pól. Ponadto w .NET Framework i .NET Core przed 3,0, jeśli struktura zawierająca pole stałego buforu jest zagnieżdżona w strukturze innej niż danych kopiowalnych, stałe pole buforu nie będzie poprawnie organizowane w kodzie natywnym.
