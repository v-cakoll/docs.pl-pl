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
ms.openlocfilehash: 8ebecddfab0724023c269e92c1fc5534f096bf1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333727"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Stała i typy literałów (Visual Basic)
Literał jest wartością, która jest wyrażona jako sama wartość zmiennej lub wynik wyrażenia, takie jak liczba 3 lub ciąg "Hello". Stała jest zrozumiałą nazwą, która przyjmuje miejsce literału i zachowuje tę samą wartość w całym programie, w przeciwieństwie do zmiennej, której wartość może zmienić.  
  
 Gdy [opcja wnioskowanie](../../../../visual-basic/language-reference/statements/option-infer-statement.md) jest `Off`, a [opcja Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) jest `On`, należy zadeklarować wszystkie stałe jawnie z typem danych. W poniższym przykładzie typ danych `MyByte` jest zadeklarowany jako typ danych `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off`, można zadeklarować stałą bez określania typu danych z klauzulą `As`. Kompilator określa typ stałej z typu wyrażenia. Literał liczbowy liczb całkowitych jest domyślnie rzutowany na typ danych `Integer`. Domyślny typ danych dla liczb zmiennoprzecinkowych to `Double`, a słowa kluczowe `True` i `False` określają stałą `Boolean`.  
  
## <a name="literals-and-type-coercion"></a>Literały i przekształcenia typów  
 W niektórych przypadkach może zajść potrzeba wymuszenia literału dla określonego typu danych; na przykład podczas przypisywania szczególnie dużej wartości literału całkowitego do zmiennej typu `Decimal`. Poniższy przykład generuje błąd:  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Błąd wynika z reprezentacji literału. Typ danych `Decimal` może przechowywać wartość, która jest duża, ale literał jest niejawnie reprezentowany jako `Long`, co nie może.  
  
 Można przekształcić literał na określony typ danych na dwa sposoby: przez dołączenie do niego znaku typu lub umieszczenie go w obrębie otaczających znaków. Znak typu lub otaczające znaki muszą bezpośrednio poprzedzać i/lub stosować literał, bez spacji lub znaków w żadnym rodzaju.  
  
 Aby wykonać poprzedni przykład pracy, można dołączyć do literału znak typu `D`, który powoduje, że jest on reprezentowany jako `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 Poniższy przykład ilustruje poprawne użycie znaków typu i otaczające znaki:  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 W poniższej tabeli przedstawiono znaki otaczające i znaki typu dostępne w Visual Basic.  
  
|Typ danych|Znak otaczający|Znak typu dołączanego|  
|---|---|---|  
|`Boolean`|dawaj|dawaj|  
|`Byte`|dawaj|dawaj|  
|`Char`|"|C|  
|`Date`|#|dawaj|  
|`Decimal`|dawaj|D lub @|  
|`Double`|dawaj|R lub #|  
|`Integer`|dawaj|I lub%|  
|`Long`|dawaj|L lub &|  
|`Short`|dawaj|S|  
|`Single`|dawaj|F lub!|  
|`String`|"|dawaj|  
  
## <a name="see-also"></a>Zobacz także

- [Stałe zdefiniowane przez użytkownika](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [Instrukcje: deklarowanie stałej](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Option Explicit, instrukcja](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Instrukcje: deklarowanie wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
