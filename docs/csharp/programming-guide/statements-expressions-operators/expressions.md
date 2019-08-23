---
title: Wyrażenia — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 1a0e94f40a9dc861b32e6a1c12935faadda9921b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921808"
---
# <a name="expressions-c-programming-guide"></a>Wyrażenia (Przewodnik programowania w języku C#)

*Wyrażenie* jest sekwencją co najmniej jednego operandu i zero lub więcej [operatorów](../../language-reference/operators/index.md) , które mogą być oceniane do pojedynczej wartości, obiektu, metody lub przestrzeni nazw. Wyrażenia mogą składać się z wartości literału, wywołania metody, operatora i jego operandów lub *nazwy prostej*. Proste nazwy mogą być nazwą zmiennej, składową, parametrem metody, przestrzenią nazw lub typem.  
  
 Wyrażenia mogą używać operatorów, które z kolei używają innych wyrażeń jako parametrów lub wywołań metod, których parametry są z kolei inne wywołania metod, dlatego wyrażenia mogą być różne od prostych do bardzo złożonych. Poniżej przedstawiono dwa przykłady wyrażeń:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));

System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>Wartości wyrażeń

 W większości kontekstów, w których są używane wyrażenia, na przykład w instrukcjach lub parametrach metod, oczekiwane jest wyrażenie do obliczenia wartości. Jeśli x i y są liczbami całkowitymi, `x + y` wyrażenie daje w wyniku wartość liczbową. Wyrażenie `new MyClass()` oblicza odwołanie do nowego wystąpienia `MyClass` klasy. Wyrażenie `myClass.ToString()` daje w wyniku ciąg, ponieważ jest typem zwracanym metody. Mimo że nazwa przestrzeni nazw jest sklasyfikowana jako wyrażenie, nie jest ona szacowana jako wartość i w związku z tym nie może być ostatnim wynikiem żadnego wyrażenia. Nie można przekazać nazwy przestrzeni nazw do parametru metody lub użyć jej w nowym wyrażeniu lub przypisać do zmiennej. Można go użyć tylko jako wyrażenia podrzędnego w większym wyrażeniu. To samo jest prawdziwe dla typów (odrębnie od <xref:System.Type?displayProperty=nameWithType> obiektów), nazw grup metod (jako odrębnych od określonych metod), a także do [dodawania](../../language-reference/keywords/add.md) i [usuwania](../../language-reference/keywords/remove.md) zdarzeń.  
  
 Każda wartość ma skojarzony typ. Na przykład jeśli x i y są zmienne typu `int`, wartość wyrażenia `x + y` jest również wpisywana jako `int`. Jeśli wartość jest przypisana do zmiennej innego typu lub jeśli x i y są różne typy, stosowane są reguły konwersji typów. Aby uzyskać więcej informacji na temat tego, jak te konwersje działają, zobacz [rzutowanie i konwersje typów](../types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Przepełnienia

 Wyrażenia liczbowe mogą spowodować przepełnienie, jeśli wartość jest większa niż wartość maksymalna typu wartości. Aby uzyskać więcej informacji, Zobacz tabele [Checked i](../../language-reference/keywords/checked-and-unchecked.md) unchecked oraz [jawne konwersje liczbowe](../../language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="operator-precedence-and-associativity"></a>Pierwszeństwo operatorów i łączność

 Sposób, w jaki wyrażenie jest oceniane, podlega regułom łączność i pierwszeństwa operatorów. Aby uzyskać więcej informacji, zobacz [Operatory](../../language-reference/operators/index.md).  
  
 Większość wyrażeń, z wyjątkiem wyrażeń przypisania i wyrażenia wywołania metody, musi być osadzona w instrukcji. Aby uzyskać więcej informacji, zobacz [instrukcje](./statements.md).  
  
## <a name="literals-and-simple-names"></a>Literały i nazwy proste

 Dwa najprostsze typy wyrażeń to literały i proste nazwy. Literał jest wartością stałą, która nie ma nazwy. Na przykład, w poniższym przykładzie kodu, obie `5` i `"Hello World"` są wartościami literału:  
  
 [!code-csharp[csProgGuideStatements#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#2)]  
  
 Aby uzyskać więcej informacji na temat literałów, zobacz [typy](../../language-reference/keywords/types.md).  
  
 W poprzednim przykładzie obie `i` i `s` są prostymi nazwami, które identyfikują zmienne lokalne. Gdy zmienne są używane w wyrażeniu, nazwa zmiennej jest obliczana do wartości, która jest aktualnie przechowywana w lokalizacji zmiennej w pamięci. Jest to pokazane w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#3)]

## <a name="invocation-expressions"></a>Wyrażenia wywołania

 W poniższym przykładzie kodu wywołanie `DoWork` jest wyrażeniem wywołania.  
  
```csharp
DoWork();  
```  
  
 Wywołanie metody wymaga nazwy metody, jako nazwy, jak w poprzednim przykładzie, lub jako wynik innego wyrażenia, po którym następuje nawias i wszystkie parametry metody. Aby uzyskać więcej informacji, zobacz [metody](../classes-and-structs/methods.md). Wywołanie delegata używa nazwy delegata i parametrów metody w nawiasie. Aby uzyskać więcej informacji, [](../delegates/index.md)Zobacz delegats. Wywołania metod i delegatów wywołań są oceniane do wartości zwracanej metody, jeśli metoda zwraca wartość. Metody zwracające typ void nie mogą być używane zamiast wartości w wyrażeniu.  

## <a name="query-expressions"></a>Wyrażenia zapytań

 Te same reguły dla wyrażeń ogólnych dotyczą wyrażeń zapytań. Aby uzyskać więcej informacji, zobacz [LINQ](../../linq/index.md).  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda

 Wyrażenia lambda reprezentują "metody wbudowane", które nie mają nazwy, ale mogą zawierać parametry wejściowe i wiele instrukcji. Są one używane w szerokim stopniu w LINQ do przekazywania argumentów do metod. Wyrażenia lambda są kompilowane do delegatów lub drzew wyrażeń w zależności od kontekstu, w którym są używane. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](lambda-expressions.md).  
  
## <a name="expression-trees"></a>Drzewa wyrażeń

Drzewa wyrażeń umożliwiają wyrażenia, które mają być reprezentowane jako struktury danych. Są one szeroko używane przez dostawców LINQ do translacji wyrażeń zapytania do kodu, który jest zrozumiały w innym kontekście, na przykład w bazie danych SQL. Aby uzyskać więcej informacji, zobacz [drzewa wyrażeńC#()](../concepts/expression-trees/index.md).
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażenia

C#obsługuje składowe w postaci *wyrażeń*, które umożliwiają dostarczenie zwięzłej definicji treści wyrażenia dla metod, konstruktorów, finalizatorów, właściwości i indeksatorów. Aby uzyskać więcej informacji, zobacz [elementy członkowskie z wyrażeniami](expression-bodied-members.md).

## <a name="remarks"></a>Uwagi

 Za każdym razem, gdy zmienna, właściwość obiektu lub dostęp indeksatora obiektu jest identyfikowany na podstawie wyrażenia, wartość tego elementu jest używana jako wartość wyrażenia. Wyrażenie można umieścić w dowolnym miejscu, C# w którym jest wymagana wartość lub obiekt, tak długo, jak wyrażenie ostatecznie zwraca wymagany typ.  

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [](~/_csharplang/spec/expressions.md) sekcję Expressions w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Operatory](../../language-reference/operators/index.md)
- [Metody](../classes-and-structs/methods.md)
- [Delegaty](../delegates/index.md)
- [Typy](../types/index.md)
- [LINQ](../../linq/index.md)
