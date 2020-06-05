---
title: Operatory porównania
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
ms.openlocfilehash: bcd51d70c5c7bd08991c7433e244316a82daa9da
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371794"
---
# <a name="comparison-operators-visual-basic"></a>Operatory porównania (Visual Basic)
Poniżej przedstawiono operatory porównania zdefiniowane w Visual Basic.

 `<`zakład

 `<=`zakład

 `>`zakład

 `>=`zakład

 `=`zakład

 `<>`zakład

 [Is, operator](is-operator.md)

 [IsNot, operator](isnot-operator.md)

 [Like — Operator](like-operator.md)

 Te operatory porównują dwa wyrażenia, aby określić, czy są równe, i czy nie, jak się różnią. `Is`, `IsNot` i `Like` są szczegółowo omówione na oddzielnych stronach pomocy. Operatory porównujące relacyjne zostały szczegółowo omówione na tej stronie.

## <a name="syntax"></a>Składnia
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Części
 `result`  
 Wymagany. `Boolean`Wartość reprezentująca wynik porównania.

 `expression1`, `expression2`  
 Wymagany. Dowolne wyrażenie.

 `comparisonoperator`  
 Wymagany. Dowolny operator porównania relacyjnego.

 `object1`, `object2`  
 Wymagany. Wszystkie nazwy obiektów odniesienia.

 `string`  
 Wymagany. Dowolne `String` wyrażenie.

 `pattern`  
 Wymagany. Dowolne `String` wyrażenie lub zakres znaków.

## <a name="remarks"></a>Uwagi
 Poniższa tabela zawiera listę operatorów relacyjnych porównania i warunki, które określają, czy `result` jest `True` lub `False` .

|Operator|`True`przypadku|`False`przypadku|
|--------------|---------------|----------------|
|`<`(Mniejsze niż)|`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=`(Mniejsze niż lub równe)|`expression1` <= `expression2`|`expression1` > `expression2`|
|`>`(Większe niż)|`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=`(Większe niż lub równe)|`expression1` >= `expression2`|`expression1` < `expression2`|
|`=`(Równe)|`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>`(Nie równa się)|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> [Operator =](assignment-operator.md) jest również używany jako operator przypisania.

 `Is`Operator, `IsNot` operator i `Like` operator mają określone funkcje porównania, które różnią się od operatorów w powyższej tabeli.

## <a name="comparing-numbers"></a>Porównywanie liczb
 W przypadku porównania wyrażenia typu `Single` z jednym z typów `Double` `Single` wyrażenie jest konwertowane na `Double` . Takie zachowanie jest przeciwieństwem do zachowania znalezionego w Visual Basic 6.

 Podobnie, podczas porównywania wyrażenia typu `Decimal` z wyrażeniem typu `Single` lub wyrażenie `Double` `Decimal` jest konwertowane na `Single` lub `Double` . W przypadku `Decimal` wyrażeń, każda wartość ułamkowa mniejsza od 1e-28 może zostać utracona. Taka ułamkowa utrata wartości może spowodować, że dwie wartości będą porównywane jako równe, gdy nie są. Z tego powodu należy zadbać o to, aby przy użyciu równości ( `=` ) porównać dwie zmienne zmiennoprzecinkowe. Jest bezpieczniejsze, aby sprawdzić, czy wartość bezwzględna różnicy między dwoma liczbami jest mniejsza niż mała akceptowalna tolerancja.

### <a name="floating-point-imprecision"></a>Niedokładność zmiennoprzecinkowa
 Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają dokładną reprezentację w pamięci. Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównanie wartości i [operator mod](mod-operator.md). Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="comparing-strings"></a>Porównywanie ciągów
 Podczas porównywania ciągów wyrażenia ciągów są oceniane na podstawie alfabetycznej kolejności sortowania, która zależy od `Option Compare` Ustawienia.

 `Option Compare Binary`podstaw porównania ciągów w kolejności sortowania pochodzącej od wewnętrznych reprezentacji binarnych znaków. Kolejność sortowania jest określana na podstawie strony kodowej. W poniższym przykładzie przedstawiono typowy binarny porządek sortowania.

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text`podstawowe porównania ciągów w przypadku, w którym rozróżniana jest wielkość liter, porządek sortowania w postaci tekstu określony przez ustawienia regionalne Twojej aplikacji. Po ustawieniu `Option Compare Text` i posortowaniu znaków w poprzednim przykładzie stosuje się następujący porządek sortowania tekstu:

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>Zależność ustawień regionalnych
 Po ustawieniu `Option Compare Text` wynik porównania ciągów może zależeć od ustawień regionalnych, w których działa aplikacja. Dwa znaki mogą być porównywane jako równe w jednej lokalizacji, ale nie w innym. Jeśli używasz porównania ciągów, aby podejmować ważne decyzje, na przykład czy należy zaakceptować próbę zalogowania, należy ostrzec o czułości ustawień regionalnych. Rozważ ustawienie `Option Compare Binary` lub wywołanie metody <xref:Microsoft.VisualBasic.Strings.StrComp%2A> , która przyjmuje ustawienia regionalne.

## <a name="typeless-programming-with-relational-comparison-operators"></a>Programowanie bez typu z relacyjnymi operatorami porównania
 Użycie operatorów porównania relacyjnego z `Object` wyrażeniami jest niedozwolone w `Option Strict On` . Gdy `Option Strict` jest `Off` , i albo `expression1` `expression2` jest `Object` wyrażeniem, typy czasu wykonywania określają, jak są porównywane. W poniższej tabeli przedstawiono, w jaki sposób wyrażenia są porównywane i wynik porównania, w zależności od typu czasu wykonywania argumentów operacji.

|Jeśli operandy są|Porównanie jest|
|---------------------|-------------------|
|Jedn`String`|Porównanie sortowania na podstawie charakterystyki sortowania ciągów.|
|Zarówno liczbowe|Obiekty konwertowane na `Double` , porównywanie numeryczne.|
|Jeden i jeden`String`|`String`Jest konwertowany na `Double` i jest wykonywane porównywanie numeryczne. Jeśli `String` nie można przekonwertować na `Double` , <xref:System.InvalidCastException> zostanie zgłoszony.|
|Oba lub oba są typami odwołań innym niż`String`|<xref:System.InvalidCastException>Jest zgłaszany.|

 Porównania liczbowe traktują się `Nothing` jako 0. Porównania ciągów traktują `Nothing` jako `""` (pusty ciąg).

## <a name="overloading"></a>Przeciążenie
 Operatory porównania relacyjnego ( `<` . `<=`, `>` ,,, `>=` `=` `<>` ) może być *przeciążona*, co oznacza, że Klasa lub struktura mogą definiować ich zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli kod używa dowolnego z tych operatorów w takiej klasie lub strukturze, pamiętaj o tym, aby zrozumieć zachowanie, które zostało ponownie zdefiniowane. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).

 Należy zauważyć, że [operator =](assignment-operator.md) może być przeciążony tylko jako operator porównania relacyjnego, a nie jako operator przypisania.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano różne zastosowania relacyjnych operatorów porównania, które służą do porównywania wyrażeń. Relacyjne operatory porównujące zwracają `Boolean` wynik, który reprezentuje, czy wyrażenie podane ma wartość `True` . Gdy `>` Operatory i są stosowane `<` do ciągów, porównanie jest wykonywane przy użyciu zwykłej alfabetycznej kolejności sortowania ciągów. Ta kolejność może być zależna od ustawień regionalnych. Czy sortowanie jest rozróżniana wielkość liter, czy nie jest zależne od [opcji Porównaj](../statements/option-compare-statement.md) ustawienia.

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 W poprzednim przykładzie pierwsze porównanie zwraca, `False` a pozostałe porównania zwracają `True` .

## <a name="see-also"></a>Zobacz też

- <xref:System.InvalidCastException>
- [= — Operator](assignment-operator.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Rozwiązywanie problemów związanych z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Operatory porównania w Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
