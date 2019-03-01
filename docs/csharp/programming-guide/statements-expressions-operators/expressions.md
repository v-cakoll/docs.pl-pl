---
title: Wyrażenia - C# przewodnik programowania
ms.custom: seodec18
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: c8856dfd1c6c8e35399c20b630c0d44493e42b6a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972199"
---
# <a name="expressions-c-programming-guide"></a>Wyrażenia (Przewodnik programowania w języku C#)
*Wyrażenie* jest sekwencją jednego lub większej liczbie operandów i zero lub więcej operatorów, które mogą być obliczane do pojedynczej wartości, obiektu, metody lub przestrzeni nazw. Wyrażenia może składać się z wartością literału, wywołanie metody, operatora i jego operandy lub *prostej nazwie*. Proste nazwy mogą być nazwa zmiennej, składowej typu, parametru metody, przestrzeń nazw lub typu.  
  
 Wyrażenia można używać operatorów, które z kolei inne wyrażenia używane jako parametry lub metoda wywołuje metodę, której parametry są z kolei inne wywołania metody, więc wyrażenia do zakresu od prostego do bardzo złożone. Poniżej przedstawiono dwa przykłady wyrażeń:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));
   
System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>Wyrażenie wartości  
 W większości w sytuacjach, w których wyrażenia są używane, na przykład w instrukcji lub parametrach metody wyrażenia powinien ocenić na wartość. Jeśli x i y są liczbami całkowitymi, wyrażenie `x + y` daje w wyniku wartość liczbową. Wyrażenie `new MyClass()` ocenia na odwołanie do nowego wystąpienia `MyClass` klasy. Wyrażenie `myClass.ToString()` ocenia na ciąg, ponieważ jest to typ zwracany metody. Jednak mimo że nazwa przestrzeni nazw jest klasyfikowana jako wyrażenia, nie można rozpoznać wartości i w związku z tym nigdy nie może być ostateczny wynik dowolne wyrażenie. Nie można przekazać nazwę przestrzeni nazw do parametru metody, lub używać go w nowe wyrażenie lub przypisać ją do zmiennej. Można używać tylko ją jako wyrażenie podrzędnych w dłuższym wyrażeniu. To samo dotyczy typów (w odróżnieniu od <xref:System.Type?displayProperty=nameWithType> obiektów), nazwy grupy metod (jak różniący się od określonej metody) oraz zdarzenia [Dodaj](../../../csharp/language-reference/keywords/add.md) i [Usuń](../../../csharp/language-reference/keywords/remove.md) metod dostępu.  
  
 Każda wartość ma skojarzony typ. Na przykład jeśli x i y są obie zmienne typu `int`, wartość wyrażenia `x + y` jako również wpisana `int`. Jeśli wartość jest przypisywana do zmiennej innego typu lub x i y są różnych typów, reguły konwersji typów są stosowane. Aby uzyskać więcej informacji na temat działania takich konwersji, zobacz [rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Przepełnienia  
 Wyrażeń liczbowych może powodować przepełnienia, jeśli wartość jest większa niż maksymalna wartość typu wartości. Aby uzyskać więcej informacji, zobacz [zaznaczone i niezaznaczone](../../../csharp/language-reference/keywords/checked-and-unchecked.md) i [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="operator-precedence-and-associativity"></a>Pierwszeństwo i kojarzenie operatorów  
 Sposób, w którym jest obliczane wyrażenie jest regulowane przez reguły pierwszeństwa łączność i operatora. Aby uzyskać więcej informacji, zobacz [operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md).  
  
 Większość wyrażeń, z wyjątkiem wyrażenia przypisania i wyrażenia wywołania metody, musi być osadzony w instrukcji. Aby uzyskać więcej informacji, zobacz [instrukcji](../../../csharp/programming-guide/statements-expressions-operators/statements.md).  
  
## <a name="literals-and-simple-names"></a>Literały i proste nazwy  
 Najprostsza dwa rodzaje wyrażeń są literały i proste nazwy. Literał jest wartością stałą, która nie ma nazwy. Na przykład w poniższym przykładzie kodu zarówno `5` i `"Hello World"` wartości literału:  
  
 [!code-csharp[csProgGuideStatements#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#2)]  
  
 Aby uzyskać więcej informacji na temat literały, zobacz [typy](../../../csharp/language-reference/keywords/types.md).  
  
 W poprzednim przykładzie zarówno `i` i `s` to proste nazwy, określających zmiennych lokalnych. Gdy te zmienne są używane w wyrażeniu, nazwa zmiennej daje w wyniku wartość, która jest obecnie przechowywanych w zmiennej lokalizacji w pamięci. Jest to pokazane w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#3)]  
## <a name="invocation-expressions"></a>Wyrażenia wywołania  
 W poniższym przykładzie kodu, wywołanie `DoWork` to wyrażenie wywołania.  
  
```csharp
DoWork();  
```  
  
 Wywołanie metody wymaga nazwę metody, jako nazwę, jak w poprzednim przykładzie, albo w wyniku innego wyrażenia, a następnie nawias oraz wszelkie parametry metody. Aby uzyskać więcej informacji, zobacz [metody](../../../csharp/programming-guide/classes-and-structs/methods.md). Wywołanie delegata używa nazwy parametrów delegata i metody w nawiasach. Aby uzyskać więcej informacji, zobacz [delegatów](../../../csharp/programming-guide/delegates/index.md). Wywołania metod i delegowanie wywołań zwrócić wartość zwracaną metody, jeśli metoda zwraca wartość. Nie można użyć metody, które zwracają void zamiast wartości w wyrażeniu.  

## <a name="query-expressions"></a>Wyrażenia zapytań  
 Ogólnie rzecz biorąc te same reguły dotyczące wyrażeń dotyczą wyrażenia zapytania. Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 Wyrażenia lambda reprezentują "wbudowane metody", do żadnej nazwy, które mają wejściowy parametry i użycie wielu instrukcji. Służą one często w składniku LINQ do argumenty przekazywane do metody. Wyrażenia lambda są kompilowane do delegatów lub drzew wyrażeń w zależności od kontekstu, w którym są używane. Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="expression-trees"></a>Drzewa wyrażeń

Drzewa wyrażeń Włącz wyrażenia może być reprezentowana jako struktur danych. Służą one często przez dostawców LINQ do translacji wyrażenia zapytań do kodu, który ma znaczenie w innym kontekście, takich jak bazy danych SQL. Aby uzyskać więcej informacji, zobacz [drzew wyrażeń (C#)](../concepts/expression-trees/index.md).
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażenia

C# obsługuje *elementy członkowskie z wyrażeniem*, które umożliwiają określanie definicji treści zwięzłe wyrażenia dla metod, konstruktory, finalizatorów, właściwości i indeksatorów. Aby uzyskać więcej informacji, zobacz [elementy członkowskie z wyrażeniem](expression-bodied-members.md).

## <a name="remarks"></a>Uwagi  
 Zawsze, gdy zmienna, właściwości obiektu lub obiektu dostęp indeksatora jest identyfikowany przy użyciu wyrażenia, wartość tego elementu jest używana jako wartość wyrażenia. Wyrażenie można umieścić dowolne miejsce w języku C# gdy wartość lub obiektu jest wymagany, tak długo, jak ostatecznie wynikiem wyrażenia jest na wymagany typ.  

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Delegaty](../../../csharp/programming-guide/delegates/index.md)
- [Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)
- [Typy](../../../csharp/programming-guide/types/index.md)
- [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
