---
title: "TypeOf — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51bd2af7af28aa229fa62770c5b92d31e461333b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 Wymagany. Wyrażenie, którego wynikiem jest typ referencyjny.  
  
 `typename`  
 Wymagany. Nazwa typu żadnych danych.  
  
## <a name="remarks"></a>Uwagi  
 `TypeOf` Operator określa, czy typ środowiska wykonawczego `objectexpression` jest zgodny z `typename`. Zgodność zależy od typu kategorii `typename`. W poniższej tabeli przedstawiono, jak ustalona zgodności.  
  
|Typ kategorii`typename`|Kryterium zgodności|  
|---------------------------------|-----------------------------|  
|Class|`objectexpression`jest typu `typename` lub dziedziczy`typename`|  
|Struktura|`objectexpression`jest typu`typename`|  
|Interface|`objectexpression`implementuje `typename` lub dziedziczy z klasy, która implementuje`typename`|  
  
 Jeśli typ środowiska wykonawczego `objectexpression` spełnia kryterium zgodności `result` jest `True`. W przeciwnym razie `result` jest `False`.  Jeśli `objectexpression` ma wartość null, następnie `TypeOf`... `Is` zwraca `False`, i... `IsNot` zwraca `True`.  
  
 `TypeOf`zawsze jest używany z `Is` — słowo kluczowe do skonstruowania `TypeOf`... `Is` wyrażenia, lub z `IsNot` — słowo kluczowe do skonstruowania `TypeOf`... `IsNot` wyrażenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `TypeOf`... `Is` wyrażenia do testowania zgodności typu dwóch obiektów zmienne odwołujące się przy użyciu różnych typów danych.  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 Zmienna `refInteger` ma typ środowiska wykonawczego `Integer`. Jest on zgodny z `Integer` , lecz nie `Double`. Zmienna `refForm` ma typ środowiska wykonawczego <xref:System.Windows.Forms.Form>. Jest on zgodny z <xref:System.Windows.Forms.Form> , ponieważ jego typ, który jest z <xref:System.Windows.Forms.Control> ponieważ <xref:System.Windows.Forms.Form> dziedziczy <xref:System.Windows.Forms.Control>i z <xref:System.ComponentModel.IComponent> ponieważ <xref:System.Windows.Forms.Form> dziedziczy <xref:System.ComponentModel.Component>, który implementuje <xref:System.ComponentModel.IComponent>. Jednak `refForm` nie jest zgodny z <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Zobacz też  
 [Is — Operator](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot — Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
