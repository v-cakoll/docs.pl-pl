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
ms.openlocfilehash: 8ba1651583f4cd962f5038fbe0e3f55a5d8b42ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589678"
---
# <a name="marshaling-classes-structures-and-unions"></a>Marshaling klas, struktur i unii
Klasy i struktury są podobne w .NET Framework. Jednocześnie może mieć pola, właściwości i zdarzenia. Może to być również metody statyczne i Niestatyczne. Jeden zauważalnej różnicy jest struktury są typami wartości a klasy są typami odwołań.  
  
 W poniższej tabeli wymieniono opcje marshaling klas, struktur i Unii; w tym artykule opisano ich użycie; zawiera również link do odpowiedniej platformy wywołania próbki.  
  
|Typ|Opis|Przykład|  
|----------|-----------------|------------|  
|Klasa przez wartość.|Przekazuje klasy z elementami członkowskimi całkowitą jako parametr wejście/wyjście, podobnie jak w przypadku zarządzanych.|SysTime — przykład|  
|Struktura przez wartość.|Przekazuje struktury, tak jak parametry.|Przykłady struktur|  
|Struktura przez odwołanie.|Przekazuje struktury jako we/wy parametrów.|OSInfo — Przykład|  
|Struktura przy użyciu zagnieżdżonych struktur (spłaszczonych).|Przekazuje klasę, która reprezentuje strukturę, przy użyciu zagnieżdżonych struktur w funkcji niezarządzanej. Struktura jest spłaszczany jeden duży struktury w prototypie zarządzanych.|FindFile — przykład|  
|Struktura za pomocą wskaźnika do innej struktury.|Przekazuje strukturę, która zawiera wskaźnik do struktury drugi jako członek.|Przykłady struktur|  
|Tablica struktury z liczbami całkowitymi, przez wartość.|Przekazuje tablicę struktur, które zawierają tylko liczby całkowite jako parametr wejście/wyjście. Elementy członkowskie tablicy można zmieniać.|Przykłady tablic|  
|Tablica struktury z liczbami całkowitymi i ciągów według odwołania.|Przekazuje tablicę struktury, które zawierają liczby całkowite i ciągi jako parametrem Out. Wywołana funkcja przydziela pamięć dla tablicy.|OutArrayOfStructs — Przykład|  
|Związki z typami wartości.|Przekazuje złożenia typów wartości (integer i double).|przykład unii|  
|Związki z mieszane typy.|Przekazuje związki z mieszane typy (liczba całkowita i ciąg).|przykład unii|  
|Wartości null w strukturze.|Przekazuje odwołanie o wartości null (**nic** w języku Visual Basic) zamiast odwołania do typu wartości.|HandleRef — przykład|  
  
## <a name="structures-sample"></a>Przykłady struktur  
 W tym przykładzie pokazano, jak przekazać strukturę, która wskazuje na strukturę drugi, przekazać struktury z osadzonego struktury i przekazać strukturę z osadzoną tablicę.  
  
 Structs — przykład używa następujących funkcji niezarządzanych, wyświetlane wraz z ich oryginalną deklaracją funkcji:  
  
-   **TestStructInStruct** eksportowany z PinvokeLib.dll.  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   **TestStructInStruct3** exported from PinvokeLib.dll.  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   **TestArrayInStruct** eksportowany z PinvokeLib.dll.  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 [PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) jest niestandardową biblioteką niezarządzaną, która zawiera implementacje dla wyżej wymienionych funkcji i cztery struktury: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, i **MYARRAYSTRUCT**. Te struktury zawierają następujące elementy:  
  
```  
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
  
 Zarządzany `MyPerson`, `MyPerson2`, `MyPerson3`, i `MyArrayStruct` struktury mają następujące cechy:  
  
-   `MyPerson` zawiera tylko składowe ciągu. [CharSet](specifying-a-character-set.md) pola ustawia ciągi formatu ANSI, gdy przekazywane do funkcji niezarządzanych.  
  
-   `MyPerson2` zawiera **IntPtr** do `MyPerson` struktury. **IntPtr** typu zastępuje oryginalny wskaźnik do struktury niezarządzanej, ponieważ aplikacje programu .NET Framework nie należy używać wskaźników, chyba że kod jest oznaczony **niebezpieczne**.  
  
-   `MyPerson3` zawiera `MyPerson` jako struktura osadzonych. Struktury osadzone w ramach innej struktury mogą spłaszczone, umieszczając elementy osadzone struktury bezpośrednio w głównym struktury lub go może pozostać osadzone struktury, co jest wykonywane na w tym przykładzie.  
  
-   `MyArrayStruct` zawiera tablicę liczb całkowitych. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu zestawu <xref:System.Runtime.InteropServices.UnmanagedType> wartość wyliczenia do **ByValArray**, który służy do wskazywania liczby elementów w tablicy.  
  
 W przypadku wszystkich struktur, w tym przykładzie <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut jest stosowany do upewnij się, że elementy członkowskie są rozmieszczone w pamięci sekwencyjnej, w kolejności, w jakiej są wyświetlane.  
  
 `LibWrap` Klasa zawiera zarządzane prototypy `TestStructInStruct`, `TestStructInStruct3`, i `TestArrayInStruct` metody wywoływane przez `App` klasy. Każdy prototypu deklaruje jeden parametr w następujący sposób:  
  
-   `TestStructInStruct` deklaruje odwołanie do typu `MyPerson2` jako parametr.  
  
-   `TestStructInStruct3` Typ deklaruje `MyPerson3` jako parametr i przekazuje parametr według wartości.  
  
-   `TestArrayInStruct` deklaruje odwołanie do typu `MyArrayStruct` jako parametr.  
  
 Struktury jako argumenty do metod są przekazywane według wartości, chyba że zawiera parametr **ref** (**ByRef** w języku Visual Basic) słowa kluczowego. Na przykład `TestStructInStruct` metoda kończy się powodzeniem (wartość adresu) odwołanie do obiektu typu `MyPerson2` do kodu niezarządzanego. Do manipulowania struktury, `MyPerson2` wskazuje, przykładowy skrypt tworzy bufor o określonym rozmiarze i zwraca jego adres, łącząc <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody. Następnie przykładowy skrypt kopiuje zawartość struktury zarządzanej do niezarządzanego buforu. Ponadto w przykładzie użyto <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metodę dane organizatora z buforu niezarządzane do zarządzanego obiektu i <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metody, aby zwolnić niezarządzane bloku pamięci.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a>FindFile — przykład  
 W tym przykładzie pokazano, jak przekazać strukturę, która zawiera strukturę drugi, osadzone do niezarządzanej funkcji. Ilustruje też sposób używania <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby zadeklarować tablicę o stałej długości w taki sposób, w obrębie struktury. W tym przykładzie osadzone elementy są dodawane do nadrzędnej struktury. Przykładowy osadzony struktury, która nie jest spłaszczany [przykłady struktur](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100)).  
  
 Findfile — przykład używa następującej funkcji niezarządzanej, wyświetlane z jej oryginalną deklaracją funkcji:  
  
-   **FindFirstFile** exported from Kernel32.dll.  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 Oryginalna struktury przekazany do funkcji zawiera następujące elementy:  
  
```  
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
  
 W tym przykładzie `FindData` klasa zawiera element członkowski danych odpowiednich dla każdego elementu pierwotnej struktury i osadzone struktury. Zamiast dwóch oryginalnego buforów znak klasy zastępuje ciągów. **MarshalAsAttribute** ustawia <xref:System.Runtime.InteropServices.UnmanagedType> wyliczeniu, aby **ByValTStr**, który jest używany do identyfikowania wbudowanej, tablice znaków o stałej długości, które pojawiają się w obrębie struktury niezarządzanej.  
  
 `LibWrap` Klasa zawiera zarządzane prototyp `FindFirstFile` metody, która przekazuje `FindData` klasy jako parametr. Parametr musi być zadeklarowany z <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybutów, ponieważ klasy, które są typami odwołań, są przekazywane w parametrach domyślnie.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a>przykład unii  
 Niniejszy przykład pokazuje, jak przekazać struktury zawierające tylko typy wartości i struktury zawierające typ wartości i ciąg jako parametry do niezarządzanej funkcji, oczekiwano Unii. Unia reprezentuje lokalizacji w pamięci, która może być współużytkowana przez dwa lub więcej zmiennych.  
  
 Przykład Unii używa następującej funkcji niezarządzanej, wyświetlane z jej oryginalną deklaracją funkcji:  
  
-   **TestUnion** eksportowany z PinvokeLib.dll.  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 [PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) jest niestandardową biblioteką niezarządzaną, zawierający implementację wyżej wymienionych funkcji i dwa rozłączne **MYUNION** i **MYUNION2**. Unie zawierają następujące elementy:  
  
```  
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
  
 W kodzie zarządzanym Unii są definiowane jako struktury. `MyUnion` Struktura zawiera dwa typy wartości jako elementy członkowskie: całkowitą, a wartość o podwójnej precyzji. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Ma ustawioną wartość atrybutu sterują położeniem dokładne każdy element członkowski danych. <xref:System.Runtime.InteropServices.FieldOffsetAttribute> Atrybut zawiera fizyczne położenie pola w reprezentacji niezarządzanej Unii. Zwróć uwagę, że oba elementy mają taką samą przesunięcia wartości, więc elementy członkowskie można zdefiniować w tej samej części pamięci.  
  
 `MyUnion2_1` i `MyUnion2_2` zawierają typ wartości (liczba całkowita) i ciąg, odpowiednio. W kodzie zarządzanym typy wartości i odwołań nie są dozwolone do nakładają się na siebie. W przykładzie użyto metody przeciążenie umożliwia obiekt wywołujący, aby użyć obu typów, przy wywołaniu tej samej funkcji niezarządzanych. Układ `MyUnion2_1` jawnego i ma dokładne wartości przesunięcia. Z kolei `MyUnion2_2` ma układzie sekwencyjnego, ponieważ jawne układy nie są dozwolone w przypadku typów referencyjnych. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu zestawu <xref:System.Runtime.InteropServices.UnmanagedType> wyliczeniu, aby **ByValTStr**, który jest używany do identyfikowania wbudowanej, tablice znaków o stałej długości, które są wyświetlane w reprezentacji niezarządzanej Unii.  
  
 `LibWrap` Klasa zawiera prototypy `TestUnion` i `TestUnion2` metody. `TestUnion2` jest przeciążona, aby zadeklarować `MyUnion2_1` lub `MyUnion2_2` jako parametry.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a>SysTime — przykład  
 W tym przykładzie pokazano, jak przekazać wskaźnik do klasy do niezarządzanej funkcji, która oczekuje wskaźnika do struktury.  
  
 Systime — przykład używa następującej funkcji niezarządzanej, wyświetlane z jej oryginalną deklaracją funkcji:  
  
-   **GetSystemTime** exported from Kernel32.dll.  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 Oryginalna struktury przekazany do funkcji zawiera następujące elementy:  
  
```  
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
  
 W tym przykładzie `SystemTime` klasy zawiera elementy oryginalnej struktury, które są reprezentowane jako elementy członkowskie klasy. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Ma ustawioną wartość atrybutu upewnij się, że elementy członkowskie są rozmieszczone w pamięci sekwencyjnej, w kolejności, w jakiej są wyświetlane.  
  
 `LibWrap` Klasa zawiera zarządzane prototyp `GetSystemTime` metody, która przekazuje `SystemTime` klasy jako In/Out parametru domyślnie. Parametr musi być zadeklarowany z <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybutów, ponieważ klasy, które są typami odwołań, są przekazywane w parametrach domyślnie. Do obiektu wywołującego otrzymać wyników są [atrybuty kierunkowe](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100)) muszą być stosowane w sposób jawny. `App` Klasy tworzy nowe wystąpienie klasy `SystemTime` klasy i uzyskuje dostęp do jego pola danych.  
  
### <a name="code-samples"></a>Przykłady kodu  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs — przykład  
 Niniejszy przykład pokazuje, jak przekazać tablicy struktur zawiera liczby całkowite i ciągi jako parametrów do niezarządzanej funkcji Out.  
  
 Ten przykład pokazuje sposób wywołania funkcji natywnej przy użyciu <xref:System.Runtime.InteropServices.Marshal> klasy i za pomocą niebezpieczny kod.  
  
 W tym przykładzie użyto funkcji otoki, a platforma wywołuje zdefiniowane w [PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100))także dostępny w folderze plików źródłowych. Używa ona `TestOutArrayOfStructs` funkcji i `MYSTRSTRUCT2` struktury. Struktura zawiera następujące elementy:  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 `MyStruct` Klasa zawiera obiekt ciągu znaków ANSI. <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole określa ANSI format. `MyUnsafeStruct`, zawierające struktury jest <xref:System.IntPtr> typu zamiast ciągu.  
  
 `LibWrap` Klasa zawiera przeciążone `TestOutArrayOfStructs` metody prototypu. Jeśli metoda deklaruje wskaźnik, jako parametr, klasa powinien być oznaczony przez `unsafe` — słowo kluczowe. Ponieważ [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nie można użyć niebezpieczny kod metody przeciążonej, modyfikator unsafe i `MyUnsafeStruct` struktury nie są konieczne.  
  
 `App` Klasy implementuje `UsingMarshaling` metody, która wykonuje zadania niezbędne do przekazania tablicy. Tablica jest oznaczona za pomocą `out` (`ByRef` w języku Visual Basic) słowa kluczowego, aby wskazać, że dane przekazuje z / / wywoływany do elementu wywołującego. Implementacja używa następujących <xref:System.Runtime.InteropServices.Marshal> metody klasy:  
  
-   <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> Aby zorganizować dane z buforu niezarządzane do zarządzanego obiektu.  
  
-   <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> Aby zwolnić pamięć zarezerwowane dla ciągów w strukturze.  
  
-   <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> Aby zwolnić pamięć, zarezerwowane dla tablicy.  
  
 Jak wcześniej wspomniano, C# umożliwia niebezpieczny kod i [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nie. W C# próbki, `UsingUnsafePointer` jest implementacją alternatywną metodą, który używa wskaźników zamiast <xref:System.Runtime.InteropServices.Marshal> klasy w celu przekazania kopii, tablica zawierająca `MyUnsafeStruct` struktury.  
  
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
- [Typy danych w wywołaniu platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))
- [Marshaling ciągów](marshaling-strings.md)
- [Organizowanie tablic typów](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))
