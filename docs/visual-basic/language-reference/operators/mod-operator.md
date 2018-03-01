---
title: "Mod — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5464b57c993e5703c09529b527a7bc714e045870
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mod-operator-visual-basic"></a>Mod — Operator (Visual Basic)
Dzieli dwie liczby i zwraca tylko resztę.  
  
## <a name="syntax"></a>Składnia  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>Części  
 `number1`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
 `number2`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe. Obejmuje to typy bez znaku i zmiennoprzecinkowych i `Decimal`.  
  
## <a name="result"></a>Wynik  
 Wynik jest resztę po `number1` przez `number2`. Na przykład, wyrażenie `14 Mod 4` ocenia się na 2.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli dowolny `number1` lub `number2` jest wartość zmiennoprzecinkową zmiennoprzecinkowe pozostałej części podziału jest zwracany. Typ danych wyniku to najmniejsza typu danych, który może posiadać wszystkie możliwe wartości wynikających z dzielenia z typami danych `number1` i `number2`.  
  
 Jeśli `number1` lub `number2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.  
  
 Operatory powiązane są następujące:  
  
-   [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) Zwraca iloraz liczbą całkowitą z dzielenia. Na przykład, wyrażenie `14 \ 4` daje w wyniku 3.  
  
-   [/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) Zwraca iloraz pełne, łącznie z pozostałą, jako liczba zmiennoprzecinkowa. Na przykład, wyrażenie `14 / 4` daje w wyniku 3.5.  
  
## <a name="attempted-division-by-zero"></a>Próba dzielenia przez Zero  
 Jeśli `number2` daje w wyniku wartość zero, zachowanie `Mod` operator zależy od typu danych operandów. Zgłasza całkowitą dzielenia <xref:System.DivideByZeroException> wyjątku. Zwraca dzielenia liczb zmiennoprzecinkowych <xref:System.Double.NaN>.  
  
## <a name="equivalent-formula"></a>Formuła równoważne  
 Wyrażenie `a Mod b` odpowiada jednej z następujących formuły:  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>Zmiennoprzecinkowe błędu  
 Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne reprezentacji w pamięci. Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i `Mod` operatora. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `Mod` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowania. Jeśli kod ma zastosowanie `Mod` do wystąpienia klasy lub struktury, która obejmuje takie przeciążenia, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Mod` operator do dzielenia dwie liczby i zwraca tylko resztę. Jeśli liczba zmiennoprzecinkowa, albo liczbą wynik jest reprezentujący Pozostała liczba zmiennoprzecinkowa.  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano ryzyko błędu argumentów operacji zmiennoprzecinkowej. W pierwszej instrukcji argumenty operacji są `Double`, i 0,2 jest nieskończenie identycznych ułamek binarnego z wartością przechowywaną 0.20000000000000001. W drugim instrukcji literału znaku typu `D` wymusza oba argumenty do `Decimal`, i 0,2 ma reprezentację dokładne.  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
