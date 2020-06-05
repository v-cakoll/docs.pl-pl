---
title: TypeOf — Operator
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
ms.openlocfilehash: 0cce36073b53442bce63f966f3bd94bd5d70d2a8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406330"
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
 Zwracać. `Boolean`Wartość.  
  
 `objectexpression`  
 Wymagany. Dowolne wyrażenie, którego wynikiem jest typ referencyjny.  
  
 `typename`  
 Wymagany. Dowolna nazwa typu danych.  
  
## <a name="remarks"></a>Uwagi  
 `TypeOf`Operator określa, czy typ czasu wykonywania `objectexpression` jest zgodny z `typename` . Zgodność zależy od kategorii typów `typename` . W poniższej tabeli przedstawiono sposób określania zgodności.  
  
|Kategoria typu`typename`|Kryterium zgodności|  
|---------------------------------|-----------------------------|  
|Klasa|`objectexpression`jest typu `typename` lub dziedziczy po`typename`|  
|Struktura|`objectexpression`jest typu`typename`|  
|Interfejs|`objectexpression`implementuje `typename` lub dziedziczy z klasy implementującej`typename`|  
  
 Jeśli typ czasu wykonywania `objectexpression` spełnia kryteria zgodności, `result` jest `True` . W przeciwnym razie `result` jest `False` .  Jeśli `objectexpression` ma wartość null, `TypeOf` Funkcja... `Is` zwraca wartość `False` , a... `IsNot` zwraca wartość `True` .  
  
 `TypeOf`jest zawsze używana ze `Is` słowem kluczowym w celu skonstruowania `TypeOf` wyrażenia... `Is` lub ze `IsNot` słowem kluczowym służącym do konstruowania `TypeOf` wyrażenia... `IsNot` .  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano `TypeOf` wyrażenia... `Is` do testowania zgodności typów dwóch zmiennych odwołań do obiektów z różnymi typami danych.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 Zmienna `refInteger` ma typ czasu wykonywania `Integer` . Jest on zgodny z programem, `Integer` ale nie z `Double` . Zmienna `refForm` ma typ czasu wykonywania <xref:System.Windows.Forms.Form> . Jest on zgodny z <xref:System.Windows.Forms.Form> faktem, że jest jego typem, z <xref:System.Windows.Forms.Control> ponieważ <xref:System.Windows.Forms.Form> dziedziczy z <xref:System.Windows.Forms.Control> , i z <xref:System.ComponentModel.IComponent> <xref:System.Windows.Forms.Form> , ponieważ dziedziczy z <xref:System.ComponentModel.Component> , który implementuje <xref:System.ComponentModel.IComponent> . `refForm`Nie jest jednak zgodna z programem <xref:System.Windows.Forms.Label> .  
  
## <a name="see-also"></a>Zobacz też

- [Is, operator](is-operator.md)
- [IsNot, operator](isnot-operator.md)
- [Operatory porównania w Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../programming-guide/language-features/operators-and-expressions/index.md)
