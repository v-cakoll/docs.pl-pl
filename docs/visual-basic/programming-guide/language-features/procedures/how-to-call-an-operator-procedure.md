---
title: 'Instrukcje: Wywoływanie procedury operatora (Visual Basic)'
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
ms.openlocfilehash: 46614ad43e7be72c8396f47ba7f5d02185f62827
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837094"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Instrukcje: Wywoływanie procedury operatora (Visual Basic)
Za pomocą symbol operatora w wyrażeniu jest wywoływanie procedury operatora. W przypadku operatora konwersji, należy wywołać [funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md) można przekonwertować wartości z jednego typu danych.  
  
 Procedury operatorów nie zostanie jawnie wywołana. Po prostu użyć operatora, lub `CType` funkcji w instrukcji przypisania lub wyrażenia, taki sam sposób, zwykle używany jest operator. Visual Basic sprawia, że wywołanie procedury operatora.  
  
 Definiowanie operatora dla klasy lub struktury jest również nazywany *przeciążenie* operatora.  
  
### <a name="to-call-an-operator-procedure"></a>Aby wywoływanie procedury operatora  
  
1.  Symbol operatora należy używać w wyrażeniach w zwykły sposób.  
  
2.  Upewnij się, że typy danych argumentów są właściwe dla operatora i w odpowiedniej kolejności.  
  
3.  Operator przyczynia się do wartości wyrażenia, zgodnie z oczekiwaniami.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Aby wywołać procedurę operatora konwersji  
  
1.  Użyj `CType` wewnątrz wyrażenia.  
  
2.  Upewnij się, że typy danych argumentów są odpowiednie, konwersji i w odpowiedniej kolejności.  
  
3.  `CType` wywołuje procedurę operatora konwersji i zwraca wartość przekonwertowana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwie <xref:System.TimeSpan> struktury, dodaje je ze sobą i zapisuje wynik w trzecim <xref:System.TimeSpan> struktury. <xref:System.TimeSpan> Struktury definiuje operator procedury przeciążenia kilka standardowych operatorów.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Ponieważ <xref:System.TimeSpan> przeciążenia standard `+` operatora, poprzedni przykład wywołuje procedury operatora podczas obliczania wartości `combinedSpan`.  
  
 Aby uzyskać przykład wywoływanie procedury operatora konwersacji, zobacz [jak: Używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Upewnij się, że klasy lub struktury, którego używasz, określa operator, który chcesz użyć.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: Definiowanie operatora](./how-to-define-an-operator.md)
- [Instrukcje: Definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)
- [Operator, instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
