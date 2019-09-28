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
ms.openlocfilehash: 2ebadf5ded1a23fe46b8e16cf18ae265b5d3c255
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591654"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf — Operator (Visual Basic)
Tworzy wystąpienie delegata, które odwołuje się do określonej procedury.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Części  
 `procedurename`  
 Wymagany. Określa procedurę, do której odwołuje się nowo utworzony delegat.  
  
## <a name="remarks"></a>Uwagi  
 Operator `AddressOf` tworzy delegata, który wskazuje na podrzędną lub funkcję określoną przez `procedurename`. Gdy określona procedura jest metodą wystąpienia, delegat odwołuje się zarówno do wystąpienia, jak i metody. Następnie, gdy obiekt delegowany jest wywoływany, wywoływana jest określona metoda określonego wystąpienia.  
  
 Operatora `AddressOf` można użyć jako operandu konstruktora delegata lub można go użyć w kontekście, w którym typ delegata może być określony przez kompilator.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa operatora `AddressOf`, aby wyznaczyć delegata do obsługi zdarzenia `Click` przycisku.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `AddressOf`, aby wyznaczyć funkcję uruchamiania wątku.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegaty](../../../visual-basic/programming-guide/language-features/delegates/index.md)
