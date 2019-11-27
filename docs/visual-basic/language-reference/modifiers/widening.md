---
title: Widening
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
ms.openlocfilehash: 1c9aa78549ca6e41c9fe54c12e0aaec8e7cc30cb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347832"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
Wskazuje, że Operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może zawierać wszystkie możliwe wartości oryginalnej klasy lub struktury.  
  
## <a name="converting-with-the-widening-keyword"></a>Konwertowanie za pomocą słowa kluczowego rozszerzającego  
 Procedura konwersji musi określać `Public Shared` oprócz `Widening`.  
  
 Rozszerzanie konwersji zawsze powiedzie się w czasie wykonywania i nigdy nie powiąże się z utratą danych. Przykłady `Single` do `Double`, `Char` do `String`i typ pochodny do jego typu podstawowego. Ta ostatnia konwersja jest rozszerzana, ponieważ typ pochodny zawiera wszystkie elementy członkowskie typu podstawowego i w związku z tym jest wystąpieniem typu podstawowego.  
  
 Kod zużywający nie musi używać `CType` do rozszerzania konwersji nawet wtedy, gdy `Option Strict` jest `On`.  
  
 W tym kontekście można użyć słowa kluczowego `Widening`:  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Aby zapoznać się z przykładami definicji rozszerzania i zawężania operatorów konwersji, zobacz [How to: define Operator konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Zobacz także

- [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Instrukcje: definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
