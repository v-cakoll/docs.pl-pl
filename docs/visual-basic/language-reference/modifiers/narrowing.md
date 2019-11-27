---
title: Narrowing
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
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351473"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Wskazuje, że Operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może nie być w stanie przechowywać niektórych możliwych wartości oryginalnej klasy lub struktury.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Konwertowanie za pomocą słowa kluczowego Narrowing  
 Procedura konwersji musi określać `Public Shared` oprócz `Narrowing`.  
  
 Konwersje wąskie nie zawsze kończą się powodzeniem w czasie wykonywania i mogą kończyć się niepowodzeniem lub spowodować utratę danych. Przykłady `Long` do `Integer`, `String` do `Date`i typ podstawowy dla typu pochodnego. Ta ostatnia konwersja jest zawężana, ponieważ typ podstawowy może nie zawierać wszystkich elementów członkowskich typu pochodnego, w związku z czym nie jest wystąpieniem typu pochodnego.  
  
 Jeśli `Option Strict` jest `On`, kod zużywający musi używać `CType` dla wszystkich konwersji zawężających.  
  
 W tym kontekście można użyć słowa kluczowego `Narrowing`:  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
