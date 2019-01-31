---
title: Kopiowanie wartości parametru „ByRef” <parametername>” z powrotem do pasującego argumentu powoduje zawężenie typu „<typename1>” do typu „<typename2>”.
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: c5d427495e8eedae9dc0163c97401338fb6d0bbd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276617"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a>Kopiowanie wartości parametru "ByRef" "\<parametername >" powrotem do pasującego argumentu powoduje zawężenie z typu "\<typename1 >" na typ "\<typename2 >"
Procedura jest wywoływana z argumentem, który rozszerza się na odpowiedni typ parametru. Ponadto jest zawężenie konwersji z parametru do argumentu.  
  
 Po zdefiniowaniu klasy lub struktury, można zdefiniować co najmniej jeden operatory konwersji można przekonwertować typu klasy lub struktury do innych typów. Można również definiować operatory konwersji odwrotnej do konwersji tych typów do swojej klasy lub typ struktury. Korzystając z typu klasy lub struktury w wywołaniu procedury, Visual Basic można użyć te operatory konwersji można przekonwertować na typ argumentu do typu jego odpowiadającego mu parametru.  
  
 W przypadku przekazania argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, zamiast przekazywać odwołania. W takim przypadku po powrocie z procedury języka Visual Basic należy skopiować do argumentu w wywoływanym kodzie następnie wartości zmiennej lokalnej.  
  
 Jeśli `ByRef` wartość argumentu jest kopiowana do procedury i parametry i argument są tego samego typu, konwersja nie jest konieczne. Jednak w przypadku różnych typów języka Visual Basic należy przekonwertować w obu kierunkach. Jeśli jeden z typów jest typu klasy lub struktury, Visual Basic należy przekonwertować go do i z innego typu. Jeśli jeden z tych konwersji jest rozszerzenie, może być zawężanie konwersji odwrotnej.  
  
 **Identyfikator błędu:** BC32053  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli to możliwe należy użyć wywoływania argumentów tego samego typu jako parametr procedury, Visual Basic nie trzeba wykonać żadnych konwersji.  
  
-   Jeśli musisz wywołać procedurę z nieprawidłowym argumentem typu różni się od typu parametru, ale nie muszą zwracać wartość do wywołującego argumentu, zdefiniuj parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) zamiast `ByRef`.  
  
-   Jeśli trzeba zwrócić wartości do wywoływania argumentów, definiowanie operatora konwersji zwrotny jako [Widening](../../../visual-basic/language-reference/modifiers/widening.md), jeśli to możliwe.  
  
## <a name="see-also"></a>Zobacz także
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Parametry i argumenty procedur](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Przekazywanie argumentów według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Instrukcje: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Instrukcje: Definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Konwersje typów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
