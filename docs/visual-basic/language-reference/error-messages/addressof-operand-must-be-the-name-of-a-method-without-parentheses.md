---
title: '&#39;AddressOf&#39; operand musi być nazwą metody (bez nawiasów)'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 6f9827d885996ffab8bdab91d0f774a57073e4a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565153"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>&#39;AddressOf&#39; operand musi być nazwą metody (bez nawiasów)
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
