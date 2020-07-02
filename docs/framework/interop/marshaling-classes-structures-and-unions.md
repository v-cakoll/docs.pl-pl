---
title: Marshaling klas, struktur i unii
description: Przejrzyj sposób organizowania klas, struktur i Unii. Wyświetl przykłady klas organizowania, struktur z zagnieżdżonymi strukturami, tablicami struktur i Unii.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
ms.openlocfilehash: 5e616b5bb513939cadd8fe5c72675ba0b6e070a3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621525"
---
# <a name="marshaling-classes-structures-and-unions"></a>Marshaling klas, struktur i unii

Klasy i struktury są podobne do .NET Framework. Oba mogą mieć pola, właściwości i zdarzenia. Mogą także mieć statyczne i niestatyczne metody. Istotną różnicą jest to, że struktury są typami wartości, a klasy są typami referencyjnymi.

W poniższej tabeli wymieniono opcje organizowania klas, struktur i Unii; opisuje ich użycie; i zawiera link do odpowiedniego wywołania platformy.

|Typ|Opis|Przykład|
|----------|-----------------|------------|
|Klasa według wartości.|Przekazuje klasę z składowymi liczb całkowitych jako parametr in/out, jak w przypadku wystąpienia zarządzanego.|[SysTime — przykład](#systime-sample)|
|Struktura według wartości.|Przekazuje struktury zgodnie z parametrami.|[Przykłady struktur](#structures-sample)|
|Struktura przez odwołanie.|Przekazuje struktury jako parametry wejściowe/out.|[OSInfo — Przykład](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|
|Struktura ze strukturami zagnieżdżonymi (spłaszczone).|Przekazuje klasę, która reprezentuje strukturę z zagnieżdżonymi strukturami w funkcji niezarządzanej. Struktura jest spłaszczona do jednej dużej struktury w zarządzanym prototypie.|[FindFile — przykład](#findfile-sample)|
|Struktura ze wskaźnikiem do innej struktury.|Przekazuje strukturę, która zawiera wskaźnik do drugiej struktury jako element członkowski.|[Przykłady struktur](#structures-sample)|
|Tablica struktur z liczbami całkowitymi przez wartość.|Przekazuje tablicę struktur, które zawierają tylko liczby całkowite jako parametr in/out. Elementy członkowskie tablicy można zmienić.|[Przykłady tablic](marshaling-different-types-of-arrays.md)|
|Tablica struktur z liczbami całkowitymi i ciągami przez odwołanie.|Przekazuje tablicę struktur, które zawierają liczby całkowite i ciągi jako parametr out. Wywołana funkcja przydziela pamięć tablicy.|[OutArrayOfStructs — Przykład](#outarrayofstructs-sample)|
|Unii z typami wartości.|Przekazuje Unię z typami wartości (integer i Double).|[przykład unii](#unions-sample)|
|Unii z typami mieszanymi.|Przekazuje Unii z typami mieszanymi (liczbami całkowitymi i ciągami).|[przykład unii](#unions-sample)|
|Struktura z układem specyficznym dla platformy.|Przekazuje typ z natywnymi definicjami pakowania.|[Przykład platformy](#platform-sample)|
|Wartości null w strukturze.|Przekazuje odwołanie o wartości null (**Nothing** w Visual Basic) zamiast odwołania do typu wartości.|[HandleRef — przykład](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))|

## <a name="structures-sample"></a>Przykłady struktur

Ten przykład pokazuje, jak przekazać strukturę, która wskazuje na drugą strukturę, przekazać strukturę z osadzoną strukturą i przekazać strukturę z osadzoną tablicą.  
  
W przykładowych strukturach są używane następujące funkcje niezarządzane, pokazane wraz z ich oryginalną deklaracją funkcji:

- **TestStructInStruct** wyeksportowany z PinvokeLib.dll.

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- **TestStructInStruct3** wyeksportowany z PinvokeLib.dll.

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- **TestArrayInStruct** wyeksportowany z PinvokeLib.dll.

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementacje wcześniej wymienionych funkcji i **MYPERSON**cztery struktury: **MYPERSON2**, **MYPERSON3**i **MYARRAYSTRUCT**. Struktury te zawierają następujące elementy:

```cpp
typedef struct _MYPERSON
{
   char* first;
   char* last;
} MYPERSON, *LP_MYPERSON;

typedef struct _MYPERSON2
{
   MYPERSON* person;
   int age;
} MYPERSON2, *LP_MYPERSON2;

typedef struct _MYPERSON3
{
   MYPERSON person;
   int age;
} MYPERSON3;

typedef struct _MYARRAYSTRUCT
{
   bool flag;
   int vals[ 3 ];
} MYARRAYSTRUCT;
```

Struktury zarządzane `MyPerson` , `MyPerson2` , `MyPerson3` i `MyArrayStruct` mają następującą cechę:

- `MyPerson`zawiera tylko elementy członkowskie ciągu. Pole [charset](specifying-a-character-set.md) ustawia ciągi na format ANSI w przypadku przekazywania do funkcji niezarządzanej.

- `MyPerson2`zawiera element **IntPtr** do `MyPerson` struktury. Typ **IntPtr** zastępuje oryginalny wskaźnik do struktury niezarządzanej, ponieważ .NET Framework aplikacje nie używają wskaźników, chyba że kod jest oznaczony jako **niebezpieczny**.

- `MyPerson3`zawiera `MyPerson` jako osadzoną strukturę. Strukturę osadzoną w innej strukturze można spłaszczyć, umieszczając elementy osadzonej struktury bezpośrednio w strukturze głównej, lub można ją pozostawić jako osadzoną strukturę, jak w tym przykładzie.

- `MyArrayStruct`zawiera tablicę liczb całkowitych. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Atrybut ustawia <xref:System.Runtime.InteropServices.UnmanagedType> wartość wyliczenia na **ByValArray**, która jest używana do wskazania liczby elementów w tablicy.

Dla wszystkich struktur w tym przykładzie <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut jest stosowany, aby upewnić się, że elementy członkowskie są uporządkowane w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.

`NativeMethods`Klasa zawiera zarządzane prototypy dla `TestStructInStruct` `TestStructInStruct3` metod, i `TestArrayInStruct` wywoływanych przez `App` klasę. Każdy prototyp deklaruje jeden parametr w następujący sposób:

- `TestStructInStruct`deklaruje odwołanie do typu `MyPerson2` jako jego parametru.

- `TestStructInStruct3`deklaruje typ `MyPerson3` jako parametr i przekazuje parametr przez wartość.

- `TestArrayInStruct`deklaruje odwołanie do typu `MyArrayStruct` jako jego parametru.

Struktury jako argumenty metod są przekazane przez wartość, chyba że parametr zawiera słowo kluczowe **ref** (**ByRef** in Visual Basic). Na przykład `TestStructInStruct` Metoda przekazuje odwołanie (wartość adresu) do obiektu typu `MyPerson2` do niezarządzanego kodu. Aby manipulować strukturą `MyPerson2` wskazującą, przykład tworzy bufor o określonym rozmiarze i zwraca jego adres przez połączenie <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metod i. Następnie przykład kopiuje zawartość zarządzanej struktury do bufora niezarządzanego. Na koniec przykład używa <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metody do organizowania danych z niezarządzanego bufora do obiektu zarządzanego i <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metody zwalniania niezarządzanego bloku pamięci.

### <a name="declaring-prototypes"></a>Deklarowanie prototypów

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a>Wywoływanie funkcji

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a>FindFile — przykład

Ten przykład pokazuje, jak przekazać strukturę, która zawiera drugą, osadzoną strukturę do niezarządzanej funkcji. Pokazano również, jak używać atrybutu, <xref:System.Runtime.InteropServices.MarshalAsAttribute> Aby zadeklarować tablicę o stałej długości w strukturze. W tym przykładzie elementy osadzonej struktury są dodawane do struktury nadrzędnej. Aby zapoznać się z przykładową strukturą osadzoną, która nie została spłaszczona, zobacz [przykładowe struktury](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).

Przykład FindFile — używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:

- **FindFirstFile** wyeksportowany z Kernel32.dll.

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

Oryginalna struktura przeniesiona do funkcji zawiera następujące elementy:

```cpp
typedef struct _WIN32_FIND_DATA
{
  DWORD    dwFileAttributes;
  FILETIME ftCreationTime;
  FILETIME ftLastAccessTime;
  FILETIME ftLastWriteTime;
  DWORD    nFileSizeHigh;
  DWORD    nFileSizeLow;
  DWORD    dwReserved0;
  DWORD    dwReserved1;
  TCHAR    cFileName[ MAX_PATH ];
  TCHAR    cAlternateFileName[ 14 ];
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;
```

W tym przykładzie `FindData` Klasa zawiera odpowiedni element członkowski danych dla każdego elementu oryginalnej struktury i osadzonej struktury. Zamiast dwóch oryginalnych buforów znaków Klasa zastępuje ciągi. **MarshalAsAttribute** ustawia <xref:System.Runtime.InteropServices.UnmanagedType> Wyliczenie na **ByValTStr**, które służy do identyfikowania wbudowanych tablic znaków o stałej długości, które są wyświetlane w strukturze niezarządzanych.

`NativeMethods`Klasa zawiera zarządzany prototyp `FindFirstFile` metody, która przekazuje `FindData` klasę jako parametr. Parametr musi być zadeklarowany za pomocą <xref:System.Runtime.InteropServices.InAttribute> atrybutów i, <xref:System.Runtime.InteropServices.OutAttribute> ponieważ klasy, które są typami odwołań, są domyślnie przenoszone jako parametry w parametrach.

### <a name="declaring-prototypes"></a>Deklarowanie prototypów

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a>Wywoływanie funkcji

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a>przykład unii

Ten przykład pokazuje, jak przekazać struktury zawierające tylko typy wartości i struktury zawierające typ wartości i ciąg jako parametry do niezarządzanej funkcji, która oczekuje złożenia. Unia reprezentuje lokalizację pamięci, która może być współużytkowana przez dwie lub więcej zmiennych.

Przykład Unii używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:

- **TestUnion** wyeksportowany z PinvokeLib.dll.

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementację wcześniej wymienionej funkcji i dwa **związki Union** i **MYUNION2**. Unii zawierają następujące elementy:

```cpp
union MYUNION
{
    int number;
    double d;
}

union MYUNION2
{
    int i;
    char str[128];
};
```

W kodzie zarządzanym Unii są zdefiniowane jako struktury. `MyUnion`Struktura zawiera dwa typy wartości jako elementy członkowskie: liczbę całkowitą i podwójną. <xref:System.Runtime.InteropServices.StructLayoutAttribute>Atrybut jest ustawiony na kontrolowanie precyzyjnej pozycji każdego elementu członkowskiego danych. Ten <xref:System.Runtime.InteropServices.FieldOffsetAttribute> atrybut zawiera fizyczną pozycję pól w niezarządzanej reprezentacji Unii. Zwróć uwagę, że oba elementy członkowskie mają te same wartości przesunięcia, dlatego członkowie mogą definiować ten sam fragment pamięci.

`MyUnion2_1`i `MyUnion2_2` zawierają odpowiednio typ wartości (Integer) i ciąg. W kodzie zarządzanym, typy wartości i typy referencyjne nie mogą nakładać się na siebie. Ten przykład używa przeciążania metody, aby umożliwić wywołującemu używanie obu typów podczas wywoływania tej samej funkcji niezarządzanej. Układ `MyUnion2_1` jest jawny i ma precyzyjną wartość przesunięcia. W przeciwieństwie `MyUnion2_2` ma układ sekwencyjny, ponieważ jawne układy są niedozwolone w przypadku typów referencyjnych. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Atrybut ustawia <xref:System.Runtime.InteropServices.UnmanagedType> Wyliczenie na **ByValTStr**, który jest używany do identyfikowania wbudowanej tablicy znaków o stałej długości, która pojawia się w niezarządzanej reprezentacji Unii.

`NativeMethods`Klasa zawiera prototypy dla `TestUnion` `TestUnion2` metod i. `TestUnion2`jest przeciążony do zadeklarowania `MyUnion2_1` lub `MyUnion2_2` jako parametry.

### <a name="declaring-prototypes"></a>Deklarowanie prototypów

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a>Wywoływanie funkcji

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a>Przykład platformy

W niektórych scenariuszach `struct` i `union` układy mogą się różnić w zależności od platformy dostosowanej. Rozważmy na przykład typ, który jest [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) zdefiniowany w scenariuszu com:

```c++
#include <pshpack8.h> /* Defines the packing of the struct */
typedef struct _STRRET
    {
    UINT uType;
    /* [switch_is][switch_type] */ union
        {
        /* [case()][string] */ LPWSTR pOleStr;
        /* [case()] */ UINT uOffset;
        /* [case()] */ char cStr[ 260 ];
        }  DUMMYUNIONNAME;
    }  STRRET;
#include <poppack.h>
```

Powyższe `struct` jest zadeklarowane z nagłówkami systemu Windows, które mają wpływ na układ pamięci typu. W przypadku zdefiniowania w środowisku zarządzanym te szczegóły układu są konieczne do prawidłowego współdziałania z kodem natywnym.

Poprawną zarządzaną definicję tego typu w procesie 32-bitowym jest:

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 264)]
public struct STRRET_32
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(4)]
    public IntPtr pOleStr;

    [FieldOffset(4)]
    public uint uOffset;

    [FieldOffset(4)]
    public IntPtr cStr;
}
```

W procesie 64-bitowym, przesunięcie rozmiaru *i* pola są różne. Prawidłowy układ to:

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 272)]
public struct STRRET_64
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(8)]
    public IntPtr pOleStr;

    [FieldOffset(8)]
    public uint uOffset;

    [FieldOffset(8)]
    public IntPtr cStr;
}
```

Niepowodzenie poprawnego rozważenia układu natywnego w scenariuszu międzyoperacyjnym może spowodować losowe awarie i gorszenie nieprawidłowych obliczeń.

Domyślnie zestawy .NET mogą działać w wersji 32-bitowej i 64-bitowej środowiska uruchomieniowego .NET. Aplikacja musi czekać do momentu uruchomienia, aby zdecydować, które z poprzednich definicji mają być używane.

Poniższy fragment kodu przedstawia przykład sposobu wyboru między definicją 32-bitową i 64-bitową w czasie wykonywania.

```CSharp
if (IntPtr.Size == 8)
{
    // Use the STRRET_64 definition
}
else
{
    Debug.Assert(IntPtr.Size == 4);
    // Use the STRRET_32 definition
}
```

## <a name="systime-sample"></a>SysTime — przykład

Ten przykład pokazuje, jak przekazać wskaźnik do klasy do niezarządzanej funkcji, która oczekuje wskaźnika do struktury.

Przykład SysTime — używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:

- **GetSystemTime** wyeksportowany z Kernel32.dll.

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

Oryginalna struktura przeniesiona do funkcji zawiera następujące elementy:

```cpp
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

W tym przykładzie `SystemTime` Klasa zawiera elementy oryginalnej struktury reprezentowane jako elementy członkowskie klasy. <xref:System.Runtime.InteropServices.StructLayoutAttribute>Atrybut jest ustawiony tak, aby upewnić się, że elementy członkowskie są ułożone w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.

`NativeMethods`Klasa zawiera zarządzany prototyp `GetSystemTime` metody, która `SystemTime` Domyślnie przekazuje klasę jako parametr we/out. Parametr musi być zadeklarowany za pomocą <xref:System.Runtime.InteropServices.InAttribute> atrybutów i, <xref:System.Runtime.InteropServices.OutAttribute> ponieważ klasy, które są typami odwołań, są domyślnie przenoszone jako parametry w parametrach. Aby obiekt wywołujący otrzymywał wyniki, należy jawnie zastosować te [atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) . `App`Klasa tworzy nowe wystąpienie `SystemTime` klasy i uzyskuje dostęp do jego pól danych.

### <a name="code-samples"></a>Przykłady kodu

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs — przykład

Ten przykład pokazuje, jak przekazać tablicę struktur, które zawierają liczby całkowite i ciągi jako parametry out do niezarządzanej funkcji.

Ten przykład pokazuje, jak wywołać funkcję natywną przy użyciu <xref:System.Runtime.InteropServices.Marshal> klasy i za pomocą niebezpiecznego kodu.

W tym przykładzie są używane funkcje otoki i wywołanie platformy zdefiniowane w [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), również dostępne w plikach źródłowych. Używa `TestOutArrayOfStructs` funkcji i `MYSTRSTRUCT2` struktury. Struktura zawiera następujące elementy:

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

`MyStruct`Klasa zawiera obiekt String znaków ANSI. <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>Pole określa format ANSI. `MyUnsafeStruct`, jest strukturą zawierającą <xref:System.IntPtr> Typ zamiast ciągu.

`NativeMethods`Klasa zawiera przeciążoną `TestOutArrayOfStructs` metodę prototypu. Jeśli Metoda deklaruje wskaźnik jako parametr, Klasa powinna być oznaczona za pomocą `unsafe` słowa kluczowego. Ponieważ Visual Basic nie może używać niebezpiecznego kodu, przeciążona metoda, modyfikator niebezpieczny i `MyUnsafeStruct` Struktura nie są potrzebne.

`App`Klasa implementuje `UsingMarshaling` metodę, która wykonuje wszystkie zadania niezbędne do przekazania tablicy. Tablica jest oznaczona za pomocą `out` `ByRef` słowa kluczowego (w Visual Basic), aby wskazać, że dane są przekazywane do obiektu wywołującego. Implementacja używa następujących <xref:System.Runtime.InteropServices.Marshal> metod klasy:

- <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>kierowanie danych z bufora niezarządzanego do obiektu zarządzanego.

- <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>zwalnianie pamięci zarezerwowanej dla ciągów w strukturze.

- <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>zwalnianie pamięci zarezerwowanej dla tablicy.

Jak wspomniano wcześniej, język C# zezwala na niebezpieczny kod i Visual Basic nie. W przykładzie w języku C# `UsingUnsafePointer` jest alternatywną implementacją metody, która używa wskaźników zamiast <xref:System.Runtime.InteropServices.Marshal> klasy do przekazania tablicy zawierającej `MyUnsafeStruct` strukturę.

### <a name="declaring-prototypes"></a>Deklarowanie prototypów

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a>Wywoływanie funkcji

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a>Zobacz także

- [Organizowanie danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)
- [Organizowanie ciągów](marshaling-strings.md)
- [Organizowanie różnych typów tablic](marshaling-different-types-of-arrays.md)
