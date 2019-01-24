---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: bd88c05f16a2027b0367effebef809cb5e5abfe8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617440"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Oznacza to, że operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może nie posiadać pewnych możliwych wartości oryginalnej klasy lub struktury.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Konwertowanie za pomocą słowa kluczowego zawężającej  
 Należy określić procedury konwersji `Public Shared` oprócz `Narrowing`.  
  
 Konwersje zawężające nie zawsze sukces w czasie wykonywania i może zakończyć się niepowodzeniem lub pociągnąć za sobą utratę danych. Należą do nich `Long` do `Integer`, `String` do `Date`, a typ podstawowy typu pochodnego. Ta ostatnia konwersja jest zawężenie, ponieważ typ podstawowy nie może zawierać wszystkie elementy członkowskie w typie pochodnym i dlatego nie jest wystąpieniem typu pochodnego.  
  
 Jeśli `Option Strict` jest `On`, wykorzystywanie kodu należy użyć `CType` dla wszystkich konwersji zawężających.  
  
 Słowa kluczowego `Narrowing` można użyć w tym kontekście:  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Zobacz także
- [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Instrukcje: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
