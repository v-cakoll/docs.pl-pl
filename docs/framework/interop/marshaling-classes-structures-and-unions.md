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
ms.openlocfilehash: be4c15f1093f359eeb9e742464b9d9e1dd5c756e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="marshaling-classes-structures-and-unions"></a>Marshaling klas, struktur i unii
Klasy i struktury są podobne w programie .NET Framework. Obydwie pola, właściwości i zdarzeń. Może to być również metody statyczne i Niestatyczne. Jeden znacząca różnica jest struktury są typy wartości oraz klasy są typy referencyjne.  
  
 W poniższej tabeli wymieniono opcje marshaling klas, struktur i Unii; w tym artykule opisano sposób ich użycia; zawiera również link do odpowiednich platform wywołania próbki.  
  
|Typ|Opis|Przykład|  
|----------|-----------------|------------|  
|Klasa przez wartość.|Przekazuje klasy z elementami członkowskimi całkowitą jako parametr we/wy, takich jak w przypadku zarządzanych.|SysTime — przykład|  
|Struktura przez wartość.|Przekazuje struktury tak jak parametry.|Przykład struktury|  
|Struktura przez odwołanie.|Przekazuje struktury jako we/wy parametrów.|OSInfo — Przykład|  
|Struktura z struktury zagnieżdżone (spłaszczonych).|Przekazuje klasa, która reprezentuje struktury zawierającej zagnieżdżone struktury w funkcji niezarządzanej. Struktura jest spłaszczona jeden duży struktury w zarządzanych prototypu.|FindFile — przykład|  
|Struktura za pomocą wskaźnika na inną strukturę.|Przekazuje struktura, która zawiera wskaźnik do drugiego struktury jako element członkowski.|Przykłady struktur|  
|Tablica struktury z liczbami całkowitymi przez wartość.|Przekazuje tablicy struktur, które zawierają tylko liczby całkowite jako parametr we/wy. Elementy członkowskie tablicy można zmieniać.|Przykłady tablic|  
|Tablica struktury z liczbami całkowitymi i ciągi przez odwołanie.|Przekazuje tablicę struktury zawierające liczby całkowite i ciągi jako parametrem Out. Wywoływana funkcja przydziela pamięć dla tablicy.|OutArrayOfStructs — Przykład|  
|Unie z typami wartości.|Przekazuje złożenia typów wartości (integer i double).|przykład unii|  
|Unie z mieszane typy.|Przekazuje unie z mieszane typy (liczba całkowita i ciąg).|przykład unii|  
|Wartości null w strukturze.|Przekazuje odwołanie o wartości null (**nic** w języku Visual Basic) zamiast odwołania do typu wartości.|HandleRef — przykład|  
  
## <a name="structures-sample"></a>Przykład struktury  
 W tym przykładzie pokazano, jak przekazać struktura, która wskazuje na strukturę drugiego, Przekaż struktury o strukturze osadzonych i przekaż struktury z osadzoną tablicę.  
  
 Przykład struktury używa następujących funkcji niezarządzane, przedstawiono ich oryginalnej deklaracji funkcji:  
  
-   **TestStructInStruct** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   **TestStructInStruct3** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   **TestArrayInStruct** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) jest niestandardowa biblioteka niezarządzane, zawierający implementacji dla funkcji wymienione wcześniej i cztery struktury: **MYPERSON**, **MYPERSON2**,  **MYPERSON3**, i **MYARRAYSTRUCT**. Te struktury zawierają następujące elementy:  
  
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
  
 Zarządzanej `MyPerson`, `MyPerson2`, `MyPerson3`, i `MyArrayStruct` struktury ma następujące cechy:  
  
-   `MyPerson` zawiera tylko elementy członkowskie ciągu. [CharSet](specifying-a-character-set.md) pola ustawia ciągi do formatu ANSI przekazany do funkcji niezarządzanej.  
  
-   `MyPerson2` zawiera **IntPtr** do `MyPerson` struktury. **IntPtr** typu zastępuje oryginalny wskaźnik do struktury niezarządzane, ponieważ aplikacji .NET Framework nie należy używać wskaźników, jeśli kod jest oznaczony jako **niebezpieczne**.  
  
-   `MyPerson3` zawiera `MyPerson` osadzone struktury. Struktury osadzone w inną strukturę można spłaszczenia umieszczając elementy osadzone struktury bezpośrednio w głównym struktury lub można je pozostawić struktury osadzone, co jest wykonywane w tym przykładzie.  
  
-   `MyArrayStruct` zawiera tablicę liczb całkowitych. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut ustawia <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia **ByValArray**, który służy do wskazywania liczba elementów w tablicy.  
  
 W przypadku wszystkich struktur w tym przykładzie <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut jest stosowany do zapewnienia, że członkowie ułożone w pamięci sekwencyjnie, w kolejności ich występowania.  
  
 `LibWrap` Klasa zawiera zarządzanych prototypy dla `TestStructInStruct`, `TestStructInStruct3`, i `TestArrayInStruct` metody wywoływane przez `App` klasy. Każdy prototypu deklaruje pojedynczy parametr w następujący sposób:  
  
-   `TestStructInStruct` deklaruje odwołanie do typu `MyPerson2` jako jego parametr.  
  
-   `TestStructInStruct3` deklaruje typ `MyPerson3` jako jego parametr, a następnie przekazuje przez wartość parametru.  
  
-   `TestArrayInStruct` deklaruje odwołanie do typu `MyArrayStruct` jako jego parametr.  
  
 Struktury jako argumenty do metod są przekazywane przez wartość, o ile nie zawiera parametru **ref** (**ByRef** w języku Visual Basic) — słowo kluczowe. Na przykład `TestStructInStruct` metoda przekazuje (wartość adresu) odwołanie do obiektu typu `MyPerson2` do kodu niezarządzanego. Do modyfikowania struktury który `MyPerson2` wskazuje, próbki tworzy buforu o określonym rozmiarze i zwraca jego adres łącząc <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody. Następnie próbki kopiuje zawartość struktury zarządzane do niezarządzanego buforu. Ponadto w przykładzie użyto <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metodę kierowanie danych z bufora niezarządzane do zarządzanego obiektu i <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metody, aby zwolnić niezarządzane bloku pamięci.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a>FindFile — przykład  
 W tym przykładzie pokazano, jak przekazać struktura, która zawiera drugi, osadzone struktury do funkcji niezarządzanej. Ponadto przedstawiono sposób użycia <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby zadeklarować tablicę o stałej długości w strukturze. W tym przykładzie elementy osadzone struktury są dodawane do struktury nadrzędnej. Przykładowy osadzone struktury, który nie jest spłaszczona [przykładowej struktury](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100)).  
  
 Przykładowe FindFile używa następujących niezarządzanej funkcji wyświetlany z jego oryginalnej deklaracji funkcji:  
  
-   **FindFirstFile** wyeksportowane z Kernel32.dll.  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 Pierwotnej struktury przekazany do funkcji zawiera następujące elementy:  
  
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
  
 W tym przykładzie `FindData` klasa zawiera odpowiedni element członkowski danych dla każdego elementu pierwotnej struktury i osadzone struktury. Zamiast dwóch oryginalnego buforów znak klasy zastępuje ciągów. **Atrybut MarshalAsAttribute** ustawia <xref:System.Runtime.InteropServices.UnmanagedType> wyliczeniu, aby **ByValTStr**, który służy do identyfikowania wbudowanej, stałych znak o stałej długości, która są umieszczone w nawiasach niezarządzane struktury.  
  
 `LibWrap` Klasa zawiera zarządzanych prototyp `FindFirstFile` metodę, która przekazuje `FindData` klasy jako parametr. Parametr musi być zadeklarowany ze <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybutów, ponieważ klasy, które są typy odwołań, są przekazywane jak parametry domyślnie.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a>przykład unii  
 W tym przykładzie pokazano, jak przekazywać struktury zawierające tylko typy wartości i struktury zawierające wartość typu i ciągu jako parametry funkcji niezarządzanej oczekiwano Unii. Unia reprezentuje lokalizację pamięci, która może być współużytkowane przez dwa lub więcej zmiennych.  
  
 Przykładowe unie używa następujących niezarządzanej funkcji wyświetlany z jego oryginalnej deklaracji funkcji:  
  
-   **TestUnion** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) jest niestandardowa biblioteka niezarządzane zawierającego implementację funkcji wymienione wcześniej i unie dwóch **MYUNION** i **MYUNION2**. Unie zawiera następujące elementy:  
  
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
  
 W kodzie zarządzanym unie są definiowane jako struktury. `MyUnion` Struktura zawiera dwa typy wartości jako elementy członkowskie: całkowitą i wartość o podwójnej precyzji. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut jest ustawiony do kontrolowania dokładności dla każdego elementu członkowskiego danych. <xref:System.Runtime.InteropServices.FieldOffsetAttribute> Atrybutu zawiera fizycznych pozycji pól w niezarządzanych reprezentację Unii. Zwróć uwagę, że oba elementy mają te same wartości przesunięcia tak członków można zdefiniować tego samego elementu pamięci.  
  
 `MyUnion2_1` i `MyUnion2_2` zawierają odpowiednio typu wartości (liczba całkowita) i ciągu. W kodzie zarządzanym typy wartości i typy referencyjne nie są dozwolone nakładanie się. W przykładzie użyto metody przeładowanie, aby włączyć obiekt wywołujący, aby korzystać z obu typów podczas wywoływania tej samej funkcji niezarządzanej. Układ `MyUnion2_1` jawne i ma dokładne wartości przesunięcia. Z kolei `MyUnion2_2` ma układ sekwencyjny, ponieważ jawne układów są niedozwolone w typach odwołań. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut ustawia <xref:System.Runtime.InteropServices.UnmanagedType> wyliczeniu, aby **ByValTStr**, który służy do identyfikowania wbudowanej, stałych znak o stałej długości, która są wyświetlane w niezarządzanych reprezentację Unii.  
  
 `LibWrap` Klasa zawiera prototypy dla `TestUnion` i `TestUnion2` metody. `TestUnion2` jest przeciążona, aby zadeklarować `MyUnion2_1` lub `MyUnion2_2` jako parametry.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a>SysTime — przykład  
 W tym przykładzie pokazano, jak przekazać wskaźnik do klasy niezarządzanej funkcji, która oczekuje wskaźnika do struktury.  
  
 Przykładowe SysTime używa następujących niezarządzanej funkcji wyświetlany z jego oryginalnej deklaracji funkcji:  
  
-   **GetSystemTime** wyeksportowane z Kernel32.dll.  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 Pierwotnej struktury przekazany do funkcji zawiera następujące elementy:  
  
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
  
 W tym przykładzie `SystemTime` klasa zawiera elementy pierwotnej struktury reprezentowane jako elementy członkowskie klasy. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut ma ustawioną upewnij się, że członkowie ułożone w pamięci sekwencyjnie, w kolejności ich występowania.  
  
 `LibWrap` Klasa zawiera zarządzanych prototyp `GetSystemTime` metodę, która przekazuje `SystemTime` klasy jako In/Out parametru domyślnie. Parametr musi być zadeklarowany ze <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybutów, ponieważ klasy, które są typy odwołań, są przekazywane jak parametry domyślnie. Dla obiekt wywołujący, aby otrzymywać wyniki te [kierunkową atrybuty](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100)) muszą być stosowane w sposób jawny. `App` Klasy tworzy nowe wystąpienie klasy `SystemTime` klasy i uzyskuje dostęp do swoich pól danych.  
  
### <a name="code-samples"></a>Przykłady kodu  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs — przykład  
 W tym przykładzie pokazano, jak przekazać tablicę struktury, która zawiera liczby całkowite i ciągi jako parametry do funkcji niezarządzanej Out.  
  
 W tym przykładzie pokazano, jak wywoływanie funkcji natywnych przy użyciu <xref:System.Runtime.InteropServices.Marshal> klasy i przy użyciu niebezpieczny kod.  
  
 W przykładzie użyto funkcji otoki i platformy wywołuje zdefiniowane w [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)), również podana w plikach źródłowych. Używa `TestOutArrayOfStructs` funkcji i `MYSTRSTRUCT2` struktury. Struktura zawiera następujące elementy:  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 `MyStruct` Klasa zawiera obiekt ciągu znaków ANSI. <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole określa formacie ANSI. `MyUnsafeStruct`, jest strukturą zawierającego <xref:System.IntPtr> typu zamiast ciągu.  
  
 `LibWrap` Klasa zawiera przeciążone `TestOutArrayOfStructs` metody prototypu. Jeśli metoda deklaruje wskaźnikiem jako parametru, klasa powinien być oznaczony przez `unsafe` — słowo kluczowe. Ponieważ [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nie można użyć niebezpieczny kod przeciążonej metody modyfikator niebezpieczne i `MyUnsafeStruct` struktury nie jest konieczne.  
  
 `App` Klasa implementuje `UsingMarshaling` metodę, która wykonuje zadania niezbędne do przekazania do tablicy. Tablica jest oznaczony atrybutem `out` (`ByRef` w języku Visual Basic) — słowo kluczowe, aby wskazać, że dane przekazuje z wywoływany do wywołującego. Implementacja używa następujących <xref:System.Runtime.InteropServices.Marshal> metody klasy:  
  
-   <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> do organizowania danych z bufora niezarządzane do zarządzanego obiektu.  
  
-   <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> Aby zwolnić pamięć zarezerwowana dla ciągów w strukturze.  
  
-   <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> Aby zwolnić pamięć zarezerwowana dla tablicy.  
  
 Jak wcześniej wspomniano, C# umożliwia niebezpieczny kod i [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nie. W przykładowym C# `UsingUnsafePointer` jest implementację alternatywną metodę, która używa wskaźników zamiast <xref:System.Runtime.InteropServices.Marshal> klasy do przekazania kopii tablica zawierająca `MyUnsafeStruct` struktury.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a>Zobacz też  
 [Marshaling danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)  
 [Typy danych wywołanie platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Marshaling ciągów](marshaling-strings.md)  
 [Organizowanie tablice typów](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))
