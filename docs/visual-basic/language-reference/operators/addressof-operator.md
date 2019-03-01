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
ms.openlocfilehash: b68d93009d2d297f8b8867fb8e79b26173a45095
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964672"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf — Operator (Visual Basic)
Tworzy wystąpienie delegata procedury, która odwołuje się do określonej procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Części  
 `procedurename`  
 Wymagana. Określa procedury być przywoływane przez delegata nowo utworzone procedury.  
  
## <a name="remarks"></a>Uwagi  
 `AddressOf` Operatora, tworzy delegata funkcji, który wskazuje na funkcji określonej przez `procedurename`. Gdy określonej procedury jest metodą wystąpienia następnie delegata funkcji, który odwołuje się do wystąpienia i metody. Następnie podczas wywoływania delegata funkcji określonej metody określone wystąpienie jest wywoływana.  
  
 `AddressOf` Operator może służyć jako argument konstruktora delegata lub mogą być używane w kontekście, w którym można określić typ delegata przez kompilator.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `AddressOf` operatora, aby wyznaczyć delegata do obsługi `Click` zdarzenia przycisku.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `AddressOf` operatora, aby wyznaczyć funkcji uruchamiania wątku.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz także
- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegaty](../../../visual-basic/programming-guide/language-features/delegates/index.md)
