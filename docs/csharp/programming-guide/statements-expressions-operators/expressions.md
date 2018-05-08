---
title: Wyrażenia (Przewodnik programowania w języku C#)
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 830c68e6857e72fe19099753ba57a7e22491af2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expressions-c-programming-guide"></a>Wyrażenia (Przewodnik programowania w języku C#)
*Wyrażenie* Sekwencja zero lub więcej operatorów, które może przyjąć pojedynczą wartość, obiekt, metodę lub przestrzeń nazw i jeden lub więcej argumentów operacji. Wartość literału, wywołania metody, operator i argumentów, może zawierać wyrażenia lub *prosta nazwa*. Proste nazwy mogą być nazwę zmiennej, członka typu, parametru metody, przestrzeni nazw lub typu.  
  
 Wyrażenia można używać operatorów, które z kolei inne wyrażenia używane jako parametry lub wywołania metody, której parametry są z kolei inne wywołania metody, więc wyrażenia mogą należeć do zakresu od prostego do bardzo złożonych. Poniżej przedstawiono dwa przykłady wyrażeń:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));
   
System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>Wyrażenie wartości  
 W większości w sytuacjach, w których są używane wyrażenia, na przykład w instrukcji lub parametry metody wyrażenia powinien zwrócić wartości. Jeśli x i y są liczbami całkowitymi, wyrażenie `x + y` wynikiem jest wartość liczbowa. Wyrażenie `new MyClass()` wynikiem obliczenia jest odwołanie do nowego wystąpienia `MyClass` obiektu. Wyrażenie `myClass.ToString()` ocenia na ciąg, ponieważ jest to typ zwracany metody. Jednak mimo że nazwa przestrzeni nazw jest sklasyfikowany jako wyrażenie, nie zwraca wartości i dlatego nigdy nie może mieć końcowego wyniku dowolne wyrażenie. Nie można przekazać nazwę przestrzeni nazw do parametru metody, lub użyć go w nowym wyrażeniu lub przypisać go do zmiennej. Można używać tylko go jako wyrażenia podrzędnego w wyrażeniu większy. To samo dotyczy dla typów (w odróżnieniu od <xref:System.Type?displayProperty=nameWithType> obiektów), nazwy grup — metoda (od konkretnych metod) i zdarzenia [dodać](../../../csharp/language-reference/keywords/add.md) i [Usuń](../../../csharp/language-reference/keywords/remove.md) metody dostępu.  
  
 Każda wartość ma skojarzonego typu. Na przykład jeśli x i y są obie zmienne typu `int`, wartość wyrażenia `x + y` jest również typu `int`. Jeśli wartość jest przypisany do zmiennej innego typu albo x i y są różnych typów, stosowane są reguły konwersji typu. Aby uzyskać więcej informacji na temat działania takich konwersje zobacz [rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Przepełnienia  
 Wyrażenia liczbowe może powodować przepełnienia, jeśli wartość jest większa niż wartość maksymalna wartość typu. Aby uzyskać więcej informacji, zobacz [zaznaczony i niezaznaczony](../../../csharp/language-reference/keywords/checked-and-unchecked.md) i [jawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="operator-precedence-and-associativity"></a>Kolejność wykonywania działań i łączność  
 Sposób, w jakiej są oceniane wyrażenia podlega reguły pierwszeństwa łączność i operatora. Aby uzyskać więcej informacji, zobacz [operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md).  
  
 Większość wyrażenia, z wyjątkiem wyrażeń przypisania i wyrażenia wywołania metody, musi być osadzony w instrukcji. Aby uzyskać więcej informacji, zobacz [instrukcje](../../../csharp/programming-guide/statements-expressions-operators/statements.md).  
  
## <a name="literals-and-simple-names"></a>Literały i proste nazwy  
 Najprostsza dwa rodzaje wyrażeń są literały i proste nazwy. Literał jest wartością stałą, który nie ma nazwy. Na przykład w poniższym przykładzie kodu zarówno `5` i `"Hello World"` są wartości literałów:  
  
 [!code-csharp[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_1.cs)]  
  
 Aby uzyskać więcej informacji na literały, zobacz [typów](../../../csharp/language-reference/keywords/types.md).  
  
 W powyższym przykładzie zarówno `i` i `s` są proste nazwy, które identyfikują zmiennych lokalnych. W przypadku używania tych zmiennych w wyrażeniu nazwę zmiennej daje w wyniku wartość, która obecnie jest przechowywane w zmiennej lokalizacji w pamięci. Przedstawiono to w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_2.cs)]  
## <a name="invocation-expressions"></a>Wyrażenia wywołania  
 W poniższym przykładzie, wywołanie `DoWork` wyrażenie wywołania.  
  
```csharp
DoWork();  
```  
  
 Wywołanie metody wymaga nazwę metody, jak nazwa, co w poprzednim przykładzie lub w wyniku innego wyrażenia, następuje nawiasy i wszelkie parametry metody. Aby uzyskać więcej informacji, zobacz [metody](../../../csharp/programming-guide/classes-and-structs/methods.md). Wywołanie delegata używa nazwy parametrów delegata i metody w nawiasach. Aby uzyskać więcej informacji, zobacz [delegatów](../../../csharp/programming-guide/delegates/index.md). Wywołań metod i delegowanie wywołań zwrócić wartość zwracaną przez metodę, jeśli metoda zwróci wartość. Zamiast wartości w wyrażeniach nie można użyć metody zwracające typ void.  

## <a name="query-expressions"></a>Wyrażenia zapytań  
 Wyrażenia te same zasady dotyczą ogólnie wyrażenia zapytania. Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 Wyrażenia lambda reprezentują "wbudowanego metody", które nie mieć nazwy, ale może mieć wejściowych parametry i użycie wielu instrukcji. Są one używane często w składniku LINQ Aby przekazać argumenty do metod. Wyrażenia lambda są kompilowane delegatów lub drzew wyrażeń w zależności od kontekstu, w którym są używane. Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="expression-trees"></a>Drzewa wyrażeń  
 Drzewa wyrażeń włączyć wyrażenia może być reprezentowana jako struktury danych. Są one używane często przez dostawców LINQ do tłumaczenia wyrażenia zapytania do kodu, który jest przydatny w innym kontekście, takie jak bazy danych SQL. Aby uzyskać więcej informacji, zobacz [drzew wyrażeń](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
## <a name="expression-body-definitions"></a>Definicje treść wyrażenia

C# obsługuje *zabudowanych wyrażenia elementów członkowskich*, co pozwala użytkownikowi umożliwiają określanie wartości wyrażenia zwięzły definicji treści metody, konstruktorów finalizatory, właściwości i indeksatorów. Aby uzyskać więcej informacji, zobacz [zabudowanych wyrażenia elementów członkowskich](expression-bodied-members.md).

## <a name="remarks"></a>Uwagi  
 Zawsze, gdy zmienna, właściwość obiektu lub dostępu do obiektów indeksator zostanie zidentyfikowana z wyrażenia, wartość tego elementu jest używana jako wartość wyrażenia. Wyrażenie można umieszczać w dowolnym w języku C# gdzie wartość lub obiektu jest wymagane, tak długo, jak ostatecznie wyrażenie ma wymaganego typu.  

## <a name="see-also"></a>Zobacz także  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Delegaci](../../../csharp/programming-guide/delegates/index.md)  
 [Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
