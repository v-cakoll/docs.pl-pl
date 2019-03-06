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
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: c8835d1c42a02fa65e9acc9bd1c1f06fcfd4af02
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359825"
---
# <a name="comparison-operators-visual-basic"></a>Operatory porównania (Visual Basic)
Dostępne są następujące operatory porównania zdefiniowany w języku Visual Basic.  
  
 `<` Operator  
  
 `<=` Operator  
  
 `>` Operator  
  
 `>=` Operator  
  
 `=` Operator  
  
 `<>` Operator  
  
 [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like, operator](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 Te operatory porównania dwóch wyrażeń, aby określić, czy są równe, a jeśli nie, jak się różnią. `Is`, `IsNot`, i `Like` opisano szczegółowo w osobnych stron pomocy. Operatory relacyjne porównania są szczegółowo omówione w na tej stronie.  
  
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
 Wymagana. Wszystkie nazwy obiektów odwołania.  
  
 `string`  
 Wymagana. Wszelkie `String` wyrażenia.  
  
 `pattern`  
 Wymagana. Wszelkie `String` wyrażenie lub zakres znaków.  
  
## <a name="remarks"></a>Uwagi  
 Poniższa tabela zawiera listę operatorów relacyjnych porównania i warunki, które określają, czy `result` jest `True` lub `False`.  
  
|Operator|`True` Jeśli|`False` Jeśli|  
|--------------|---------------|----------------|  
|`<` (Mniejsze niż)|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=` (Mniejsze niż lub równe)|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>` (Większe niż)|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=` (Większe niż lub równe)|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=` (Równe)|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>` (Nie równa się)|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  [= — Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) jest również używany jako operator przypisania.  
  
 `Is` Operatora `IsNot` operatora i `Like` operator ma porównania określone funkcje, które różnią się od operatorów w powyższej tabeli.  
  
## <a name="comparing-numbers"></a>Porównanie liczb  
 Przy porównaniu wyrażenie typu `Single` do jednego typu `Double`, `Single` wyrażenie jest konwertowany na `Double`. To zachowanie jest przeciwnej zachowanie w języku Visual Basic 6.  
  
 Podobnie, jeśli do porównania wyrażenie typu `Decimal` do wyrażenia typu `Single` lub `Double`, `Decimal` wyrażenie jest konwertowany na `Single` lub `Double`. Aby uzyskać `Decimal` wyrażeń, dowolnej ułamkowe wartości mniejszej niż 1E-28 mogą zostać utracone. Takie utraty wartość ułamkowa może spowodować dwie wartości do porównania jako równe, jeśli nie są one. Z tego powodu należy zajmie się przy użyciu równości (`=`) do porównywania dwóch zmienne zmiennoprzecinkowe. Jest to bezpieczniejsze sprawdzić, czy wartość bezwzględną liczby różnicę między dwoma liczbami jest mniejsza niż małych akceptowane na uszkodzenia.  
  
### <a name="floating-point-imprecision"></a>Zmiennoprzecinkowe niedokładności  
 Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać o tym, że nie zawsze mają dokładne reprezentacji w pamięci. Może to spowodować nieoczekiwane wyniki z niektórych operacji, takich jak porównania wartości i [Mod — Operator](../../../visual-basic/language-reference/operators/mod-operator.md). Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="comparing-strings"></a>Porównywanie ciągów  
 Podczas porównywania ciągów wyrażenia ciągu są oceniane w oparciu o ich kolejność sortowania alfabetycznego, która zależy od `Option Compare` ustawienie.  
  
 `Option Compare Binary` podstawy ciąg porównania w porządku sortowania pochodną wewnętrzne binarne reprezentacje znaków. Kolejność sortowania jest określana przez stronę kodową. Poniższy przykład przedstawia typowy binarny porządek sortowania.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` podstawy ciąg porównania w kolejności sortowania bez uwzględniania wielkości liter, tekstowe, określane przez ustawienia regionalne aplikacji. Po ustawieniu `Option Compare Text` i sortowania znaków w poprzednim przykładzie, mają zastosowanie następujące tekstowy porządek sortowania:  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>Zależność od ustawień regionalnych  
 Po ustawieniu `Option Compare Text`, wynikiem porównania ciągów może zależeć od ustawień regionalnych, w którym aplikacja jest uruchomiona. Dwa znaki może być porównywany jako równe w jeden ustawień regionalnych, ale nie w innym. Jeśli używasz porównania ciągów podjęcie istotnych decyzji, np. Czy chcesz zaakceptować próba logowania, należy alertu wrażliwość na ustawienia regionalne. Rozważ ustawienie albo `Option Compare Binary` lub wywoływania <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, która uwzględnia ustawienia regionalne.  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>Programowanie nietypowane z operatorów porównania relacyjnych  
 Korzystanie z operatorów porównania relacyjnych z `Object` wyrażenia nie jest dozwolone w ramach `Option Strict On`. Gdy `Option Strict` jest `Off`oraz `expression1` lub `expression2` jest `Object` wyrażenia, typy środowiska wykonawczego określają, jak są porównywane. W poniższej tabeli przedstawiono, jak są porównywane wyrażeń i wynikiem porównania, w zależności od typu środowiska uruchomieniowego operandu.  
  
|W przypadku argumentów operacji|Porównanie jest|  
|---------------------|-------------------|  
|Oba `String`|Posortuj porównań opartych na właściwości sortowania ciągów.|  
|Zarówno liczbowe|Obiekty konwertowane `Double`, porównanie numeryczne.|  
|Jeden liczbowych i jeden `String`|`String` Jest konwertowana na `Double` i wykonywane jest porównanie numeryczne. Jeśli `String` nie można przekonwertować na `Double`, <xref:System.InvalidCastException> zgłaszany.|  
|Jeden lub oba są typami odwołań, innym niż `String`|<xref:System.InvalidCastException> Zgłaszany.|  
  
 Traktuj liczbowego porównania `Nothing` jako 0. Traktuj porównań ciągów `Nothing` jako `""` (ciąg pusty).  
  
## <a name="overloading"></a>Przeciążenie  
 Operatory relacyjne (`<`. `<=``>`, `>=`, `=`, `<>`) może być *przeciążone*, co oznacza, że klasa lub Struktura można ponownie zdefiniować ich zachowania, gdy argument operacji ma typ tej klasy lub struktury. Jeśli Twój kod wykorzystuje dowolne z tych operatorów dla klasy lub struktury, upewnij się, że należy zrozumieć zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
 Należy zauważyć, że [= — Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) mogą być przeciążone, tylko jako operator porównania relacyjnych, a nie jako operator przypisania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje różne przypadki użycia operatorów porównania relacyjnych, które umożliwia porównywanie wyrażeń. Operatory relacyjne porównania zwracają `Boolean` wynik, który reprezentuje informację określającą, czy podane wyrażenie daje w wyniku `True`. Po zastosowaniu `>` i `<` dokonywane jest porównanie operatorów na ciągi, przy użyciu normalnych alfabetycznej sortowania ciągów. To zamówienie mogą być zależne od ustawienia regionalne. Sortowanie jest rozróżniana wielkość liter lub nie jest zależny od [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) ustawienie.  
  
 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]  
  
 W powyższym przykładzie zwraca pierwszy porównania `False` i zwracają pozostałych porównań `True`.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.InvalidCastException>
- [=, operator](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Operatory porównania w języku Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
