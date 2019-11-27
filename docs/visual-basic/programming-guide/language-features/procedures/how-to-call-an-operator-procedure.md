---
title: 'Porady: wywoływanie procedury operatora'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: a685be7cc3b346b271413e2c29faae5a839313f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340245"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Porady: wywoływanie procedury operatora (Visual Basic)
Wywoływanie procedury operatora przy użyciu symbolu operatora w wyrażeniu. W przypadku operatora konwersji należy wywołać [funkcję CType](../../../../visual-basic/language-reference/functions/ctype-function.md) , aby przekonwertować wartość z jednego typu danych na inny.  
  
 Procedury operatorów nie są jawnie wywoływane. Wystarczy użyć operatora lub funkcji `CType` w instrukcji przypisania lub wyrażeniu, tak samo jak zwykle korzystasz z operatora. Visual Basic wykonuje wywołanie procedury operatora.  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywane *przeciążeniem* operatora.  
  
### <a name="to-call-an-operator-procedure"></a>Aby wywołać procedurę operatora  
  
1. Użyj symbolu operatora w wyrażeniu w zwykły sposób.  
  
2. Upewnij się, że typy danych argumentów operacji są odpowiednie dla operatora i w prawidłowej kolejności.  
  
3. Operator uczestniczy w wartości wyrażenia zgodnie z oczekiwaniami.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Aby wywołać procedurę operatora konwersji  
  
1. Użyj `CType` wewnątrz wyrażenia.  
  
2. Upewnij się, że typy danych argumentów operacji są odpowiednie dla konwersji, i w odpowiedniej kolejności.  
  
3. `CType` wywołuje procedurę operatora konwersji i zwraca przekonwertowaną wartość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwie <xref:System.TimeSpan> struktur, dodaje je razem i zapisuje wynik w trzeciej strukturze <xref:System.TimeSpan>. Struktura <xref:System.TimeSpan> definiuje procedury operatora, aby przeciążać kilka standardowych operatorów.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Ponieważ <xref:System.TimeSpan> przeciążać standardowego operatora `+`, poprzedni przykład wywołuje procedurę operatora podczas obliczania wartości `combinedSpan`.  
  
 Aby zapoznać się z przykładem wywoływania procedury operatora konwersacji, zobacz [How to: use a Class, który definiuje operatory](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Upewnij się, że używana Klasa lub struktura definiuje operatora, którego chcesz użyć.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: definiowanie operatora](./how-to-define-an-operator.md)
- [Instrukcje: definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)
- [Operator, instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
