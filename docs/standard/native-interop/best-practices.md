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
# <a name="native-interoperability-best-practices"></a>Najlepsze rozwiązania dotyczące współpracy natywnej

.NET oferuje wiele sposobów dostosowywania natywnego kodu współdziałania. Ten artykuł zawiera wskazówki, które zespoły platformy .NET firmy Microsoft przestrzegać dla natywnej współdziałania.

## <a name="general-guidance"></a>Wskazówki ogólne

Wskazówki w tej sekcji dotyczy wszystkich scenariuszy interop.

- ✔️ DO używać tej samej nazwy i wielkich liter dla metod i parametrów, jak metoda natywna, którą chcesz wywołać.
- ✔️ NALEŻY ROZWAŻYĆ użycie tego samego nazewnictwa i wielkich liter dla wartości stałych.
- ✔️ do użycia typów .NET, które mapują najbliżej typu macierzystego. Na przykład w języku `uint` C#użyj, `unsigned int`gdy typem macierzystym jest .
- ✔️ DO używać `[In]` tylko `[Out]` i atrybuty, gdy zachowanie, które chcesz różni się od zachowania domyślnego.
- ✔️ NALEŻY ROZWAŻYĆ <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> użycie do puli buforów tablicy macierzystych.
- ✔️ NALEŻY ROZWAŻYĆ zawijanie deklaracji P/Invoke w klasie o takiej samej nazwie i wielkich literach jak biblioteka macierzysta.
  - Dzięki temu `[DllImport]` atrybuty do `nameof` korzystania z funkcji języka języka języka C# przekazać w nazwie biblioteki macierzystej i upewnij się, że nie błędnie nazwę biblioteki macierzystej.

## <a name="dllimport-attribute-settings"></a>Ustawienia atrybutu DllImport

| Ustawienie | Domyślne | Zalecenie | Szczegóły |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  zachowaj wartość domyślną  | Gdy jest jawnie ustawiona na false, nie powiodło się HRESULT zwracane wartości zostaną przekształcone w wyjątki (i zwraca wartość w definicji staje się null w wyniku).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | zależy od API  | Ustaw to na true, jeśli interfejs API używa GetLastError i użyj Marshal.GetLastWin32Error, aby uzyskać wartość. Jeśli interfejs API ustawia warunek, który mówi, że ma błąd, pobierz błąd przed wykonaniem innych wywołań, aby uniknąć nieumyślnego jego nadania.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, który wraca `CharSet.Ansi` do zachowania  | Jawnie `CharSet.Unicode` używać `CharSet.Ansi` lub gdy ciągi lub znaki są obecne w definicji | Określa zachowanie marshaling ciągów i `ExactSpelling` co `false`robi, gdy . Należy `CharSet.Ansi` pamiętać, że jest rzeczywiście UTF8 na Unix. _W_ większości przypadków system Windows używa unicode, podczas gdy Unix używa UTF8. Zobacz więcej informacji na temat [dokumentacji znaków](./charset.md). |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Ustaw tę wartość true i uzyskaj niewielką korzyść perf, ponieważ środowisko wykonawcze nie będzie szukać alternatywnych nazw funkcji z `CharSet` przyrostkiem "A" lub "W" w zależności od wartości ustawienia ("A" dla `CharSet.Ansi` i "W" dla `CharSet.Unicode`). |

## <a name="string-parameters"></a>Parametry ciągu

Gdy CharSet jest Unicode lub argument jest `[MarshalAs(UnmanagedType.LPWSTR)]` jawnie oznaczony jako _i_ ciąg jest przekazywany przez wartość (nie `ref` lub), `out`ciąg zostanie przypięty i używany bezpośrednio przez kod macierzysty (a nie kopiowane).

Pamiętaj, aby `[DllImport]` `Charset.Unicode` oznaczyć jako, chyba że wyraźnie chcesz ANSI leczenia strun.

❌NIE używaj `[Out] string` parametrów. Parametry ciągu przekazywane przez `[Out]` wartość z atrybutem może zdestabilizować środowisko uruchomieniowe, jeśli ciąg jest ciąg internowany. Zobacz więcej informacji na temat internowania ciągów w dokumentacji dla <xref:System.String.Intern%2A?displayProperty=nameWithType>.

❌UNIKNĄĆ `StringBuilder` parametrów. `StringBuilder`organizowanie *zawsze* tworzy natywną kopię buforu. Jako takie, może to być bardzo nieefektywne. Weź typowy scenariusz wywoływania interfejsu API systemu Windows, który przyjmuje ciąg:

1. Tworzenie SB żądanej pojemności (przydziela zarządzaną pojemność)**{1}**
2. Invoke
   1. Przydziela bufor macierzysty**{2}**
   2. Kopiuje zawartość, jeśli `[In]` _(domyślnie dla parametru) `StringBuilder` _
   3. Kopiuje bufor macierzysty do nowo `[Out]` **{3}** przydzielonej tablicy zarządzanej, jeśli _(również `StringBuilder`domyślnie)_
3. `ToString()`przydziela kolejną tablicę zarządzana**{4}**

To *{4}* jest alokacje, aby uzyskać ciąg z kodu macierzystego. Najlepsze, co możesz zrobić, aby ograniczyć to jest ponowne użycie `StringBuilder` w innym wywołaniu, ale to nadal zapisuje tylko *1* alokacji. Znacznie lepiej jest używać i buforować `ArrayPool`bufor znaków z — można następnie `ToString()` dostać się do tylko alokacji dla kolejnych wywołań.

Innym problemem `StringBuilder` jest to, że zawsze kopiuje buforu zwracanego z powrotem do pierwszej wartości null. Jeśli przekazany ciąg wstecz nie jest zakończony lub jest ciągiem zakończonym z podwójną wartością null, p/invoke jest w najlepszym wypadku niepoprawny.

Jeśli *używasz* `StringBuilder`, jeden ostatni gotcha jest to, że pojemność **nie** zawiera ukryte null, który jest zawsze rozliczane w interop. Jest to typowe dla ludzi, aby uzyskać ten błąd, jak większość interfejsów API chcesz rozmiar buforu, *w tym* null. Może to spowodować zmarnowane/niepotrzebne alokacje. Ponadto ten gotcha uniemożliwia środowisko uruchomieniowe `StringBuilder` optymalizacji organizowania, aby zminimalizować kopie.

✔️ ROZWAŻ użycie `char[]`s z `ArrayPool`pliku .

Aby uzyskać więcej informacji na temat organizowania [ciągów, zobacz Domyślne kierowanie ciągami i](../../framework/interop/default-marshaling-for-strings.md) [dostosowywanie ciągów .](customize-parameter-marshaling.md#customizing-string-parameters)

> __Specyficzne dla systemu Windows__ W `[Out]` przypadku ciągów CLR będzie domyślnie `CoTaskMemFree` `SysStringFree` używany do wolnych `UnmanagedType.BSTR`ciągów lub ciągów, które są oznaczone jako .
> **Dla większości interfejsów API z buforem ciągu wyjściowego:** Liczba przekazanych znaków musi zawierać wartość null. Jeśli zwracana wartość jest mniejsza niż liczba przekazanych znaków wywołanie zakończyło się pomyślnie, a wartość jest liczbą znaków *bez* końcowego null. W przeciwnym razie liczba jest wymagany rozmiar buforu, *w tym* znak null.
>
> - Pass in 5, get 4: Ciąg ma 4 znaki długości z końcowego null.
> - Przekaż w 5, get 6: Ciąg ma długość 5 znaków, potrzebujesz bufora 6 znaków, aby pomieścić wartość null.
> [Typy danych systemu Windows dla ciągów](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Parametry i pola logiczne

Wartości logiczne są łatwe do bałaganu. Domyślnie .NET `bool` jest organizowane do `BOOL`systemu Windows , gdzie jest to wartość 4-bajtowa. Jednak , `_Bool`i `bool` typy w C i C++ są *pojedynczym* bajtem. Może to prowadzić do trudnych do wyśledzenia błędów, ponieważ połowa wartości zwracanej zostanie odrzucona, co tylko *potencjalnie* zmieni wynik. Aby uzyskać więcej informacji na `bool` temat organizowania wartości `bool` .NET do typów C lub C++, zobacz dokumentację [dotyczącą dostosowywania zasadowania pól logicznych](customize-struct-marshaling.md#customizing-boolean-field-marshaling).

## <a name="guids"></a>Identyfikatory guid

Identyfikatory GUID można bezpośrednio ująć w podpisach. Wiele interfejsów API `GUID&` systemu Windows `REFIID`przyjmuje aliasy typów, takie jak . Po przejściu przez ref, mogą `ref` one być `[MarshalAs(UnmanagedType.LPStruct)]` przekazywane przez lub z atrybutem.

| Identyfikator GUID | Identyfikator GUID przez ref |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

❌NIE używaj `[MarshalAs(UnmanagedType.LPStruct)]` do `ref` niczego innego niż parametry GUID.

## <a name="blittable-types"></a>Typy blittable

Typy Blittable są typy, które mają taką samą reprezentację na poziomie bitowym w kodzie zarządzanym i macierzystym. W związku z tym nie muszą być konwertowane na inny format, który ma być organizowany do i z kodu macierzystego, a ponieważ zwiększa to wydajność powinny być preferowane.

**Typy Blittable:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- nie zagnieżdżone jednowymiarowe tablice typów `int[]`blittable (na przykład)
- struktury i klasy o stałym układzie, które mają tylko typy wartości blittable dla pól instancji
  - wymaga `[StructLayout(LayoutKind.Sequential)]` lub`[StructLayout(LayoutKind.Explicit)]`
  - struktury są `LayoutKind.Sequential` domyślnie, klasy są`LayoutKind.Auto`

**NIE blittable:**

- `bool`

**CZASAMI blittable:**

- `char`, `string`

Gdy typy blittable są przekazywane przez odwołanie, są one po prostu przypięte przez marshaller zamiast kopiowane do buforu pośredniego. (Klasy są z natury przekazywane przez odwołanie, struktury są `ref` `out`przekazywane przez odwołanie, gdy są używane z lub .)

`char`jest blittable w tablicy jednowymiarowej **lub** jeśli jest to część typu, `[StructLayout]` który `CharSet = CharSet.Unicode`zawiera jest jawnie oznaczone .

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string`jest blittable, jeśli nie jest zawarty w innym typie i jest przekazywany `[DllImport]` `CharSet = CharSet.Unicode` jako argument, który jest oznaczony `[MarshalAs(UnmanagedType.LPWStr)]` lub ma zestaw.

Możesz sprawdzić, czy typ jest blittable, próbując `GCHandle`utworzyć przypięty . Jeśli typ nie jest ciągiem lub uważany `GCHandle.Alloc` za `ArgumentException`blittable, zrzuci .

✔️ zrobić, aby twoje struktury blittable, gdy jest to możliwe.

Aby uzyskać więcej informacji, zobacz:

- [Typy kopiowalne i niekopiowalne](../../framework/interop/blittable-and-non-blittable-types.md)
- [Typ Marshaling](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Utrzymywanie obiektów zarządzanych przy życiu

`GC.KeepAlive()`zapewni, że obiekt pozostanie w zakresie, dopóki metoda KeepAlive nie zostanie trafiona.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)umożliwia marshaller zachować obiekt przy życiu na czas trwania P/Invoke. Może być używany zamiast `IntPtr` w podpisy metody. `SafeHandle`skutecznie zastępuje tę klasę i powinien być stosowany zamiast tego.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)umożliwia przypinanie obiektu zarządzanego i uzyskanie do niego natywnego wskaźnika. Podstawowy wzór to:

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Przypinanie nie jest `GCHandle`ustawieniem domyślnym dla . Inny wzorzec głównych jest przekazywanie odwołania do obiektu zarządzanego za pośrednictwem kodu macierzystego i z powrotem do kodu zarządzanego, zwykle z wywołaniem zwrotnym. Oto wzór:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Nie zapominaj, `GCHandle` że musi być jawnie uwolniony, aby uniknąć przecieków pamięci.

## <a name="common-windows-data-types"></a>Typowe typy danych systemu Windows

Oto lista typów danych powszechnie używanych w interfejsach API systemu Windows i typy C# do użycia podczas wywoływania kodu systemu Windows.

Następujące typy są tego samego rozmiaru w systemie Windows 32-bitowym i 64-bitowym, pomimo ich nazw.

| impulsów | Windows          | C (Windows)          | C#       | Alternatywnych                          |
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

Następujące typy, będąc wskaźniki, należy wykonać szerokość platformy. `IntPtr` / Użyj `UIntPtr` do nich.

| Typy wskaźników `IntPtr`podpisanych (używanie) | Niepodpisane typy `UIntPtr`wskaźników (użyj) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

System `PVOID` Windows, który `void*` jest C może `IntPtr` być `UIntPtr`organizowane `void*` jako jeden lub , ale wolą, gdy jest to możliwe.

[Typy danych systemu Windows](/windows/desktop/WinProg/windows-data-types)

[Zakresy typów danych](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Struktury

Struktury zarządzane są tworzone na stosie i nie są usuwane, dopóki metoda nie zwróci. Zgodnie z definicją są one "przypięte" (nie zostaną przeniesione przez GC). Można również po prostu wziąć adres w niebezpiecznych bloków kodu, jeśli kod macierzysty nie będzie używać wskaźnika poza koniec bieżącej metody.

Struktury Blittable są znacznie bardziej wydajne, ponieważ mogą być po prostu używane bezpośrednio przez warstwę organizowania. Spróbuj zrobić struktury blittable (na przykład, uniknąć `bool`). Aby uzyskać więcej informacji, zobacz [Blittable typy](#blittable-types) sekcji.

*Jeśli* struktura jest blittable, `sizeof()` należy `Marshal.SizeOf<MyStruct>()` użyć zamiast dla lepszej wydajności. Jak wspomniano powyżej, można sprawdzić, czy typ jest blittable, próbując `GCHandle`utworzyć przypięty . Jeśli typ nie jest ciągiem lub `GCHandle.Alloc` uważany za `ArgumentException`blittable, zrzuci plik .

Wskaźniki do struktur w definicjach muszą być `ref` przekazywane `unsafe` przez `*`lub używać i .

✔️ DO dopasować zarządzane struktury jak najbliżej kształtu i nazwy, które są używane w oficjalnej dokumentacji platformy lub nagłówka.

✔️ do użycia języka C# `sizeof()` zamiast `Marshal.SizeOf<MyStruct>()` struktur blittable w celu zwiększenia wydajności.

❌UNIKAJ `System.Delegate` używania pól lub `System.MulticastDelegate` pól do reprezentowania pól wskaźnika funkcji w strukturach.

Ponieważ <xref:System.Delegate?displayProperty=fullName> <xref:System.MulticastDelegate?displayProperty=fullName> i nie mają wymaganego podpisu, nie gwarantują, że pełnomocnik przeszedł będzie zgodny z podpisem kod macierzysty oczekuje. Ponadto w .NET Framework i .NET Core kierowanie struktury `System.Delegate` `System.MulticastDelegate` zawierającej lub z jego reprezentacji macierzystej do obiektu zarządzanego może zdestabilizować środowisko uruchomieniowe, jeśli wartość pola w reprezentacji macierzystej nie jest wskaźnikiem funkcji, który zawija zarządzanego delegata. W wersji .NET 5 i `System.Delegate` nowszych kierowanie lub `System.MulticastDelegate` pole z reprezentacji natywnej do obiektu zarządzanego nie jest obsługiwane. Użyj określonego typu delegata `System.Delegate` `System.MulticastDelegate`zamiast lub .

### <a name="fixed-buffers"></a>Stałe bufory

Tablica `INT_PTR Reserved1[2]` taka jak musi być `IntPtr` zorganizowana do dwóch pól `Reserved1a` i `Reserved1b`. Gdy tablica natywna jest typem `fixed` pierwotnym, możemy użyć słowa kluczowego, aby napisać go trochę bardziej czysto. Na przykład `SYSTEM_PROCESS_INFORMATION` wygląda następująco w nagłówku macierzystym:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

W języku C# możemy napisać to w ten sposób:

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

Istnieją jednak pewne gotchas ze stałymi buforami. Stałe bufory typów nietrwalonych nie będą poprawnie organizowane, więc tablica w miejscu musi zostać rozszerzona na wiele pojedynczych pól. Ponadto w programie .NET Framework i .NET Core przed 3.0, jeśli struktura zawierająca stałe pole buforu jest zagnieżdżona w strukturze nieduwalnej, stałe pole buforu nie zostanie poprawnie zorganizowane do kodu macierzystego.
