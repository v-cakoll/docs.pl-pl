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
ms.openlocfilehash: 0e69136b1e3015055cad9852bf04151f57558b88
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352645"
---
# <a name="overload-resolution-visual-basic"></a>Rozpoznanie przeciążenia (Visual Basic)
Gdy kompilator Visual Basic napotyka wywołanie procedury, która jest zdefiniowana w kilku przeciążonych wersjach, kompilator musi zdecydować, które z przeciążeń mają być wywoływane. Robi to, wykonując następujące czynności:  
  
1. **Ułatwienia dostępu.** Eliminuje wszelkie przeciążenia z poziomem dostępu, który uniemożliwia Wywoływanie kodu wywołującego.  
  
2. **Liczba parametrów.** Eliminuje wszelkie przeciążenia, które definiują inną liczbę parametrów niż podano w wywołaniu.  
  
3. **Typ danych parametru.** Kompilator zapewnia preferencje metod wystąpień względem metod rozszerzających. Jeśli zostanie znaleziona jakakolwiek metoda wystąpienia, która wymaga tylko konwersji rozszerzających, aby pasowała do wywołania procedury, wszystkie metody rozszerzające są porzucane, a kompilator kontynuuje tylko z użyciem metody wystąpienia. Jeśli nie zostanie znaleziona taka metoda wystąpienia, kontynuuje z obu tych metod.  
  
     W tym kroku eliminuje wszelkie przeciążenia, dla których typy danych argumentów wywołujących nie mogą być konwertowane na typy parametrów zdefiniowane w przeciążenia.  
  
4. **Zawężanie konwersji.** Eliminuje wszelkie przeciążenia, które wymagają konwersji zawężania z typów argumentów wywołujących na zdefiniowane typy parametrów. Jest to prawdą, czy przełącznik sprawdzania typu ([instrukcja Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On` lub `Off`.  
  
5. **Najmniej rozszerzanie.** Kompilator traktuje pozostałe przeciążenia w parach. Dla każdej pary porównuje typy danych zdefiniowanych parametrów. Jeśli typy w jednym z przeciążeń wszystkie rozszerzają się do odpowiednich typów w drugim, kompilator eliminuje ten ostatni. Oznacza to, że zachowuje Przeciążenie, które wymaga najmniejszej ilości rozszerzania.  
  
6. **Pojedynczy kandydat.** Kontynuuje rozważanie przeciążenia par do momentu pozostawania tylko jednego przeciążenia i rozwiązuje wywołanie do tego przeciążenia. Jeśli kompilator nie może zmniejszyć przeciążenia do pojedynczego kandydata, generuje błąd.  
  
 Na poniższej ilustracji przedstawiono proces określający, który z zestawów przeciążonych wersji ma być wywoływana.  
  
 ![Diagram przepływu procesu rozpoznawania przeciążenia](./media/overload-resolution/determine-overloaded-version.gif "Rozwiązywanie między przeciążonymi wersjami")    
  
 Poniższy przykład ilustruje ten proces rozwiązywania przeciążenia.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 W pierwszym wywołaniu kompilator eliminuje pierwsze Przeciążenie, ponieważ typ pierwszego argumentu (`Short`) jest wąski do typu odpowiadającego mu parametru (`Byte`). Następnie eliminuje trzecie Przeciążenie, ponieważ każdy typ argumentu w drugim przeciążeniu (`Short` i `Single`) poszerza do odpowiedniego typu w trzecim przeciążenia (`Integer` i `Single`). Drugie Przeciążenie wymaga mniej poszerzania, więc kompilator używa go do wywołania.  
  
 W drugim wywołaniu kompilator nie może wyeliminować żadnych przeciążeń na podstawie zawężania. Eliminuje trzecie Przeciążenie z tego samego powodu, co w pierwszym wywołaniu, ponieważ może wywoływać drugie Przeciążenie przy mniejszej poszerzeniu typów argumentów. Jednak kompilator nie może rozpoznać pierwszego i drugiego przeciążenia. Każdy z nich ma jeden zdefiniowany typ parametru, który jest poszerzany do odpowiedniego typu w drugim (`Byte` do `Short`, ale `Single` do `Double`). W związku z tym kompilator generuje błąd rozpoznawania przeciążenia.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Przeciążone argumenty opcjonalne i ParamArray  
 Jeśli dwa przeciążenia procedury mają identyczne podpisy, z wyjątkiem tego, że ostatni parametr jest zadeklarowany jako [opcjonalny](../../../../visual-basic/language-reference/modifiers/optional.md) w jednym i [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) w drugim, kompilator rozpoznaje wywołanie tej procedury w następujący sposób:  
  
|Jeśli wywołanie dostarcza ostatni argument jako|Kompilator rozpoznaje wywołanie do przeciążenia deklarującego ostatni argument jako|  
|---|---|  
|Brak wartości (pominięto argument)|`Optional`|  
|Pojedyncza wartość|`Optional`|  
|Co najmniej dwie wartości na liście rozdzielanej przecinkami|`ParamArray`|  
|Tablica dowolnej długości (łącznie z pustą tablicą)|`ParamArray`|  
  
## <a name="see-also"></a>Zobacz także

- [Parametry opcjonalne](./optional-parameters.md)
- [Tablice parametrów](./parameter-arrays.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Metody rozszerzeń](./extension-methods.md)
