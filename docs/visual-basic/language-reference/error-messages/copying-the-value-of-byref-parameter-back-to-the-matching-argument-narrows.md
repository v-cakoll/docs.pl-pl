---
title: Kopiowanie wartości &#39;ByRef&#39; parametru &#39; &lt;parametername&gt; &#39; powrotem do pasującego argumentu powoduje zawężenie z typu &#39; &lt;typename1&gt; &#39; do typu &#39; &lt;typename2&gt;&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18c72e56e4b2cc9c2251de2417a9f12a6688323f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>Kopiowanie wartości &#39;ByRef&#39; parametru &#39; &lt;parametername&gt; &#39; powrotem do pasującego argumentu powoduje zawężenie z typu &#39; &lt;typename1&gt; &#39; do typu &#39; &lt;typename2&gt;&#39;
Procedura jest wywoływana z argumentem rozszerzająca do odpowiedniego typu parametru, a jest zawężanie konwersji z parametru do argumentu.  
  
 Podczas definiowania klasy lub struktury, można zdefiniować co najmniej jeden operatory konwersji można przekonwertować typu klasy lub struktury na inne typy. Można również definiować operatory konwersji odwrotnej do konwertowania tych typów do własnej klasy lub typ struktury. Używając danego typu klasy lub struktury w wywołaniu procedury, Visual Basic można użyć tych operatory konwersji można przekonwertować typu argumentu na typ jego odpowiadającego mu parametru.  
  
 Jeśli zostanie przekazany argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, a przekazywaniem odwołań do. W takim przypadku po powrocie z procedury języka Visual Basic należy skopiować do argumentu w wywoływanym kodzie następnie wartości zmiennej lokalnej.  
  
 Jeśli `ByRef` wartość argumentu jest kopiowany do procedury i argumentów i parametrów są tego samego typu, niezbędne jest brak konwersji. Ale typy są różne, Visual Basic, należy przekonwertować w obu kierunkach. Jeśli jeden z typów jest danego typu klasy lub struktury, Visual Basic przekonwertować ją zarówno do, jak i z innego typu. Jeśli jeden z tych konwersje to rozszerzenie, może być zawężanie konwersji odwrotnej.  
  
 **Identyfikator błędu:** BC32053  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli to możliwe należy użyć wywoływania argumentów tego samego typu jako parametru procedury dzięki Visual Basic nie trzeba wykonać żadnej konwersji.  
  
-   Jeśli musisz wywołać procedurę z argumentem Typ inny niż typ parametru, ale nie muszą zwracać wartość do wywołującego argumentu, zdefiniuj dany parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) zamiast `ByRef`.  
  
-   Jeśli trzeba zwrócić wartość do wywołującego argumentu, należy zdefiniować operator konwersji odwrotnej jako [Widening](../../../visual-basic/language-reference/modifiers/widening.md), jeśli to możliwe.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametry i argumenty procedur](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Przekazywanie argumentów według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Instrukcje: definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Konwersje typów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
