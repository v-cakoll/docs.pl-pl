---
title: Stała i typy literałów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 1d030f8058cd497212c20bca8f064f2bedc99fce
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389564"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Stała i typy literałów (Visual Basic)
Literał jest wartość, która jest wyrażona w swoim imieniu, a nie jako wartość zmiennej lub wyniku wyrażenia, takie jak numer 3 lub ciąg "Hello". Stałe są znaczącą nazwę, która zajmuje miejsce literału i zachowuje ta sama wartość w całym programie, w przeciwieństwie do zmiennej, którego wartość może ulec zmianie.  
  
 Gdy [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) jest `Off` i [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) jest `On`, należy jawnie zadeklarować wszystkich stałych o typie danych. W poniższym przykładzie typ danych `MyByte` jest jawnie zadeklarowana jako typ danych `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off`, stałej można zadeklarować bez określania typu danych za pomocą `As` klauzuli. Kompilator Określa typ stałej z typu wyrażenia. Liczbowe literał liczby całkowitej jest rzutowany domyślnie `Integer` typu danych. Domyślny typ danych liczb zmiennoprzecinkowych jest `Double`i słowa kluczowe `True` i `False` określ `Boolean` stałej.  
  
## <a name="literals-and-type-coercion"></a>Literały i wymuszenia typu  
 W niektórych przypadkach możesz chcieć wymusić literału do określonego typu danych; na przykład podczas przypisywania szczególnie dużą wartość całkowitą literału do zmiennej typu `Decimal`. Poniższy przykład generuje błąd:  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Ten błąd wynika z reprezentacji literału. `Decimal` Typu danych można zawierającą wartość parametru tak dużej, ale literał niejawnie jest reprezentowany jako `Long`, które nie mogą.  
  
 Można wymusić literału do określonego typu danych na dwa sposoby: przez dodanie znaku typu do niego lub przez umieszczenie ich w ramach otaczającej znaków. Znak typu lub Załączanie znaków musi bezpośrednio poprzedzać i/lub wykonaj literału, bez pośredniczące miejsca lub znaków jakiegokolwiek rodzaju.  
  
 Aby w poprzednim przykładzie działają, można dołączyć `D` wpisz znak literału, który powoduje, że może być reprezentowana jako `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 Poniższy przykład pokazuje poprawne użycie typu znaki i znaki otaczającej:  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 Pokazano w poniższej tabeli otaczającego znaki i znaki typu, które są dostępne w języku Visual Basic.  
  
|Typ danych|Otaczający znaków|Znak typu dołączonych|  
|---|---|---|  
|`Boolean`|(Brak)|(Brak)|  
|`Byte`|(Brak)|(Brak)|  
|`Char`|"|C|  
|`Date`|#|(Brak)|  
|`Decimal`|(Brak)|D lub @|  
|`Double`|(Brak)|R lub #|  
|`Integer`|(Brak)|Lub %|  
|`Long`|(Brak)|L lub &|  
|`Short`|(Brak)|S|  
|`Single`|(Brak)|F lub!|  
|`String`|"|(Brak)|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe zdefiniowane przez użytkownika](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [Instrukcje: deklarowanie stałej](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Option Explicit, instrukcja](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Porady: deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)  
 [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
