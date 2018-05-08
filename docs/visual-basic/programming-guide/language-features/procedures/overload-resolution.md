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
ms.openlocfilehash: d95589eb16f45eeff10692cdc897bf65ebe2d84e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="overload-resolution-visual-basic"></a>Rozpoznanie przeciążenia (Visual Basic)
Gdy kompilator Visual Basic napotka wywołaniu procedury, która jest zdefiniowana w kilku wersji przeciążona, kompilator należy zdecydować, które przeciążeń do wywołania. Dzieje się tak, wykonując następujące czynności:  
  
1.  **Ułatwienia dostępu.** Eliminuje wszystkie przeciążenia z poziomu dostępu, uniemożliwiający wywoływanie jej kod wywołujący.  
  
2.  **Liczba parametrów.** Eliminuje wszystkie przeciążenia, który definiuje różne liczby parametrów niż podano w wywołaniu.  
  
3.  **Typ danych parametru.** Kompilator przekazuje metody rozszerzenia preferencji metody wystąpienia. Jeśli zostanie znaleziony dowolnej metody wystąpienia, który wymaga tylko rozszerzanie konwersji w celu dopasowania wywołania procedury, wszystkie metody rozszerzenia są usuwane i kompilator będzie kontynuowane przy użyciu kandydatów metody wystąpienia. Jeśli zostanie znaleziony taki metody wystąpienia, będzie kontynuowane z wystąpienia i metody rozszerzenia.  
  
     W tym kroku eliminuje wszystkie przeciążenia, dla którego typy danych, wywoływania argumentów nie można przekonwertować na typy parametrów zdefiniowanych w przeciążenia.  
  
4.  **Zawężanie konwersji.** Eliminuje wszystkie przeciążenia, które wymaga zwężenia konwersji z wywołania typy argumentów do typów zdefiniowanych parametrów. Dotyczy to określa, czy sprawdzanie typu przełączać ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On` lub `Off`.  
  
5.  **Co najmniej rozszerzanie.** Kompilator uwzględnia pozostałych przeciążeń w parach. Dla każdej pary porównuje typów danych zdefiniowanych parametrów. Jeśli poszerzyć typów w jednym z przeciążeń wszystkie odpowiednie typy w innym, kompilator eliminuje to drugie. Oznacza to zachowuje przeciążenia, które wymaga minimalnej liczbie rozszerzanie.  
  
6.  **Jeden kandydat.** Nadal considering przeciążenia parami dopóki tylko jeden przeciążenia pozostaje oraz umożliwia rozwiązanie można wywołać tego przeciążenia. Czy kompilator nie można zmniejszyć przeciążeń do pojedynczego kandydujących, zostanie wygenerowany błąd.  
  
 Na poniższej ilustracji przedstawiono proces, który określa, który zestaw zastąpionej wersji do wywołania.  
  
 ![Diagram przepływu procesu rozpoznawania przeciążenia](./media/overloadres.gif "OverloadRes")  
Rozpoznawanie między zastąpionej wersji  
  
 Poniższy przykład przedstawia tego procesu rozpoznawania przeciążenia.  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 W pierwszym wywołaniu kompilator eliminuje pierwszy przeciążenia, ponieważ typ pierwszego argumentu (`Short`) znajduje się w zakresie odpowiadającego mu parametru na typ (`Byte`). Następnie program eliminuje trzeci przeciążenia ponieważ każdy argument typu w drugim przeciążenia (`Short` i `Single`) rozszerzenie do danego typu w trzecim przeciążenia (`Integer` i `Single`). Drugi przeciążenia wymaga mniej rozszerzenia, dlatego kompilator używa go do wywołania.  
  
 W wywołaniu drugi kompilator nie może wyeliminować żadnego przeciążenia na podstawie zawężanie. Eliminuje trzeci przeciążenia z tego samego powodu jak pierwsze wywołanie, ponieważ mogą wywoływać przeciążenia drugi z mniej rozszerzanie typy argumentów. Jednak kompilator nie można rozpoznać między pierwszym i drugim przeciążeń. Każdy ma jeden typ parametru zdefiniowanego rozszerzająca do danego typu w innym (`Byte` do `Short`, ale `Single` do `Double`). Kompilator generuje w związku z tym błąd rozpoznawania przeciążenia.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Przeciążone opcjonalne i ParamArray-argumenty  
 Jeśli dwa przeciążenia procedury identycznych podpisach z tą różnicą, że jest zadeklarowany jako ostatni parametr [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) w jednym i [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) w innych, kompilator rozpoznaje wywołania tej procedury jako następująco:  
  
|Jeśli wywołanie dostarcza jako ostatni argument|Kompilator rozpoznaje wywołania przeciążenia deklarowanie jako ostatni argument|  
|---|---|  
|Brak wartości (pominięty argument)|`Optional`|  
|pojedynczą wartość|`Optional`|  
|Dwie lub więcej wartości w postaci listy rozdzielanej przecinkami|`ParamArray`|  
|Tablica o dowolnej długości (w tym pusta tablica)|`ParamArray`|  
  
## <a name="see-also"></a>Zobacz też  
 [Parametry opcjonalne](./optional-parameters.md)  
 [Tablice parametrów](./parameter-arrays.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)  
 [Instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Instrukcje: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)  
 [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Metody rozszerzeń](./extension-methods.md)
