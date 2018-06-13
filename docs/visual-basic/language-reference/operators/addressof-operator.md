---
title: AddressOf — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 7c229c32a3b295b4dbfe50ca2abc60d4ad5f2145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597790"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf — Operator (Visual Basic)
Tworzy wystąpienia delegata procedury, która odwołuje się do określonej procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Części  
 `procedurename`  
 Wymagana. Określa procedurę, aby odwoływać się procedury nowo utworzonego obiektu delegowanego.  
  
## <a name="remarks"></a>Uwagi  
 `AddressOf` Operator tworzy delegata funkcji, które wskazuje funkcji określonej przez `procedurename`. Gdy określonej procedury jest metodą wystąpienia następnie delegata funkcji odwołuje się do wystąpienia i metody. Następnie gdy jest wywoływany delegat funkcji określonej metody określone wystąpienie jest wywoływana.  
  
 `AddressOf` Operator może być używany jako argument konstruktora delegata lub mogą być używane w kontekście, w którym można ustalić typu obiektu delegowanego przez kompilator.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `AddressOf` operatora, aby wyznaczyć pełnomocnika, aby obsłużyć `Click` zdarzeń przycisku.  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `AddressOf` operatora, aby wyznaczyć funkcja uruchomienia wątku.  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Delegaci](../../../visual-basic/programming-guide/language-features/delegates/index.md)
