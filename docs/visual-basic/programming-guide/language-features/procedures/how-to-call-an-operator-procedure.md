---
title: 'Porady: wywoływanie procedury operatora (Visual Basic)'
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
ms.openlocfilehash: b1dc4477daa4ceb9dfc6a9a6ab3f041e68011acd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Porady: wywoływanie procedury operatora (Visual Basic)
Za pomocą symbol operatora w wyrażeniu jest wywoływanie procedury operatora. W przypadku operatora konwersji, należy wywołać [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) można przekonwertować wartości z jednego typu danych.  
  
 Procedury operatorów nie zostanie jawnie wywołana. Po prostu użyć operatora, lub `CType` funkcji w instrukcji przypisania lub wyrażenie, tak samo zwykle użycie operatora. Visual Basic sprawia, że wywołanie procedury operatora.  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywany *przeładowanie* operatora.  
  
### <a name="to-call-an-operator-procedure"></a>Wywoływanie procedury operatora  
  
1.  Symbol operatora należy używać w wyrażeniach w zwykły sposób.  
  
2.  Upewnij się, że typy danych argumenty operacji są odpowiednie dla operatora i we właściwej kolejności.  
  
3.  Operator przyczynia się do wartości wyrażenia zgodnie z oczekiwaniami.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Wywoływanie procedury operatora konwersji  
  
1.  Użyj `CType` wewnątrz wyrażenia.  
  
2.  Upewnij się, że typy danych argumenty operacji są odpowiednie do konwersji, a w odpowiedniej kolejności.  
  
3.  `CType` wywołuje procedurę operatora konwersji i zwraca wartość przekonwertowana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa <xref:System.TimeSpan> struktury, dodaje je ze sobą i zapisuje wynik w innej <xref:System.TimeSpan> struktury. <xref:System.TimeSpan> Struktury definiuje operator procedury przeciążenia kilka standardowych operatorów.  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 Ponieważ <xref:System.TimeSpan> overloads standardowego `+` operatora, poprzedni przykład wywołuje procedurę operatora podczas obliczania wartości `combinedSpan`.  
  
 Przykład wywoływanie procedury operatora konwersacji, zobacz [porady: używanie klasy tego definiuje operatory](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Upewnij się, że klasy lub struktury, którego używasz definiuje operator, który ma być używany.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury operatorów](./operator-procedures.md)  
 [Instrukcje: definiowanie operatora](./how-to-define-an-operator.md)  
 [Instrukcje: definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)  
 [Operator, instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
