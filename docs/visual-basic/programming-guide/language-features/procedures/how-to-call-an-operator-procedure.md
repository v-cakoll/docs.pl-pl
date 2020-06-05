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
ms.openlocfilehash: fa2bc5417b8b917ff48502a5bd0a4daa21fab67e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388572"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Porady: wywoływanie procedury operatora (Visual Basic)
Wywoływanie procedury operatora przy użyciu symbolu operatora w wyrażeniu. W przypadku operatora konwersji należy wywołać [funkcję CType](../../../language-reference/functions/ctype-function.md) , aby przekonwertować wartość z jednego typu danych na inny.  
  
 Procedury operatorów nie są jawnie wywoływane. Wystarczy użyć operatora lub `CType` funkcji w instrukcji przypisania lub wyrażeniu, tak samo jak zwykle korzystasz z operatora. Visual Basic wykonuje wywołanie procedury operatora.  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywane *przeciążeniem* operatora.  
  
### <a name="to-call-an-operator-procedure"></a>Aby wywołać procedurę operatora  
  
1. Użyj symbolu operatora w wyrażeniu w zwykły sposób.  
  
2. Upewnij się, że typy danych argumentów operacji są odpowiednie dla operatora i w prawidłowej kolejności.  
  
3. Operator uczestniczy w wartości wyrażenia zgodnie z oczekiwaniami.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Aby wywołać procedurę operatora konwersji  
  
1. Użyj `CType` wewnątrz wyrażenia.  
  
2. Upewnij się, że typy danych argumentów operacji są odpowiednie dla konwersji, i w odpowiedniej kolejności.  
  
3. `CType`wywołuje procedurę operatora konwersji i zwraca przekonwertowaną wartość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwie <xref:System.TimeSpan> struktury, dodaje je razem i zapisuje wynik w trzeciej <xref:System.TimeSpan> strukturze. <xref:System.TimeSpan>Struktura definiuje procedury operatora, aby przeciążać kilka standardowych operatorów.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Ponieważ <xref:System.TimeSpan> przeciążenia operatora standardowego `+` , poprzedni przykład wywołuje procedurę operatora podczas obliczania wartości `combinedSpan` .  
  
 Aby zapoznać się z przykładem wywoływania procedury operatora konwersacji, zobacz [How to: use a Class, który definiuje operatory](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Upewnij się, że używana Klasa lub struktura definiuje operatora, którego chcesz użyć.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: definiowanie operatora](./how-to-define-an-operator.md)
- [Instrukcje: definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)
- [Operator — Instrukcja](../../../language-reference/statements/operator-statement.md)
- [Widening](../../../language-reference/modifiers/widening.md)
- [Narrowing](../../../language-reference/modifiers/narrowing.md)
- [Structure — Instrukcja](../../../language-reference/statements/structure-statement.md)
- [Instrukcje: Deklarowanie struktury](../data-types/how-to-declare-a-structure.md)
- [Konwersje jawne i niejawne](../data-types/implicit-and-explicit-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../data-types/widening-and-narrowing-conversions.md)
