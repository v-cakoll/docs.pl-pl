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
ms.openlocfilehash: fe287794423048e993d953c83fc8590a06b7a5e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="typeof-operator-visual-basic"></a>TypeOf — Operator (Visual Basic)
Porównuje zmiennej odwołania do obiektu z typem danych.  
  
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
 Wymagana. Wyrażenie, którego wynikiem jest typ referencyjny.  
  
 `typename`  
 Wymagana. Nazwa typu żadnych danych.  
  
## <a name="remarks"></a>Uwagi  
 `TypeOf` Operator określa, czy typ środowiska wykonawczego `objectexpression` jest zgodny z `typename`. Zgodność zależy od typu kategorii `typename`. W poniższej tabeli przedstawiono, jak ustalona zgodności.  
  
|Typ kategorii `typename`|Kryterium zgodności|  
|---------------------------------|-----------------------------|  
|Class|`objectexpression` jest typu `typename` lub dziedziczy `typename`|  
|Struktura|`objectexpression` jest typu `typename`|  
|Interface|`objectexpression` implementuje `typename` lub dziedziczy z klasy, która implementuje `typename`|  
  
 Jeśli typ środowiska wykonawczego `objectexpression` spełnia kryterium zgodności `result` jest `True`. W przeciwnym razie `result` jest `False`.  Jeśli `objectexpression` ma wartość null, następnie `TypeOf`... `Is` zwraca `False`, i... `IsNot` zwraca `True`.  
  
 `TypeOf` zawsze jest używany z `Is` — słowo kluczowe do skonstruowania `TypeOf`... `Is` wyrażenia, lub z `IsNot` — słowo kluczowe do skonstruowania `TypeOf`... `IsNot` wyrażenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `TypeOf`... `Is` wyrażenia do testowania zgodności typu dwóch obiektów zmienne odwołujące się przy użyciu różnych typów danych.  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 Zmienna `refInteger` ma typ środowiska wykonawczego `Integer`. Jest on zgodny z `Integer` , lecz nie `Double`. Zmienna `refForm` ma typ środowiska wykonawczego <xref:System.Windows.Forms.Form>. Jest on zgodny z <xref:System.Windows.Forms.Form> , ponieważ jego typ, który jest z <xref:System.Windows.Forms.Control> ponieważ <xref:System.Windows.Forms.Form> dziedziczy <xref:System.Windows.Forms.Control>i z <xref:System.ComponentModel.IComponent> ponieważ <xref:System.Windows.Forms.Form> dziedziczy <xref:System.ComponentModel.Component>, który implementuje <xref:System.ComponentModel.IComponent>. Jednak `refForm` nie jest zgodny z <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Zobacz też  
 [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
