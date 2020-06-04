---
title: Stała i typy literałów
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: b94259326b42104db05d9fc5bb09f686075d0759
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414534"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Stała i typy literałów (Visual Basic)
Literał jest wartością, która jest wyrażona jako sama wartość zmiennej lub wynik wyrażenia, takie jak liczba 3 lub ciąg "Hello". Stała jest zrozumiałą nazwą, która przyjmuje miejsce literału i zachowuje tę samą wartość w całym programie, w przeciwieństwie do zmiennej, której wartość może zmienić.  
  
 Gdy [opcja wnioskowanie](../../../language-reference/statements/option-infer-statement.md) jest `Off` i [opcją Strict](../../../language-reference/statements/option-strict-statement.md) jest `On` , należy zadeklarować wszystkie stałe jawnie z typem danych. W poniższym przykładzie typ danych `MyByte` jest zadeklarowany jako typ danych `Byte` :  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off` , można zadeklarować stałą bez określania typu danych z `As` klauzulą. Kompilator określa typ stałej z typu wyrażenia. Literał liczbowy liczb całkowitych jest domyślnie rzutowany na `Integer` Typ danych. Domyślny typ danych dla liczb zmiennoprzecinkowych to `Double` , i słowa kluczowe `True` i `False` Określanie `Boolean` stałej.  
  
## <a name="literals-and-type-coercion"></a>Literały i przekształcenia typów  
 W niektórych przypadkach może zajść potrzeba wymuszenia literału dla określonego typu danych; na przykład podczas przypisywania szczególnie dużej wartości literału całkowitego do zmiennej typu `Decimal` . Poniższy przykład generuje błąd:  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Błąd wynika z reprezentacji literału. `Decimal`Typ danych może przechowywać wartość, która jest duża, ale literał jest niejawnie reprezentowany jako `Long` , co nie może.  
  
 Można przekształcić literał na określony typ danych na dwa sposoby: przez dołączenie do niego znaku typu lub umieszczenie go w obrębie otaczających znaków. Znak typu lub otaczające znaki muszą bezpośrednio poprzedzać i/lub stosować literał, bez spacji lub znaków w żadnym rodzaju.  
  
 Aby wykonać poprzedni przykład pracy, można dołączyć `D` znak typu do literału, co powoduje, że jest reprezentowany jako `Decimal` :  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 Poniższy przykład ilustruje poprawne użycie znaków typu i otaczające znaki:  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 W poniższej tabeli przedstawiono znaki otaczające i znaki typu dostępne w Visual Basic.  
  
|Typ danych|Znak otaczający|Znak typu dołączanego|  
|---|---|---|  
|`Boolean`|(brak)|(brak)|  
|`Byte`|(brak)|(brak)|  
|`Char`|"|C|  
|`Date`|#|(brak)|  
|`Decimal`|(brak)|D lub @|  
|`Double`|(brak)|R lub #|  
|`Integer`|(brak)|I lub%|  
|`Long`|(brak)|L lub &|  
|`Short`|(brak)|S|  
|`Single`|(brak)|F lub!|  
|`String`|"|(brak)|  
  
## <a name="see-also"></a>Zobacz też

- [Stałe zdefiniowane przez użytkownika](user-defined-constants.md)
- [Instrukcje: deklarowanie stałej](how-to-declare-a-constant.md)
- [Stałe — Przegląd](constants-overview.md)
- [Option Strict — Instrukcja](../../../language-reference/statements/option-strict-statement.md)
- [Option Explicit, instrukcja](../../../language-reference/statements/option-explicit-statement.md)
- [Enumerations — Przegląd](enumerations-overview.md)
- [Instrukcje: deklarowanie wyliczenia](how-to-declare-enumerations.md)
- [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md)
- [Typy danych](../../../language-reference/data-types/index.md)
- [Stałe i wyliczenia](../../../language-reference/constants-and-enumerations.md)
