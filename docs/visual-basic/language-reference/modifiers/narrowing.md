---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50116c6212e919d4b9b35fc933d80dee14bd4ecf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Oznacza to, że operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może nie posiadać pewnych możliwych wartości oryginalnej klasy lub struktury.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Konwertowanie z zawężającej — słowo kluczowe  
 Należy określić procedury konwersji `Public Shared` oprócz `Narrowing`.  
  
 Zawężanie konwersji nie zawsze pomyślnie w czasie wykonywania i może się nie powieść lub pociągnąć za sobą utraty danych. Przykłady `Long` do `Integer`, `String` do `Date`oraz typem bazowym typu pochodnego. Ta konwersja ostatniego jest zawężenie, ponieważ typ podstawowy nie może zawierać wszystkie elementy członkowskie typu pochodnego i w związku z tym nie jest wystąpieniem typu pochodnego.  
  
 Jeśli `Option Strict` jest `On`, wykorzystywanie kodu musi używać `CType` dla wszystkich konwersji zawężającej.  
  
 `Narrowing` Można użyć słowa kluczowego, w tym kontekście:  
  
 [Operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Rozszerzanie](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Porady: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType — funkcja](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
