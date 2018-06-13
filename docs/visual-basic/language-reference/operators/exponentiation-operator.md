---
title: ^ — Operator (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 426c3e9913dadda1091f4ba53c66c6b65e40e768
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604448"
---
# <a name="-operator-visual-basic"></a>^ — Operator (Visual Basic)
Podnosi liczbę do potęgi równej innej liczbie.  
  
## <a name="syntax"></a>Składnia  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a>Części  
 `number`  
 Wymagana. Dowolne wyrażenie liczbowe.  
  
 `exponent`  
 Wymagana. Dowolne wyrażenie liczbowe.  
  
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
  
 `exp1` ma ustawioną wartość 4 (kwadrat 2).  
  
 `exp2` ustawiono 19683 (3 sześcian, następnie tę wartość do sześcianu).  
  
 `exp3` ustawiono-125 (-5 do sześcianu).  
  
 `exp4` ustawiono 625 (-5 do potęgi czwarty).  
  
 `exp5` wynosi 2 (główny modułu 8).  
  
 `exp6` wynosi 0,5 (podzielona przez główny modułu 8 1.0).  
  
 Należy zwrócić uwagę znaczenie nawiasów w wyrażeniach w poprzednim przykładzie. Z powodu *kolejność*, Visual Basic zazwyczaj wykonuje `^` operator przed innych, nawet jednoargumentowego `–` operatora. Jeśli `exp4` i `exp6` został wyliczony bez nawiasów, czy zostały utworzone następujące wyniki:  
  
 `exp4 = -5 ^ 4` oblicza — (5 do potęgi czwarty), co mogłoby spowodować-625.  
  
 `exp6 = 8 ^ -1.0 / 3.0` oblicza (od 8 do potęgi-1 lub 0,125) podzielony przez 3.0, co spowoduje 0.041666666666666666666666666666667.  
  
## <a name="see-also"></a>Zobacz też  
 [^=, operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
