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
ms.openlocfilehash: 54a18d0cc10e42829b48b0ef75bb77ab0d47b45f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Oznacza to, że operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może nie posiadać pewnych możliwych wartości oryginalnej klasy lub struktury.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Konwertowanie z zawężającej — słowo kluczowe  
 Należy określić procedury konwersji `Public Shared` oprócz `Narrowing`.  
  
 Zawężanie konwersji nie zawsze pomyślnie w czasie wykonywania i może się nie powieść lub pociągnąć za sobą utraty danych. Przykłady `Long` do `Integer`, `String` do `Date`oraz typem bazowym typu pochodnego. Ta konwersja ostatniego jest zawężenie, ponieważ typ podstawowy nie może zawierać wszystkie elementy członkowskie typu pochodnego i w związku z tym nie jest wystąpieniem typu pochodnego.  
  
 Jeśli `Option Strict` jest `On`, wykorzystywanie kodu musi używać `CType` dla wszystkich konwersji zawężającej.  
  
 Słowa kluczowego `Narrowing` można użyć w tym kontekście:  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
