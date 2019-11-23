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
ms.openlocfilehash: c6028f524a16b836310f0c8d564205244515cdc9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701285"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf — Operator (Visual Basic)
Sprawdza, czy typ środowiska uruchomieniowego wyniku wyrażenia jest zgodny z typem określonego typu.
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Zwracać. Wartość `Boolean`.  
  
 `objectexpression`  
 Wymagana. Dowolne wyrażenie, którego wynikiem jest typ referencyjny.  
  
 `typename`  
 Wymagana. Dowolna nazwa typu danych.  
  
## <a name="remarks"></a>Uwagi  
 Operator `TypeOf` określa, czy typ czasu wykonywania `objectexpression` jest zgodny z `typename`. Zgodność zależy od kategorii typu `typename`. W poniższej tabeli przedstawiono sposób określania zgodności.  
  
|Kategoria typu `typename`|Kryterium zgodności|  
|---------------------------------|-----------------------------|  
|Class|`objectexpression` jest typu `typename` lub dziedziczy po `typename`|  
|Struktura|`objectexpression` jest typu `typename`|  
|Interface|`objectexpression` implementuje `typename` lub dziedziczy z klasy implementującej `typename`|  
  
 Jeśli typ czasu wykonywania `objectexpression` spełnia kryterium zgodności, `result` jest `True`. W przeciwnym razie `result` jest `False`.  Jeśli `objectexpression` ma wartość null, `TypeOf`...`Is` zwraca `False`, a...`IsNot` zwraca `True`.  
  
 `TypeOf` jest zawsze używana ze słowem kluczowym `Is` do konstruowania wyrażenia `TypeOf`...`Is`, lub za pomocą słowa kluczowego `IsNot` do konstruowania wyrażenia `TypeOf`...`IsNot`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono użycie wyrażeń `TypeOf`...`Is` w celu przetestowania zgodności typów dwóch zmiennych odwołań do obiektów z różnymi typami danych.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 Zmienna `refInteger` ma typ `Integer`w czasie wykonywania. Jest on zgodny z `Integer`, ale nie z `Double`. Zmienna `refForm` ma typ <xref:System.Windows.Forms.Form>w czasie wykonywania. Jest on zgodny z <xref:System.Windows.Forms.Form>, ponieważ jest typem, z <xref:System.Windows.Forms.Control>, ponieważ <xref:System.Windows.Forms.Form> dziedziczy z <xref:System.Windows.Forms.Control>i z <xref:System.ComponentModel.IComponent>, ponieważ <xref:System.Windows.Forms.Form> dziedziczy z <xref:System.ComponentModel.Component>, który implementuje <xref:System.ComponentModel.IComponent>. Jednak `refForm` nie jest zgodny z <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Zobacz także

- [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
