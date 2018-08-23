---
title: Typy wartości (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 17bbb0280c4db7d91e5d3cc3d3b6233b8db89cdc
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42754972"
---
# <a name="value-types-c-reference"></a>Typy wartości (odwołanie w C#)
Typy wartości obejmują dwie główne kategorie:  
  
-   [Struktury](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Wyliczenia](../../../csharp/language-reference/keywords/enum.md)  
  
 Struktury można podzielić na następujące kategorie:  
  
-   Typy liczbowe  
  
    -   [Typy całkowite](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [Typy zmiennoprzecinkowe](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   Struktury zdefiniowany przez użytkownika.  
  
## <a name="main-features-of-value-types"></a>Główne funkcje typów wartości  
 Zmienne, które są oparte na typach wartości bezpośrednio zawierają wartości. Przypisanie jednej zmiennej typu wartości do innej kopii zawarte wartości. To różni się od przypisania zmiennych typu odwołania, która kopiuje odwołanie do obiektu, ale nie samego obiektu.  
  
 Wszystkie typy wartości niejawnie pochodzą od <xref:System.ValueType?displayProperty=nameWithType>.  
  
 Inaczej niż w przypadku typów referencyjnych nie może pochodzić nowy typ z typem wartości. Jednakże, takie jak typy odwołań struktury mogą implementować interfejsów.  
  
 W przeciwieństwie do typów referencyjnych, typ wartości nie może zawierać `null` wartość. Jednak [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md) funkcja pozwala dla typów wartości, które ma być przypisane do `null`.  
  
 Różne wartości mają niejawnego domyślnego konstruktora, który jest inicjowana wartością domyślną tego typu. Aby uzyskać informacje o wartościach domyślnych typów wartości, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="main-features-of-simple-types"></a>Najważniejsze typy proste  
 Wszystkie typy proste — te całkowite języka C# — są aliasy typów programu .NET Framework System. Na przykład [int](../../../csharp/language-reference/keywords/int.md) jest aliasem <xref:System.Int32?displayProperty=nameWithType>. Aby uzyskać pełną listę aliasów, zobacz [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md).  
  
 Wyrażenia stałe, w której argumenty operacji są stałymi typu prostego, są obliczane w czasie kompilacji.  
  
 Proste typy mogą być inicjowane za pomocą literałów ciągów. Na przykład, "A" jest literał o typie `char` i 2001 jest literał o typie `int`.  
  
## <a name="initializing-value-types"></a>Inicjowanie typów wartości  
 Zmienne lokalne w języku C# muszą zostać zainicjowane, przed są one używane. Na przykład może zadeklarować zmienną lokalną bez inicjowania, jak w poniższym przykładzie:  
  
```csharp  
int myInt;  
```  
  
 Nie można użyć go, przed jej inicjalizację. Można zainicjować za pomocą następującej instrukcji:  
  
```csharp  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 Ta instrukcja jest równoważna następującej instrukcji:  
  
```csharp  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 Można oczywiście masz deklaracji i inicjowania w tej samej instrukcji, co pokazano w następujących przykładach:  
  
```csharp  
int myInt = new int();  
```  
  
 — lub —  
  
```csharp  
int myInt = 0;  
```  
  
 Za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) operator wywołuje domyślnego konstruktora określonego typu i przypisuje wartość domyślną do zmiennej. W powyższym przykładzie konstruktora domyślnego przypisaną wartość `0` do `myInt`. Aby uzyskać więcej informacji na temat wartości przypisane przez wywołanie metody konstruktory domyślne zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 W przypadku typów zdefiniowanych przez użytkownika, należy użyć [nowe](../../../csharp/language-reference/keywords/new.md) do wywołania konstruktora domyślnego. Na przykład następująca instrukcja wywołuje domyślny konstruktor obiektu `Point` struktury:  
  
```csharp  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 Po tym wywołaniu struktury uznaje się być zdecydowanie przypisywany; oznacza to, że wszystkie jego elementy członkowskie są inicjowane do wartości domyślnych.  
  
 Aby uzyskać więcej informacji na temat operatora new zobacz [nowe](../../../csharp/language-reference/keywords/new.md).  
  
 Aby dowiedzieć się, jak formatowanie danych wyjściowych typów liczbowych, zobacz [formatowanie tabeli wyników liczbowych](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [Tabele odwołań dla typów](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy dopuszczające wartości zerowe](../../programming-guide/nullable-types/index.md)  
