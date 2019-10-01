---
title: If — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 244c0598c65ba691decc09c36293799571211a40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701155"
---
# <a name="if-operator-visual-basic"></a>If — Operator (Visual Basic)
Używa oceny krótkiego obwodu do warunkowego zwrócenia jednej z dwóch wartości. Operator `If` może być wywoływany z trzema argumentami lub z dwoma argumentami.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>Operator if wywoływany z trzema argumentami  
 Gdy `If` jest wywoływana przy użyciu trzech argumentów, pierwszy argument musi być obliczany do wartości, która może być rzutowana jako `Boolean`. Wartość `Boolean` określi, które z pozostałych dwóch argumentów są oceniane i zwracane. Poniższa lista ma zastosowanie tylko wtedy, gdy operator `If` jest wywoływany przy użyciu trzech argumentów.  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`argument1`|Wymagany. `Boolean`., Określa, które z innych argumentów należy obliczyć i zwrócić.|  
|`argument2`|Wymagany. `Object`., Obliczany i zwracany, jeśli `argument1` szacuje się na `True`.|  
|`argument3`|Wymagany. `Object`., Obliczany i zwracany, jeśli `argument1` szacuje się do `False` lub jeśli `argument1` to zmienna [null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean`, która zwraca wartość [Nothing](../../../visual-basic/language-reference/nothing.md).|  
  
 Operator `If` wywoływany z trzema argumentami działa jak funkcja `IIf`, z tą różnicą, że używa oceny krótkiego obwodu. Funkcja `IIf` zawsze oblicza wszystkie trzy z jej argumentów, natomiast operator `If`, który ma trzy argumenty, szacuje tylko dwa z nich. Zostanie obliczony pierwszy argument `If`, a wynik jest rzutowany jako wartość `Boolean`, `True` lub `False`. Jeśli wartość jest `True`, zostanie obliczone `argument2` i zostanie zwrócona wartość, ale `argument3` nie jest oceniane. Jeśli wartość wyrażenia `Boolean` jest `False`, `argument3` jest oceniana i zwracana jest jego wartość, ale `argument2` nie jest szacowana. Poniższe przykłady ilustrują użycie `If`, gdy są używane trzy argumenty:  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 Poniższy przykład ilustruje wartość oceny krótkiego obwodu. Przykład pokazuje dwie próby podzielenia zmiennej `number` według zmiennej `divisor`, z wyjątkiem sytuacji, gdy `divisor` wynosi zero. W takim przypadku należy zwrócić wartość 0 i nie należy podejmować żadnych prób w celu przeprowadzenia podziału, ponieważ może to wynikać z błędu w czasie wykonywania. Ponieważ wyrażenie `If` używa oceny krótkiego obwodu, ocenia drugi lub trzeci argument, w zależności od wartości pierwszego argumentu. Jeśli pierwszy argument ma wartość true, dzielnik nie jest zerem i jest bezpiecznie do obliczenia drugiego argumentu i przeprowadzenia dzielenia. Jeśli pierwszy argument ma wartość false, oceniany jest tylko trzeci argument i zwracana jest wartość 0. W związku z tym, gdy dzielnik ma wartość 0, nie jest podejmowana żadna próba wykonania dzielenia i brak wyników błędu. Jednak ponieważ `IIf` nie używa oceny krótkiego obwodu, drugi argument jest obliczany nawet wtedy, gdy pierwszy argument ma wartość false. Powoduje to błąd dzielenia przez zero w czasie wykonywania.  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a>Operator if wywoływany z dwoma argumentami  
 Pierwszy argument `If` może zostać pominięty. Umożliwia to wywoływanie operatora przy użyciu tylko dwóch argumentów. Poniższa lista ma zastosowanie tylko wtedy, gdy operator `If` jest wywoływany z dwoma argumentami.  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`argument2`|Wymagany. `Object`., Musi być typem referencyjnym lub dopuszczającym wartość null. Obliczany i zwracany, gdy oblicza wartość inną niż `Nothing`.|  
|`argument3`|Wymagany. `Object`., Obliczany i zwracany, jeśli `argument2` szacuje się na `Nothing`.|  
  
 Po pominięciu argumentu `Boolean` pierwszy argument musi być odwołaniem lub typem dopuszczającym wartość null. Jeśli pierwszy argument szacuje się `Nothing`, zwracana jest wartość drugiego argumentu. We wszystkich innych przypadkach zwracana jest wartość pierwszego argumentu. Poniższy przykład ilustruje sposób działania tej oceny.  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Typy wartości dopuszczających wartości null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
