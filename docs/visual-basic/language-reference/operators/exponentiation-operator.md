---
title: "^ — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>^ — Operator (Visual Basic)
Podnosi liczbę do potęgi równej innej liczbie.  
  
## <a name="syntax"></a>Składnia  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a>Części  
 `number`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
 `exponent`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="result"></a>Wynik  
 Wynik jest `number` podniesionej do potęgi równej `exponent`, zawsze jako `Double` wartość.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 `Double`. Argumenty operacji dowolnego innego typu są konwertowane na `Double`.  
  
## <a name="remarks"></a>Uwagi  
 Visual Basic zawsze przeprowadza potęgowania w [— typ danych Double](../../../visual-basic/language-reference/data-types/double-data-type.md).  
  
 Wartość `exponent` może być ułamkową ujemne lub oba.  
  
 Gdy więcej niż jeden potęgowania odbywa się w jednym wyrażeniu `^` operator jest oceniane, ponieważ napotkano od lewej do prawej.  
  
> [!NOTE]
>  `^` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `^` operatora, aby podnieść liczbę do potęgi wykładnik. Wynik jest pierwszym argumentem podniesionej do potęgi drugiego.  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 Powyższy przykład tworzy następujące wyniki:  
  
 `exp1`ma ustawioną wartość 4 (kwadrat 2).  
  
 `exp2`ustawiono 19683 (3 sześcian, następnie tę wartość do sześcianu).  
  
 `exp3`ustawiono-125 (-5 do sześcianu).  
  
 `exp4`ustawiono 625 (-5 do potęgi czwarty).  
  
 `exp5`wynosi 2 (główny modułu 8).  
  
 `exp6`wynosi 0,5 (podzielona przez główny modułu 8 1.0).  
  
 Należy zwrócić uwagę znaczenie nawiasów w wyrażeniach w poprzednim przykładzie. Z powodu *kolejność*, Visual Basic zazwyczaj wykonuje `^` operator przed innych, nawet jednoargumentowego `–` operatora. Jeśli `exp4` i `exp6` został wyliczony bez nawiasów, czy zostały utworzone następujące wyniki:  
  
 `exp4 = -5 ^ 4`oblicza — (5 do potęgi czwarty), co mogłoby spowodować-625.  
  
 `exp6 = 8 ^ -1.0 / 3.0`oblicza (od 8 do potęgi-1 lub 0,125) podzielony przez 3.0, co spowoduje 0.041666666666666666666666666666667.  
  
## <a name="see-also"></a>Zobacz też  
 [^ = — Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
