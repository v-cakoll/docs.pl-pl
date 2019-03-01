---
title: Rozpoznanie przeciążenia (Visual Basic)
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
ms.openlocfilehash: c55b1c001ae1c74b0c34d716b9fa3f90dade3e28
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966232"
---
# <a name="overload-resolution-visual-basic"></a>Rozpoznanie przeciążenia (Visual Basic)
Gdy kompilator języka Visual Basic napotyka wywołanie procedury, która jest zdefiniowana w kilku przeciążone wersje, kompilator należy zdecydować, której przeciążenia do wywołania. Dzieje się tak, wykonując następujące czynności:  
  
1.  **Ułatwienia dostępu.** Eliminuje to żadnego przeciążenia z poziomem dostępu, który uniemożliwia jej wywołanie kodu wywołującego.  
  
2.  **Liczba parametrów.** Eliminuje to wszystkie przeciążenia, które definiuje szereg różnych parametrów nie są określane w wywołaniu.  
  
3.  **Typ danych parametru.** Kompilator preferuje wystąpienia metod za pośrednictwem metody rozszerzenia. Jeśli zostanie znaleziony dowolnej metody wystąpienia, która wymaga tylko poszerzeniem konwersji, w celu dopasowania wywołania procedury, wszystkie metody rozszerzenia są odrzucane i kompilator będzie kontynuowane z użyciem kandydatów metody wystąpienia. Jeśli żadna metoda wystąpienia zostanie znaleziony, jest kontynuowane przy użyciu wystąpienia i metody rozszerzenia.  
  
     W tym kroku pozwala wyeliminować żadnego przeciążenia, dla którego typy danych, wywoływania argumentów nie można przekonwertować na typy parametrów zdefiniowanych w przeciążenia.  
  
4.  **Konwersje zawężające.** Eliminuje to żadnego przeciążenia, który wymaga konwersji zawężającej od wywołującego typy argumentów do parametrów zdefiniowanych typów. Jest to istotne, czy przełączyć kontrola typów ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On` lub `Off`.  
  
5.  **Co najmniej rozszerzanie.** Kompilator traktuje pozostałe przeciążeń w pary. Dla każdej pary porównuje typy danych zdefiniowanych parametrów. Jeśli jedno z przeciążeń wszystkich typów są rozszerzane odpowiadające typy w innym, kompilator eliminuje te ostatnie. Oznacza to, że zachowuje przeciążenia, które wymaga minimalnej liczbie rozszerzanie.  
  
6.  **Pojedynczy Release Candidate.** Kontynuuje considering przeciążenia w parach, dopóki tylko jeden przeciążenia pozostaje i jest rozpoznawana jako wywołanie tego przeciążenia. Jeśli kompilator nie może ograniczyć przeciążenia do pojedynczego Release candidate, spowoduje wygenerowanie błędu.  
  
 Na poniższej ilustracji przedstawiono proces, który określa, który zestaw przeciążone wersje do wywołania.  
  
 ![Diagram przepływu procesu rozpoznawania przeciążenia](./media/overloadres.gif "OverloadRes")  
Rozpoznawanie między przeciążone wersje  
  
 Poniższy przykład ilustruje ten proces rozpoznawania przeciążenia.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 W pierwszym wywołaniu kompilator eliminuje pierwsze przeciążenie, ponieważ typ pierwszego argumentu (`Short`) powoduje zawężenie typu odpowiadającego mu parametru (`Byte`). Następnie eliminuje trzecie przeciążenie ponieważ każdy argument typu w drugie przeciążenie (`Short` i `Single`) rozszerza się na odpowiedni typ w trzecie przeciążenie (`Integer` i `Single`). Drugie przeciążenie wymaga mniej rozszerzenia, dlatego kompilator używa go na potrzeby wywołania.  
  
 W drugim wywołaniu kompilator nie może wyeliminować żadnego przeciążenia na podstawie zawężanie. Eliminuje to trzecie przeciążenie dla tego samego powodu, tak jak w pierwszym wywołaniu, ponieważ może wywołać drugie przeciążenie z mniej rozszerzanie typy argumentów. Jednak kompilator nie może rozpoznać między przeciążeniami pierwszego i drugiego. Każda z nich ma jeden typ zdefiniowany parametr, który rozszerza się na odpowiedni typ w innym (`Byte` do `Short`, ale `Single` do `Double`). Kompilator generuje w związku z tym błędem rozpoznawania przeciążenia.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Przeciążone opcjonalne i ParamArray-argumenty  
 Jeśli dwa przeciążenia procedury, posiadające identyczne oznaczenie, z tą różnicą, że ostatni parametr jest zadeklarowana [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) w jednym i [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) w innych, kompilator rozpoznaje wywołania tej procedury jako następujące:  
  
|Jeśli wywołanie dostarcza ostatni argument jako|Kompilator rozpoznaje wywołania przeciążenia deklarowanie ostatni argument jako|  
|---|---|  
|Brak wartości (pominięty argument)|`Optional`|  
|Pojedyncza wartość|`Optional`|  
|Dwie lub więcej wartości na liście rozdzielanej przecinkami|`ParamArray`|  
|Tablica o dowolnej długości (w tym pusta tablica)|`ParamArray`|  
  
## <a name="see-also"></a>Zobacz także
- [Parametry opcjonalne](./optional-parameters.md)
- [Tablice parametrów](./parameter-arrays.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: Wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Metody rozszerzeń](./extension-methods.md)
