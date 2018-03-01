---
title: "Typy wartości (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 281b811f2a8a1f2c364405b563f9f103899b492c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-c-reference"></a>Typy wartości (odwołanie w C#)
Typy wartości obejmują dwie główne kategorie:  
  
-   [Struktury](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Wyliczenia](../../../csharp/language-reference/keywords/enum.md)  
  
 Struktury można podzielić na następujące kategorie:  
  
-   Typy liczbowe  
  
    -   [Typy całkowite](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [Typy zmiennoprzecinkowe](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [decimal](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [wartość logiczna](../../../csharp/language-reference/keywords/bool.md)  
  
-   Struktury zdefiniowane przez użytkownika.  
  
## <a name="main-features-of-value-types"></a>Główne funkcje typów wartości  
 Zmienne, które są oparte na typy wartości bezpośrednio zawierać wartości. Przypisywanie jedną wartość typu zmienną do innej kopii zawartych w niej wartości. To różni się od przypisywanie zmienne odwołujące się do typu, który kopiuje odwołanie do obiektu, ale nie samego obiektu.  
  
 Wszystkie typy wartości są pochodnymi niejawnie <xref:System.ValueType?displayProperty=nameWithType>.  
  
 W odróżnieniu od z typami odwołanie, nie może pochodzić nowy typ z typem wartości. Jednakże, takich jak typy referencyjne struktury mogą implementować interfejsów.  
  
 W przeciwieństwie do typów referencyjnych, typ wartości nie może zawierać `null` wartość. Jednak [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md) funkcji Zezwalaj dla typów wartości do przypisania do `null`.  
  
 Każdy typ wartości ma niejawne domyślnego konstruktora, który inicjuje wartością domyślną tego typu. Aby uzyskać informacje o wartościach domyślnych typów wartości, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="main-features-of-simple-types"></a>Główne funkcje typy proste  
 Wszystkie typy proste — te typy całkowite języka C# — są aliasów typów .NET Framework systemu. Na przykład [int](../../../csharp/language-reference/keywords/int.md) jest aliasem <xref:System.Int32?displayProperty=nameWithType>. Aby uzyskać pełną listę aliasów, zobacz [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md).  
  
 Wyrażenia stałe, którego argumenty operacji są wszystkich stałych typu prostego, są oceniane w czasie kompilacji.  
  
 Proste typy mogą być inicjowane przy użyciu literałów. Na przykład, "A" jest literałem typu `char` i 2001 jest literałem typu `int`.  
  
## <a name="initializing-value-types"></a>Inicjowanie typów wartości  
 Zmienne lokalne w języku C# muszą zostać zainicjowane, przed są one używane. Na przykład może zadeklarować zmiennej lokalnej bez inicjowania jak w poniższym przykładzie:  
  
```  
int myInt;  
```  
  
 Nie można używać go, zanim można go zainicjować. Można zainicjować za pomocą następujących instrukcji:  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 Ta instrukcja jest odpowiednikiem następująca instrukcja:  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 Deklaracji i inicjowania mogą oczywiście ma w tej samej instrukcji, na przykład:  
  
```  
int myInt = new int();  
```  
  
 — lub —  
  
```  
int myInt = 0;  
```  
  
 Przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) operator wywołuje domyślny konstruktor obiektu określonego typu i przypisuje wartość domyślną do zmiennej. W powyższym przykładzie konstruktora domyślnego przypisaną wartość `0` do `myInt`. Aby uzyskać więcej informacji na temat przypisanych przez wywołanie metody konstruktory domyślne wartości, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Typy danych zdefiniowane przez użytkownika, za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) do wywołania konstruktora domyślnego. Na przykład następująca instrukcja wywołuje domyślny konstruktor obiektu `Point` struktury:  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 Po tym wywołaniu struktury jest uznawany za można zdecydowanie przypisać; oznacza to, że wszyscy jej członkowie są inicjowane z wartościami domyślnymi.  
  
 Aby uzyskać więcej informacji na temat operatora new, zobacz [nowe](../../../csharp/language-reference/keywords/new.md).  
  
 Aby dowiedzieć się, jak formatowanie danych wyjściowych typy liczbowe, zobacz [formatowanie tabeli wyników liczbowych](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [Tabele odwołań dla typów](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)
