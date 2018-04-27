---
title: Kolejność wykonywania działań (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d8de9deea84c7f0c11c91b55951cdfc200b017f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="operator-precedence-in-visual-basic"></a>Kolejność wykonywania działań (Visual Basic)
Gdy występują kilka operacji w wyrażeniu, każda część jest oceniane i rozpoznać w ustalonej kolejności o nazwie *kolejność*.  
  
## <a name="precedence-rules"></a>Reguły pierwszeństwa  
 Jeśli wyrażenia zawierają operatory z więcej niż jedną kategorię, są one oceniane zgodnie z następującymi zasadami:  
  
-   Operatory arytmetyczne i łączenia mają kolejność pierwszeństwa opisane w poniższej sekcji, a wszystkie mają wyższy priorytet niż porównanie logiczne i operatory bitowe.  
  
-   Wszystkie operatory porównania ma taki sam priorytet i wszystkie mają wyższy priorytet niż operatory logiczne i bitowe, ale niższy priorytet niż operatory arytmetyczne i łączenia.  
  
-   Operatory logiczne i bitowe mają kolejność pierwszeństwa opisane w poniższej sekcji, a wszystkie mieć niższego pierwszeństwa niż arytmetyczne, łączenie i operatory porównania.  
  
-   Operatory z równy priorytet są wykonywane od lewej do prawej w kolejności, w jakiej występują w wyrażeniu.  
  
## <a name="precedence-order"></a>Kolejność pierwszeństwa  
 Operatory są oceniane w następującej kolejności:  
  
### <a name="await-operator"></a>Await — Operator  
 await  
  
### <a name="arithmetic-and-concatenation-operators"></a>Operacje arytmetyczne i operatory łączenia  
 Zapis wykładniczy (`^`)  
  
 Jednoargumentowy tożsamości i negacji (`+`, `–`)  
  
 Mnożenia i dzielenia liczb zmiennoprzecinkowych (`*`, `/`)  
  
 Dzielenie liczby całkowitej (`\`)  
  
 Arytmetycznego modulo (`Mod`)  
  
 Dodawanie i odejmowanie (`+`, `–`)  
  
 Łączenie ciągów (`&`)  
  
 Przesunięcia bitowego arytmetyczne (`<<`, `>>`)  
  
### <a name="comparison-operators"></a>Operatory porównania  
 Wszystkie operatory porównania (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)  
  
### <a name="logical-and-bitwise-operators"></a>Operatory logiczne i bitowe  
 Negacja (`Not`)  
  
 Razem (`And`, `AndAlso`)  
  
 Wraz z wartościami granicznymi rozłączenia (`Or`, `OrElse`)  
  
 Wyłączny rozłączenia (`Xor`)  
  
### <a name="comments"></a>Komentarze  
 `=` Operator jest tylko operator porównania, nie operator przypisania.  
  
 Operator łączenia ciągu (`&`) nie jest operator arytmetyczny, ale w pierwszeństwo jest zgrupowana za pomocą operatorów arytmetycznych.  
  
 `Is` i `IsNot` operatory są operatory porównania odwołanie do obiektu. Porównuje wartości dwa obiekty; Sprawdź one tylko do określenia, czy dwie zmienne obiektu odwoływać się do tego samego wystąpienia obiektu.  
  
## <a name="associativity"></a>Łączność  
 Gdy operatory równy priorytet występować razem w wyrażeniu, na przykład mnożenia i dzielenia, kompilator oblicza każdej operacji zgodnie z jego napotka od lewej do prawej. Ilustruje to poniższy przykład.  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 Pierwsze wyrażenie daje w wyniku dzielenia 96 / 8 (co powoduje 12), a następnie dzielenia 12 / 4, co prowadzi do trzech. Ponieważ kompilator daje w wyniku operacji `n1` od lewej do prawej, oceny jest taki sam jawnie określić kolejności `n2`. Zarówno `n1` i `n2` dawać wynik trzech. Z kolei `n3` ma wynik 48, ponieważ nawiasy wymusić kompilator, aby ocenić 8 / 4 pierwszy.  
  
 Ze względu na to zachowanie operatory są określane jako *pozostałych asocjacyjnej* w języku Visual Basic.  
  
## <a name="overriding-precedence-and-associativity"></a>Zastępowanie priorytet i łączność  
 Aby wymusić niektórych części wyrażenia ma zostać obliczone przed pozostałymi można Użyj nawiasów. To zastąpienie jednocześnie kolejność pierwszeństwa, jak i kojarzenie po lewej stronie. Visual Basic zawsze wykonuje operacje, które są ujęte w nawiasy przed elementami poza. Jednak w obrębie nawiasów przechowuje zwykłej priorytet i łączność, chyba że Użyj nawiasów w nawiasach. Ilustruje to poniższy przykład.  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [=, operator](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Like, operator](../../../visual-basic/language-reference/operators/like-operator.md)  
 [TypeOf, operator](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Await, operator](../../../visual-basic/language-reference/operators/await-operator.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
