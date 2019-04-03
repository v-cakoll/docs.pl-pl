---
title: Operand „AddressOf" musi być nazwą metody (bez nawiasów)
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: af1ce858108785fa4dac6352c9e80531e86fbb23
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813967"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a>Operand „AddressOf" musi być nazwą metody (bez nawiasów)
`AddressOf` Operator tworzy wystąpienie delegata procedury, która odwołuje się do określonej procedury. Składnia jest następująca.  
  
 `AddressOf``procedurename`  
  
 Dodaje nawiasy wokół następujący argument `AddressOf`, których nie są wymagane.  
  
 **Identyfikator błędu:** BC30577  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Usuń nawiasy wokół następujący argument `AddressOf`.  
  
2.  Upewnij się, że argument jest nazwa metody.  
  
## <a name="see-also"></a>Zobacz także

- [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegaty](../../../visual-basic/programming-guide/language-features/delegates/index.md)
