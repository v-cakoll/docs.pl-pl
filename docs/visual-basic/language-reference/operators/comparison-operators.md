---
title: Operatory porównania (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 4e37f55b4c873c3dbea22a8edf0e5e2b58824720
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="comparison-operators-visual-basic"></a>Operatory porównania (Visual Basic)
Poniżej przedstawiono operatory porównania zdefiniowany w języku Visual Basic.  
  
 `<` Operator  
  
 `<=` Operator  
  
 `>` Operator  
  
 `>=` Operator  
  
 `=` Operator  
  
 `<>` Operator  
  
 [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like, operator](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 Te operatory porównania dwóch wyrażeń w celu ustalenia, czy są równe, a jeśli nie, jak różnią się one. `Is`, `IsNot`, i `Like` opisano szczegółowo na oddzielnych stronach pomocy. Operatory relacyjne opisano szczegółowo na tej stronie.  
  
## <a name="syntax"></a>Składnia  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. A `Boolean` wartość reprezentująca wynik porównania.  
  
 `expression`  
 Wymagana. Dowolne wyrażenie.  
  
 `comparisonoperator`  
 Wymagana. Dowolny relacyjny operator porównania.  
  
 `object1`, `object2`  
 Wymagana. Wszystkie nazwy obiektu odwołania.  
  
 `string`  
 Wymagana. Wszelkie `String` wyrażenia.  
  
 `pattern`  
 Wymagana. Wszelkie `String` wyrażenie lub zakres znaków.  
  
## <a name="remarks"></a>Uwagi  
 Poniższa tabela zawiera listę operatory relacyjne i warunków, które określają, czy `result` jest `True` lub `False`.  
  
|Operator|`True` Jeśli|`False` Jeśli|  
|--------------|---------------|----------------|  
|`<` (Poniżej)|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=` (Mniejsze niż lub równe)|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>` (Więcej niż)|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=` (Większe niż lub równe)|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=` (Równe)|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>` (Nie ma wartości)|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  [= — Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) jest również używany jako operator przypisania.  
  
 `Is` Operatora, `IsNot` , operator i `Like` operator ma funkcje określonych porównanie, które różnią się od operatorów w powyższej tabeli.  
  
## <a name="comparing-numbers"></a>Porównanie liczby  
 Jeśli wyrażenie typu do porównania `Single` do jednego z typów `Double`, `Single` wyrażenie jest konwertowana na `Double`. To zachowanie jest przeciwnej zachowanie w języku Visual Basic 6.  
  
 Podobnie, jeśli do porównania wyrażenia typu `Decimal` do wyrażenia typu `Single` lub `Double`, `Decimal` wyrażenie jest konwertowana na `Single` lub `Double`. Aby uzyskać `Decimal` wyrażenia, każda wartość ułamkową mniej niż 28 1E mogą zostać utracone. Takie utraty wartość ułamkową może spowodować dwie wartości porównać jako równe, jeśli nie są one. Z tego powodu należy zajmie się przy użyciu równości (`=`) do porównania dwóch zmienne zmiennoprzecinkowe. Jest bezpieczniejsze sprawdzić, czy wartość bezwzględna różnicy między dwiema liczbami jest mniejsza niż małych dopuszczalnych granicach.  
  
### <a name="floating-point-imprecision"></a>Zmiennoprzecinkowe błędu  
 Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne reprezentacji w pamięci. Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md). Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="comparing-strings"></a>Porównywanie ciągów  
 Podczas porównywania ciągów wyrażenia parametrów są oceniane w oparciu ich kolejność sortowania alfabetyczne, zależy od `Option Compare` ustawienie.  
  
 `Option Compare Binary` podstawy ciągu porównania na kolejność sortowania, pochodzi z wewnętrznego reprezentacje binarne znaków. Kolejność sortowania jest określany za pomocą stron kodowych. W poniższym przykładzie przedstawiono typowe binarny porządek sortowania.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` podstawy ciągu porównania w kolejności sortowania bez uwzględniania wielkości liter, tekstowych określają ustawienia regionalne aplikacji. Podczas ustawiania `Option Compare Text` i sortowania znaków w poprzednim przykładzie, mają zastosowanie następujące tekstowy porządek sortowania:  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>Zależność od ustawień regionalnych  
 Podczas ustawiania `Option Compare Text`, wynik porównania ciągów może być zależny od ustawień regionalnych, w którym aplikacja jest uruchomiona. Dwa znaki może porównać jako równe co ustawień regionalnych, ale nie w innym. Jeśli używasz porównania ciągów podjęcie istotnych decyzji, takich jak zaakceptowanie próba logowania, należy alert do wrażliwości ustawień regionalnych. Należy wziąć pod uwagę ustawienia `Option Compare Binary` lub wywoływania <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, która uwzględnia ustawienia regionalne.  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>Programowanie Nietypowane przy użyciu operatorów relacyjnych porównania  
 Korzystanie z operatorów relacyjnych porównania z `Object` wyrażenia jest niedozwolone w obszarze `Option Strict On`. Gdy `Option Strict` jest `Off`oraz `expression1` lub `expression2` jest `Object` wyrażenia, typy środowiska wykonawczego określają, jak są one porównywane. W poniższej tabeli przedstawiono, jak są porównywane wyrażeń i wynik porównania, zależnie od typu środowiska uruchomieniowego argumenty operacji.  
  
|W przypadku argumentów operacji|Wynik porównania ma|  
|---------------------|-------------------|  
|Zarówno `String`|Aby posortować porównań opartych na ciąg sortowania właściwości.|  
|Zarówno liczbowe|Obiekty konwertowane na `Double`, porównanie liczbowe.|  
|Jeden numeryczne i jeden `String`|`String` Jest konwertowana na `Double` i wykonywane jest porównanie numeryczne. Jeśli `String` nie można przekonwertować na `Double`, <xref:System.InvalidCastException> jest generowany.|  
|Jedno lub obydwa są typy referencyjne innych niż `String`|<xref:System.InvalidCastException> Jest generowany.|  
  
 Traktuj porównanie liczbowe `Nothing` jako 0. Porównywanie ciągów Traktuj `Nothing` jako `""` (ciągiem pustym).  
  
## <a name="overloading"></a>Przeciążenie  
 Operatory relacyjne (`<`. `<=``>`, `>=`, `=`, `<>`) może być *przeciążony*, co oznacza, że klasy lub struktury można zmienić ich zachowania, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa żadnego z tych operatorów dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
 Zwróć uwagę, że [= — Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) może być przeciążona tylko jako operator porównania relacyjne, a nie jako operatora przypisania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono różnych zastosowań operatory porównania relacyjne, które umożliwia porównywanie wyrażeń. Operatory relacyjne porównania zwracać `Boolean` wynik, który reprezentuje czy podane wyrażenie daje w wyniku `True`. Po zastosowaniu `>` i `<` operatory ciągów, porównując przy użyciu normalnego alfabetycznie sortowania ciągi. To zamówienie mogą być zależne od ustawienia regionalne. Sortowanie jest rozróżniana wielkość liter i nie jest zależna od [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) ustawienie.  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 W powyższym przykładzie zwraca pierwszy porównanie `False` i zwracać pozostałych porównań `True`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.InvalidCastException>  
 [=, operator](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
