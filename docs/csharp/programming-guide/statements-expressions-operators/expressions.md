---
title: Wyrażenia — przewodnik programowania Języka C#
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 4bbee8f15c2591e8b172df9a6759449d48697804
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75699096"
---
# <a name="expressions-c-programming-guide"></a>Wyrażenia (Przewodnik programowania w języku C#)

*Wyrażenie* jest sekwencją jednego lub więcej operandów i zero lub więcej [operatorów,](../../language-reference/operators/index.md) które mogą być oceniane do pojedynczej wartości, obiektu, metody lub przestrzeni nazw. Wyrażenia mogą składać się z wartości literału, wywołania metody, operatora i jego argumentów lub *prostej nazwy.* Proste nazwy mogą być nazwą zmiennej, elementu członkowskiego typu, parametru metody, obszaru nazw lub typu.  
  
 Wyrażenia można używać operatorów, które z kolei używają innych wyrażeń jako parametry lub wywołania metody, których parametry są z kolei inne wywołania metody, więc wyrażenia mogą wahać się od prostych do bardzo złożonych. Oto dwa przykłady wyrażeń:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));

System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>Wartości wyrażenia

 W większości kontekstów, w których używane są wyrażenia, na przykład w instrukcjach lub parametrach metody, wyrażenie ma ocenić pewną wartość. Jeśli x i y są liczbami `x + y` całkowitymi, wyrażenie oblicza wartość liczbową. Wyrażenie `new MyClass()` oblicza odwołanie do nowego wystąpienia `MyClass` klasy. Wyrażenie `myClass.ToString()` oblicza ciąg, ponieważ jest to typ zwracany metody. Jednak mimo że nazwa obszaru nazw jest klasyfikowany jako wyrażenie, nie jest oceniana do wartości i dlatego nigdy nie może być wynikiem końcowym dowolnego wyrażenia. Nie można przekazać nazwy obszaru nazw do parametru metody ani użyć jej w nowym wyrażeniu ani przypisać jej do zmiennej. Można go używać tylko jako wyrażenia podrzędnego w wyrażeniu większym. To samo dotyczy typów (w <xref:System.Type?displayProperty=nameWithType> odróżnieniu od obiektów), nazw grup metod (w odróżnieniu od określonych metod) i [dodania](../../language-reference/keywords/add.md) i [usuwania](../../language-reference/keywords/remove.md) akcesorów.  
  
 Każda wartość ma skojarzony typ. Na przykład jeśli x i y są `int`obiema zmiennymi `x + y` typu, wartość `int`wyrażenia jest również wpisana jako . Jeśli wartość jest przypisana do zmiennej innego typu lub jeśli x i y są różnymi typami, stosowane są reguły konwersji typu. Aby uzyskać więcej informacji na temat działania takich konwersji, zobacz [Konwersje rzutowania i typu](../types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Przepełnienie

 Wyrażenia liczbowe mogą powodować przepełnienie, jeśli wartość jest większa niż maksymalna wartość typu wartości. Aby uzyskać więcej informacji, zobacz [Sprawdzone i niezaznaczone](../../language-reference/keywords/checked-and-unchecked.md) oraz [jawne konwersje liczbowe](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) w artykule [Wbudowane konwersje liczbowe.](../../language-reference/builtin-types/numeric-conversions.md)
  
## <a name="operator-precedence-and-associativity"></a>Pierwszeństwo operatora i zespolenie

 Sposób, w jaki wyrażenie jest oceniane jest regulowane przez zasady kojarzenia i pierwszeństwo operatora. Aby uzyskać więcej informacji, zobacz [Operatory](../../language-reference/operators/index.md).  
  
 Większość wyrażeń, z wyjątkiem wyrażeń przypisania i wyrażeń wywołania metody, musi być osadzona w instrukcji. Aby uzyskać więcej informacji, zobacz [Oświadczenia](./statements.md).  
  
## <a name="literals-and-simple-names"></a>Literały i proste nazwy

 Dwa najprostsze typy wyrażeń są literały i proste nazwy. Literału jest stałą wartością, która nie ma nazwy. Na przykład w poniższym przykładzie `5` `"Hello World"` kodu oba i są wartościami literału:  
  
 [!code-csharp[csProgGuideStatements#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#2)]  
  
 Aby uzyskać więcej informacji na temat literału, zobacz [Typy](/dotnet/csharp/language-reference/keywords).  
  
 W poprzednim przykładzie oba `i` `s` i są proste nazwy, które identyfikują zmienne lokalne. Gdy te zmienne są używane w wyrażeniu, nazwa zmiennej jest obliczana na wartość, która jest aktualnie przechowywana w lokalizacji zmiennej w pamięci. Jest to pokazane w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#3)]

## <a name="invocation-expressions"></a>Wyrażenia wywołania

 W poniższym przykładzie kodu `DoWork` wywołanie jest wyrażenie minacji.  
  
```csharp
DoWork();  
```  
  
 Wywołanie metody wymaga nazwy metody, jako nazwę, jak w poprzednim przykładzie, lub w wyniku innego wyrażenia, a następnie nawiasy i wszelkie parametry metody. Aby uzyskać więcej informacji, zobacz [Metody](../classes-and-structs/methods.md). Wywołanie delegata używa nazwy delegata i parametrów metody w nawiasie. Aby uzyskać więcej informacji, zobacz [Delegatów](../delegates/index.md). Wywołania metody i delegować wywołania ocenić wartość zwracaną metody, jeśli metoda zwraca wartość. Metody, które zwracają void nie można użyć w miejsce wartości w wyrażeniu.  

## <a name="query-expressions"></a>Wyrażenia kwerendy

 Te same reguły dla wyrażeń w ogóle stosuje się do wyrażeń kwerendy. Aby uzyskać więcej informacji, zobacz [LINQ](../../linq/index.md).  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda

 Wyrażenia Lambda reprezentują "metody inline", które nie mają nazwy, ale mogą mieć parametry wejściowe i wiele instrukcji. Są one szeroko stosowane w LINQ do przekazywania argumentów do metod. Wyrażenia Lambda są kompilowane do delegatów lub drzewa wyrażeń w zależności od kontekstu, w którym są używane. Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda](lambda-expressions.md).  
  
## <a name="expression-trees"></a>Drzewa wyrażeń

Drzewa wyrażeń umożliwiają reprezentację wyrażeń jako struktury danych. Są one szeroko używane przez dostawców LINQ do tłumaczenia wyrażeń zapytań na kod, który ma znaczenie w innym kontekście, takich jak baza danych SQL. Aby uzyskać więcej informacji, zobacz [Drzewa wyrażeń (C#)](../concepts/expression-trees/index.md).
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażeń

C# obsługuje *elementy członkowskie zabudowane wyrażeniem*, które umożliwiają dostarczanie definicji treści zwięzłe wyrażenie dla metod, konstruktorów, finalizatorów, właściwości i indeksatorów. Aby uzyskać więcej informacji, zobacz [Elementy członkowskie zabudowane wyrażeniem](expression-bodied-members.md).

## <a name="remarks"></a>Uwagi

 Za każdym razem, gdy zmienna, właściwość obiektu lub dostęp do indeksatora obiektów są identyfikowane z wyrażenia, wartość tego elementu jest używana jako wartość wyrażenia. Wyrażenie można umieścić w dowolnym miejscu w języku C#, gdzie wymagana jest wartość lub obiekt, tak długo, jak wyrażenie ostatecznie ocenia wymagany typ.  

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję Wyrażenia](~/_csharplang/spec/expressions.md) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Operatory](../../language-reference/operators/index.md)
- [Metody](../classes-and-structs/methods.md)
- [Delegaty](../delegates/index.md)
- [Typy](../types/index.md)
- [Linq](../../linq/index.md)
