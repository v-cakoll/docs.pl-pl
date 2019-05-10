---
title: TypeOf — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: e5cb1ddc130a8b1913f30b0d20d27941005dd9d3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063255"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf — Operator (Visual Basic)
Sprawdza, czy typ środowiska uruchomieniowego, wynikiem wyrażenia jest typ zgodny z określonym typem.
  
## <a name="syntax"></a>Składnia  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Zwracane. A `Boolean` wartość.  
  
 `objectexpression`  
 Wymagana. Dowolne wyrażenie, którego wynikiem jest typem referencyjnym.  
  
 `typename`  
 Wymagana. Nazwa typu żadnych danych.  
  
## <a name="remarks"></a>Uwagi  
 `TypeOf` Operator określa, czy środowiska wykonawczego typu `objectexpression` jest zgodny z `typename`. Zgodność jest zależna od typu kategorii `typename`. W poniższej tabeli przedstawiono, jak jest określana zgodność.  
  
|Typ kategorii `typename`|Kryterium zgodności|  
|---------------------------------|-----------------------------|  
|Class|`objectexpression` Typ jest `typename` lub dziedziczy z `typename`|  
|Struktura|`objectexpression` jest typu `typename`|  
|Interface|`objectexpression` implementuje `typename` lub dziedziczy z klasy, która implementuje `typename`|  
  
 Jeśli typ środowiska wykonawczego `objectexpression` spełnia kryterium zgodności `result` jest `True`. W przeciwnym razie `result` jest `False`.  Jeśli `objectexpression` ma wartość null, następnie `TypeOf`... `Is` zwraca `False`, i... `IsNot` zwraca `True`.  
  
 `TypeOf` zawsze jest używana z `Is` — słowo kluczowe do konstruowania `TypeOf`... `Is` wyrażenie, lub za pomocą `IsNot` — słowo kluczowe do konstruowania `TypeOf`... `IsNot` wyrażenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `TypeOf`... `Is` wyrażeń, które umożliwiają przetestowanie zgodności typu dwóch obiektów zmienne odwołania z różnych typów danych.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 Zmienna `refInteger` ma typ środowiska wykonawczego `Integer`. Jest to zgodne z `Integer` , ale nie z `Double`. Zmienna `refForm` ma typ środowiska wykonawczego <xref:System.Windows.Forms.Form>. Jest to zgodne z <xref:System.Windows.Forms.Form> , ponieważ jego typ, jest z <xref:System.Windows.Forms.Control> ponieważ <xref:System.Windows.Forms.Form> dziedziczy <xref:System.Windows.Forms.Control>i <xref:System.ComponentModel.IComponent> ponieważ <xref:System.Windows.Forms.Form> dziedziczy <xref:System.ComponentModel.Component>, który implementuje <xref:System.ComponentModel.IComponent>. Jednak `refForm` nie jest zgodny z <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Zobacz także

- [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operatory porównania w języku Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
