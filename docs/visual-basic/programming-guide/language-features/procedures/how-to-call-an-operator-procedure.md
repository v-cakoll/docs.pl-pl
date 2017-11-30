---
title: "Porady: wywoływanie procedury operatora (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0abff0a81ebcdacb59b69d0c307bb4aa219906c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Porady: wywoływanie procedury operatora (Visual Basic)
Za pomocą symbol operatora w wyrażeniu jest wywoływanie procedury operatora. W przypadku operatora konwersji, należy wywołać [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) można przekonwertować wartości z jednego typu danych.  
  
 Procedury operatorów nie zostanie jawnie wywołana. Po prostu użyć operatora, lub `CType` funkcji w instrukcji przypisania lub wyrażenie, tak samo zwykle użycie operatora. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]wykonuje wywołanie procedury operatora.  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywany *przeładowanie* operatora.  
  
### <a name="to-call-an-operator-procedure"></a>Wywoływanie procedury operatora  
  
1.  Symbol operatora należy używać w wyrażeniach w zwykły sposób.  
  
2.  Upewnij się, że typy danych argumenty operacji są odpowiednie dla operatora i we właściwej kolejności.  
  
3.  Operator przyczynia się do wartości wyrażenia zgodnie z oczekiwaniami.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Wywoływanie procedury operatora konwersji  
  
1.  Użyj `CType` wewnątrz wyrażenia.  
  
2.  Upewnij się, że typy danych argumenty operacji są odpowiednie do konwersji, a w odpowiedniej kolejności.  
  
3.  `CType`wywołuje procedurę operatora konwersji i zwraca wartość przekonwertowana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa <xref:System.TimeSpan> struktury, dodaje je ze sobą i zapisuje wynik w innej <xref:System.TimeSpan> struktury. <xref:System.TimeSpan> Struktury definiuje operator procedury przeciążenia kilka standardowych operatorów.  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 Ponieważ <xref:System.TimeSpan> overloads standardowego `+` operatora, poprzedni przykład wywołuje procedurę operatora podczas obliczania wartości `combinedSpan`.  
  
 Przykład wywoływanie procedury operatora konwersacji, zobacz [porady: używanie klasy tego definiuje operatory](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Upewnij się, że klasy lub struktury, którego używasz definiuje operator, który ma być używany.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury operatorów](./operator-procedures.md)  
 [Porady: Definiowanie operatora](./how-to-define-an-operator.md)  
 [Porady: Definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)  
 [Operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Rozszerzanie](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Zawężanie](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure — instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Porady: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
