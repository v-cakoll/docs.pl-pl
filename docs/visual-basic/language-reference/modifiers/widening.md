---
title: Widening (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 2323aa38c81ce4e027f256d0e29c069f7ec77c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595316"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
Oznacza to, że operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może posiadać wszystkie możliwe wartości oryginalnej klasy lub struktury.  
  
## <a name="converting-with-the-widening-keyword"></a>Konwertowanie z rozszerzającą — słowo kluczowe  
 Należy określić procedury konwersji `Public Shared` oprócz `Widening`.  
  
 Rozszerzanie konwersji zawsze pomyślnie w czasie wykonywania i nigdy nie pociągnąć za sobą utraty danych. Przykłady `Single` do `Double`, `Char` do `String`i na jego typ podstawowy typu pochodnego. Ostatni konwersji jest rozszerzenia, ponieważ typ pochodny zawiera wszystkie elementy członkowskie typu podstawowego i w związku z tym jest wystąpieniem typu podstawowego.  
  
 Odbierającą kodu nie trzeba używać `CType` dla rozszerzanie konwersji, nawet jeśli `Option Strict` jest `On`.  
  
 Słowa kluczowego `Widening` można użyć w tym kontekście:  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Na przykład definicje rozszerzanie i zwężanie konwersji operatorów, zobacz [porady: Definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Instrukcje: definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
