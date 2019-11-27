---
title: AddressOf, operator
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: e88520bd7e731a35b98c1d40c5210dc5d1314911
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350284"
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
  
 Operatora `AddressOf` można używać jako operandu konstruktora delegata lub można go użyć w kontekście, w którym typ delegata może być określony przez kompilator.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa operatora `AddressOf`, aby wyznaczyć delegata do obsługi zdarzenia `Click` przycisku.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `AddressOf`, aby wyznaczyć funkcję uruchamiania dla wątku.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegaci](../../../visual-basic/programming-guide/language-features/delegates/index.md)
