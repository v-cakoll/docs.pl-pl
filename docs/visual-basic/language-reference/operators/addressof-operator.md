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
ms.openlocfilehash: 3e7db8e7329ce8d21b6e07863e6f1673a6389608
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372067"
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
 `AddressOf`Operator tworzy delegata, który wskazuje element Sub lub Function określony przez `procedurename` . Gdy określona procedura jest metodą wystąpienia, delegat odwołuje się zarówno do wystąpienia, jak i metody. Następnie, gdy obiekt delegowany jest wywoływany, wywoływana jest określona metoda określonego wystąpienia.  
  
 `AddressOf`Operatora można używać jako operandu konstruktora delegata lub może być używany w kontekście, w którym typ delegata może być określony przez kompilator.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa `AddressOf` operatora, aby wyznaczyć delegata do obsługi `Click` zdarzenia przycisku.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `AddressOf` Aby wyznaczyć funkcję uruchamiania wątku.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz też

- [Declare — Instrukcja](../statements/declare-statement.md)
- [Function, instrukcja](../statements/function-statement.md)
- [Sub, instrukcja](../statements/sub-statement.md)
- [Delegaci](../../programming-guide/language-features/delegates/index.md)
