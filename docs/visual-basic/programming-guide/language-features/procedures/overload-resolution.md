---
title: Rozpoznanie przeciążenia
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: 84d52bbbfb34c2e5d67ed6a1810ab3e32fafda22
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266875"
---
# <a name="overload-resolution-visual-basic"></a>Rozpoznanie przeciążenia (Visual Basic)
Gdy kompilator języka Visual Basic napotka wywołanie procedury, która jest zdefiniowana w kilku przeciążonych wersjach, kompilator musi zdecydować, które z przeciążeń do wywołania. Robi to wykonując następujące kroki:  
  
1. **Dostępności.** Eliminuje wszelkie przeciążenia z poziomu dostępu, który uniemożliwia wywoływanie kodu wywołującego.  
  
2. **Liczba parametrów.** Eliminuje przeciążenie, które definiuje inną liczbę parametrów niż są dostarczane w wywołaniu.  
  
3. **Typy danych parametrów.** Kompilator daje metody wystąpienia preferencji nad metodami rozszerzenia. Jeśli zostanie znaleziona jakakolwiek metoda wystąpienia, która wymaga tylko rozszerzania konwersji, aby dopasować wywołanie procedury, wszystkie metody rozszerzenia są odrzucane, a kompilator kontynuuje tylko kandydatów metody wystąpienia. Jeśli nie zostanie znaleziona taka metoda wystąpienia, kontynuuje zarówno metody wystąpienia, jak i rozszerzenia.  
  
     W tym kroku eliminuje wszelkie przeciążenia, dla których nie można przekonwertować typów danych argumentów wywołujących na typy parametrów zdefiniowane w przeciążeniu.  
  
4. **Zawężanie konwersji.** Eliminuje wszelkie przeciążenia, które wymaga konwersji zawężenia z typów argumentów wywołujących do zdefiniowanych typów parametrów. Dotyczy to tego, czy przełącznik sprawdzania typu `On` ( `Off`Option[Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest lub .  
  
5. **Najmniej poszerzenie.** Kompilator uwzględnia pozostałe przeciążenia w parach. Dla każdej pary porównuje typy danych zdefiniowanych parametrów. Jeśli typy w jednym z przeciążeń wszystkie poszerzyć do odpowiednich typów w innych, kompilator eliminuje ten ostatni. Oznacza to, że zachowuje przeciążenie, które wymaga najmniejszej ilości poszerzenia.  
  
6. **Jeden kandydat.** Kontynuuje biorąc pod uwagę przeciążenia w parach, dopóki nie pozostaje tylko jedno przeciążenie i rozwiązuje wywołanie tego przeciążenia. Jeśli kompilator nie może zmniejszyć przeciążenia do jednego kandydata, generuje błąd.  
  
 Na poniższej ilustracji przedstawiono proces, który określa, który z zestawu przeciążonych wersji do wywołania.  
  
 ![Diagram przepływu procesu rozpoznawania przeciążenia](./media/overload-resolution/determine-overloaded-version.gif "Rozwiązywanie problemów między przeciążonymi wersjami")
  
 Poniższy przykład ilustruje ten proces rozpoznawania przeciążenia.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 W pierwszym wywołaniu kompilator eliminuje pierwsze przeciążenie, ponieważ`Short`typ pierwszego argumentu ( )`Byte`zawęża się do typu odpowiedniego parametru ( ). Następnie eliminuje trzecie przeciążenie, ponieważ każdy typ argumentu w drugim przeciążeniu`Short` ( i `Single``Integer` ) `Single`rozszerza się do odpowiedniego typu w trzecim przeciążeniu ( i ). Drugie przeciążenie wymaga mniej poszerzenia, więc kompilator używa go do wywołania.  
  
 W drugim wywołaniu kompilator nie można wyeliminować żadnych przeciążeń na podstawie zawężenia. Eliminuje trzecie przeciążenie z tego samego powodu, co w pierwszym wywołaniu, ponieważ może wywołać drugie przeciążenie z mniejszym rozszerzeniem typów argumentów. Jednak kompilator nie można rozwiązać między pierwszym i drugim przeciążenia. Każdy ma jeden zdefiniowany typ parametru, który`Byte` rozszerza `Short`się `Single` `Double`do odpowiedniego typu w drugim ( do , ale do ). Kompilator w związku z tym generuje błąd rozpoznawania przeciążenia.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Przeciążone opcjonalne i paramarray argumenty  
 Jeśli dwa przeciążenia procedury mają identyczne podpisy, z tą różnicą, że ostatni parametr jest [zadeklarowany opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) w jednym i [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) w drugim, kompilator rozwiązuje wywołanie tej procedury w następujący sposób:  
  
|Jeśli wywołanie dostarcza ostatni argument jako|Kompilator rozwiązuje wywołanie przeciążenia deklarując ostatni argument jako|  
|---|---|  
|Brak wartości (argument pominięty)|`Optional`|  
|Pojedyncza wartość|`Optional`|  
|Dwie lub więcej wartości na liście oddzielonej przecinkami|`ParamArray`|  
|Tablica o dowolnej długości (łącznie z pustą tablicą)|`ParamArray`|  
  
## <a name="see-also"></a>Zobacz też

- [Parametry opcjonalne](./optional-parameters.md)
- [Parameter — Tablice](./parameter-arrays.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Metody rozszerzeń](./extension-methods.md)
