---
title: Marshaling klas, struktur i unii
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a53c8b7b88bd25a6611c33218c7a386de55889e9
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2019
ms.locfileid: "71151762"
---
# <a name="marshaling-classes-structures-and-unions"></a>Marshaling klas, struktur i unii
Klasy i struktury są podobne do .NET Framework. Oba mogą mieć pola, właściwości i zdarzenia. Mogą także mieć statyczne i niestatyczne metody. Istotną różnicą jest to, że struktury są typami wartości, a klasy są typami referencyjnymi.  
  
 W poniższej tabeli wymieniono opcje organizowania klas, struktur i Unii; opisuje ich użycie; i zawiera link do odpowiedniego wywołania platformy.  
  
|Typ|Opis|Przykład|  
|----------|-----------------|------------|  
|Klasa według wartości.|Przekazuje klasę z składowymi liczb całkowitych jako parametr in/out, jak w przypadku wystąpienia zarządzanego.|SysTime — przykład|  
|Struktura według wartości.|Przekazuje struktury zgodnie z parametrami.|Przykłady struktur|  
|Struktura przez odwołanie.|Przekazuje struktury jako parametry wejściowe/out.|OSInfo — Przykład|  
|Struktura ze strukturami zagnieżdżonymi (spłaszczone).|Przekazuje klasę, która reprezentuje strukturę z zagnieżdżonymi strukturami w funkcji niezarządzanej. Struktura jest spłaszczona do jednej dużej struktury w zarządzanym prototypie.|FindFile — przykład|  
|Struktura ze wskaźnikiem do innej struktury.|Przekazuje strukturę, która zawiera wskaźnik do drugiej struktury jako element członkowski.|Przykłady struktur|  
|Tablica struktur z liczbami całkowitymi przez wartość.|Przekazuje tablicę struktur, które zawierają tylko liczby całkowite jako parametr in/out. Elementy członkowskie tablicy można zmienić.|Przykłady tablic|  
|Tablica struktur z liczbami całkowitymi i ciągami przez odwołanie.|Przekazuje tablicę struktur, które zawierają liczby całkowite i ciągi jako parametr out. Wywołana funkcja przydziela pamięć tablicy.|OutArrayOfStructs — Przykład|  
|Unii z typami wartości.|Przekazuje Unię z typami wartości (integer i Double).|przykład unii|  
|Unii z typami mieszanymi.|Przekazuje Unii z typami mieszanymi (liczbami całkowitymi i ciągami).|przykład unii|  
|Wartości null w strukturze.|Przekazuje odwołanie o wartości null (**Nothing** w Visual Basic) zamiast odwołania do typu wartości.|HandleRef — przykład|  
  
## <a name="structures-sample"></a>Przykłady struktur  
 Ten przykład pokazuje, jak przekazać strukturę, która wskazuje na drugą strukturę, przekazać strukturę z osadzoną strukturą i przekazać strukturę z osadzoną tablicą.  
  
 W przykładowych strukturach są używane następujące funkcje niezarządzane, pokazane wraz z ich oryginalną deklaracją funkcji:  
  
- **TestStructInStruct** wyeksportowany z PinvokeLib. dll.  
  
    ```cpp  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
- **TestStructInStruct3** wyeksportowany z PinvokeLib. dll.  
  
    ```cpp  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
- **TestArrayInStruct** wyeksportowany z PinvokeLib. dll.  
  
    ```cpp  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 [PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementacje wcześniej wymienionych funkcji i czterech struktur: **Osoby**, **MYPERSON2**, **MYPERSON3**i **MYARRAYSTRUCT**. Struktury te zawierają następujące elementy:  
  
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
  
 Struktury zarządzane `MyPerson`, `MyPerson2`, `MyPerson3` i`MyArrayStruct` mają następującą cechę:  
  
- `MyPerson`zawiera tylko elementy członkowskie ciągu. Pole [charset](specifying-a-character-set.md) ustawia ciągi na format ANSI w przypadku przekazywania do funkcji niezarządzanej.  
  
- `MyPerson2`zawiera element **IntPtr** do `MyPerson` struktury. Typ **IntPtr** zastępuje oryginalny wskaźnik do struktury niezarządzanej, ponieważ .NET Framework aplikacje nie używają wskaźników, chyba że kod jest oznaczony jako **niebezpieczny**.  
  
- `MyPerson3`zawiera `MyPerson` jako osadzoną strukturę. Strukturę osadzoną w innej strukturze można spłaszczyć, umieszczając elementy osadzonej struktury bezpośrednio w strukturze głównej, lub można ją pozostawić jako osadzoną strukturę, jak w tym przykładzie.  
  
- `MyArrayStruct`zawiera tablicę liczb całkowitych. Atrybut ustawia wartość wyliczenia na ByValArray, która jest używana do wskazania liczby elementów w tablicy. <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Runtime.InteropServices.UnmanagedType>  
  
 Dla wszystkich struktur w tym przykładzie <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut jest stosowany, aby upewnić się, że elementy członkowskie są uporządkowane w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.  
  
 `TestStructInStruct3` `TestStructInStruct` `App` `TestArrayInStruct` Klasa zawiera zarządzane prototypy dla metod, i wywoływanych przez klasę. `NativeMethods` Każdy prototyp deklaruje jeden parametr w następujący sposób:  
  
- `TestStructInStruct`deklaruje odwołanie do typu `MyPerson2` jako jego parametru.  
  
- `TestStructInStruct3`deklaruje `MyPerson3` typ jako parametr i przekazuje parametr przez wartość.  
  
- `TestArrayInStruct`deklaruje odwołanie do typu `MyArrayStruct` jako jego parametru.  
  
 Struktury jako argumenty metod są przekazane przez wartość, chyba że parametr zawiera słowo kluczowe **ref** (**ByRef** in Visual Basic). Na przykład `TestStructInStruct` Metoda przekazuje odwołanie (wartość adresu) do obiektu typu `MyPerson2` do niezarządzanego kodu. Aby manipulować strukturą `MyPerson2` wskazującą, przykład tworzy bufor o określonym rozmiarze i zwraca jego adres przez <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> połączenie metod i <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> . Następnie przykład kopiuje zawartość zarządzanej struktury do bufora niezarządzanego. Na koniec przykład używa <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metody do organizowania danych z niezarządzanego bufora do obiektu zarządzanego <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> i metody zwalniania niezarządzanego bloku pamięci.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a>FindFile — przykład  
 Ten przykład pokazuje, jak przekazać strukturę, która zawiera drugą, osadzoną strukturę do niezarządzanej funkcji. Pokazano również, jak używać atrybutu, <xref:System.Runtime.InteropServices.MarshalAsAttribute> aby zadeklarować tablicę o stałej długości w strukturze. W tym przykładzie elementy osadzonej struktury są dodawane do struktury nadrzędnej. Aby zapoznać się z przykładową strukturą osadzoną, która nie została spłaszczona, zobacz [przykładowe struktury](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).  
  
 Przykład FindFile — używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:  
  
- **FindFirstFile** wyeksportowany z pliku Kernel32. dll.  
  
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
  
 Klasa zawiera zarządzany prototyp `FindFirstFile` `FindData` metody, która przekazuje klasę jako parametr. `NativeMethods` Parametr musi być zadeklarowany za pomocą <xref:System.Runtime.InteropServices.InAttribute> atrybutów <xref:System.Runtime.InteropServices.OutAttribute> i, ponieważ klasy, które są typami odwołań, są domyślnie przenoszone jako parametry w parametrach.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a>przykład unii  
 Ten przykład pokazuje, jak przekazać struktury zawierające tylko typy wartości i struktury zawierające typ wartości i ciąg jako parametry do niezarządzanej funkcji, która oczekuje złożenia. Unia reprezentuje lokalizację pamięci, która może być współużytkowana przez dwie lub więcej zmiennych.  
  
 Przykład Unii używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:  
  
- **TestUnion** wyeksportowany z PinvokeLib. dll.  
  
    ```cpp
    void TestUnion(MYUNION u, int type);  
    ```  
  
 [PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementację wcześniej wymienionej funkcji i dwa Unii, **Reunion** i **MYUNION2**. Unii zawierają następujące elementy:  
  
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
  
 W kodzie zarządzanym Unii są zdefiniowane jako struktury. `MyUnion` Struktura zawiera dwa typy wartości jako elementy członkowskie: liczbę całkowitą i podwójną. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut jest ustawiony na kontrolowanie precyzyjnej pozycji każdego elementu członkowskiego danych. Ten <xref:System.Runtime.InteropServices.FieldOffsetAttribute> atrybut zawiera fizyczną pozycję pól w niezarządzanej reprezentacji Unii. Zwróć uwagę, że oba elementy członkowskie mają te same wartości przesunięcia, dlatego członkowie mogą definiować ten sam fragment pamięci.  
  
 `MyUnion2_1`i `MyUnion2_2` zawierają odpowiednio typ wartości (Integer) i ciąg. W kodzie zarządzanym, typy wartości i typy referencyjne nie mogą nakładać się na siebie. Ten przykład używa przeciążania metody, aby umożliwić wywołującemu używanie obu typów podczas wywoływania tej samej funkcji niezarządzanej. Układ `MyUnion2_1` jest jawny i ma precyzyjną wartość przesunięcia. W przeciwieństwie `MyUnion2_2` ma układ sekwencyjny, ponieważ jawne układy są niedozwolone w przypadku typów referencyjnych. Atrybut ustawia Wyliczenie na ByValTStr, który jest używany do identyfikowania wbudowanej tablicy znaków o stałej długości, która pojawia się w niezarządzanej reprezentacji Unii. <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Runtime.InteropServices.UnmanagedType>  
  
 Klasa zawiera prototypy `TestUnion` dla metod i `TestUnion2`. `NativeMethods` `TestUnion2`jest przeciążony do `MyUnion2_1` zadeklarowania lub `MyUnion2_2` jako parametry.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a>SysTime — przykład  
 Ten przykład pokazuje, jak przekazać wskaźnik do klasy do niezarządzanej funkcji, która oczekuje wskaźnika do struktury.  
  
 Przykład SysTime — używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:  
  
- **GetSystemTime** wyeksportowany z pliku Kernel32. dll.  
  
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
  
 W tym przykładzie `SystemTime` Klasa zawiera elementy oryginalnej struktury reprezentowane jako elementy członkowskie klasy. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut jest ustawiony tak, aby upewnić się, że elementy członkowskie są ułożone w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.  
  
 Klasa zawiera zarządzany prototyp `GetSystemTime` `SystemTime` metody, która domyślnie przekazuje klasę jako parametr we/out. `NativeMethods` Parametr musi być zadeklarowany za pomocą <xref:System.Runtime.InteropServices.InAttribute> atrybutów <xref:System.Runtime.InteropServices.OutAttribute> i, ponieważ klasy, które są typami odwołań, są domyślnie przenoszone jako parametry w parametrach. Aby obiekt wywołujący otrzymywał wyniki, należy jawnie zastosować te [atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) . Klasa tworzy nowe wystąpienie `SystemTime` klasy i uzyskuje dostęp do jego pól danych. `App`  
  
### <a name="code-samples"></a>Przykłady kodu  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs — przykład  
 Ten przykład pokazuje, jak przekazać tablicę struktur, które zawierają liczby całkowite i ciągi jako parametry out do niezarządzanej funkcji.  
  
 Ten przykład pokazuje, jak wywołać funkcję natywną przy użyciu <xref:System.Runtime.InteropServices.Marshal> klasy i za pomocą niebezpiecznego kodu.  
  
 W tym przykładzie używane są funkcje otoki i wywołanie platformy zdefiniowane w [PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), które są również dostępne w plikach źródłowych. Używa `TestOutArrayOfStructs` funkcji`MYSTRSTRUCT2` i struktury. Struktura zawiera następujące elementy:  
  
```cpp
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 `MyStruct` Klasa zawiera obiekt String znaków ANSI. <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole określa format ANSI. `MyUnsafeStruct`, jest strukturą zawierającą <xref:System.IntPtr> typ zamiast ciągu.  
  
 Klasa zawiera przeciążoną `TestOutArrayOfStructs` metodę prototypu. `NativeMethods` Jeśli Metoda deklaruje wskaźnik jako parametr, Klasa powinna być oznaczona za pomocą `unsafe` słowa kluczowego. Ponieważ Visual Basic nie może używać niebezpiecznego kodu, przeciążona metoda, modyfikator niebezpieczny i `MyUnsafeStruct` struktura nie są potrzebne.  
  
 `App` Klasa`UsingMarshaling` implementuje metodę, która wykonuje wszystkie zadania niezbędne do przekazania tablicy. Tablica jest oznaczona za pomocą `out` słowa kluczowego (`ByRef` w Visual Basic), aby wskazać, że dane są przekazywane do obiektu wywołującego. Implementacja używa następujących <xref:System.Runtime.InteropServices.Marshal> metod klasy:  
  
- <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>kierowanie danych z bufora niezarządzanego do obiektu zarządzanego.  
  
- <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>zwalnianie pamięci zarezerwowanej dla ciągów w strukturze.  
  
- <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>zwalnianie pamięci zarezerwowanej dla tablicy.  
  
 Jak wspomniano wcześniej C# , zezwala na niebezpieczny kod i Visual Basic nie. W C# przykładzie `UsingUnsafePointer` jest alternatywną implementacją metody, która używa <xref:System.Runtime.InteropServices.Marshal> wskaźników zamiast klasy `MyUnsafeStruct` do przekazania tablicy zawierającej strukturę.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a>Zobacz także

- [Marshaling danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)
- [Marshaling ciągów](marshaling-strings.md)
- [Organizowanie różnych typów tablic](marshaling-different-types-of-arrays.md)
