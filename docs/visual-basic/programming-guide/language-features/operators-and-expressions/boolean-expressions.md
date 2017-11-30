---
title: "Wyrażenia logiczne (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 48071c6833f9841fa42311dda59d6959c0645ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-expressions-visual-basic"></a>Wyrażenia logiczne (Visual Basic)
A *wyrażenie warunkowe* wyrażenie obliczane do wartości [— typ danych logicznych](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` lub `False`. `Boolean`wyrażenia może potrwać kilka formularzy. Najprostszą jest bezpośrednie porównanie wartości `Boolean` zmienną `Boolean` literal, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a>Dwa znaczenie = — Operator  
 Zwróć uwagę, że w instrukcji przypisania `newCustomer = True` wygląda tak samo jak wyrażenia w poprzednim przykładzie, ale wykonuje różne funkcje i jest używane w inny sposób. W powyższym przykładzie wyrażenie `newCustomer = True` reprezentuje wartość logiczną i `=` logowania jest interpretowana jako operator porównania. W instrukcji autonomicznej `=` logowania jest interpretowana jako operatora przypisania i przypisuje wartość prawej strony, aby zmienna po lewej stronie. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) i [instrukcje](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operatory porównania  
 Operatory porównania, takich jak `=`, `<`, `>`, `<>`, `<=`, i `>=` utworzyć na podstawie porównania ilości wyrażenie po lewej stronie operatora wyrażenie po prawej stronie wyrażenia logiczne operator i oceny wynik w postaci `True` lub `False`. Ilustruje to poniższy przykład.  
  
 `42 < 81`  
  
 Ponieważ 42 jest mniejsza niż 81, wyrażenia logicznego w poprzednim przykładzie daje w wyniku `True`. Aby uzyskać więcej informacji na ten rodzaj wyrażenia, zobacz [porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operatory porównania w połączeniu z operatorami logicznymi  
 Przy użyciu operatorów logicznych w celu utworzenia bardziej złożonych wyrażeń logicznych można łączyć wyrażeniach porównania. W poniższym przykładzie pokazano użycie operatory porównania w połączeniu z operatorem logicznym.  
  
 `x > y And x < 1000`  
  
 W powyższym przykładzie wartość wyrażenia zależy od wartości wyrażenia na każdej stronie `And` operatora. Jeśli oba wyrażenia są `True`, a następnie daje w wyniku wyrażenia `True`. Jeśli jedno z wyrażeń ma `False`, a następnie całe wyrażenie daje w wyniku `False`.  
  
## <a name="short-circuiting-operators"></a>Zwarcie operatory  
 Operatory logiczne `AndAlso` i `OrElse` zachowują znany jako *zwarcie*. Short-circuiting operator najpierw sprawdza Lewy argument operacji. Jeśli lewy operand określa wartość wyrażenia, wykonywania programu będzie kontynuowane bez obliczania prawe wyrażenie. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 W powyższym przykładzie operator oblicza wyrażenie po lewej stronie, `45 < 12`. Ponieważ lewe wyrażenie daje w wyniku `False`, całego wyrażenia logicznego musi być `False`. Wykonanie programu, w związku z tym pomija wykonywanie kodu w `If` bez oceny prawe wyrażenie `testFunction(3)`. W tym przykładzie nie wywołuje `testFunction()` ponieważ po lewej stronie wyrażenia falsifies całego wyrażenia.  
  
 Podobnie jeśli wyrażenie po lewej stronie wyrażenia logicznego przy użyciu `OrElse` daje w wyniku `True`, wykonanie przechodzi do następnego wiersza kodu bez sprawdzania prawe wyrażenie, ponieważ wyrażenie po lewej stronie już został zweryfikowany całą wyrażenie.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Porównanie z operatorami Circuiting krótki  
 Z kolei obu stronach operatora logicznego są oceniane po operatorów logicznych `And` i `Or` są używane. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 Poprzednim przykładzie wywołuje `testFunction()` nawet po lewej stronie wyrażenia `False`.  
  
## <a name="parenthetical-expressions"></a>Wyrażenia w nawiasach  
 Można użyć nawiasów określających kolejność obliczania wyrażeń logicznych. Najpierw należy ocenić wyrażenia ujętego w nawiasy. Wiele poziomów zagnieżdżenia pierwszeństwo jest przyznawane najbardziej głęboko zagnieżdżone wyrażenia. Ocena będzie kontynuowana, zgodnie z regułami kolejność wykonywania działań w obrębie nawiasów. Aby uzyskać więcej informacji, zobacz [kolejność wykonywania w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Instrukcje](../../../../visual-basic/programming-guide/language-features/statements.md)  
 [Operatory porównania](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Boolean — typ danych](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
