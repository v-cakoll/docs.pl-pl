---
title: '&#39;AddressOf&#39; operand musi być nazwą metody (bez nawiasów)'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 701d86e03d9b14236eec8436d99ec40cebbbcd44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583815"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>&#39;AddressOf&#39; operand musi być nazwą metody (bez nawiasów)
`AddressOf` Operator tworzy procedury wystąpienia delegata, który odwołuje się do określonej procedury. Składnia jest następująca:  
  
 `AddressOf``procedurename`  
  
 Dodaje nawiasy następujący argument `AddressOf`, gdy nie są jest potrzebne.  
  
 **Identyfikator błędu:** BC30577  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Usuń nawiasy następujący argument `AddressOf`.  
  
2.  Upewnij się, że argument jest nazwą metody.  
  
## <a name="see-also"></a>Zobacz też  
 [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Delegaci](../../../visual-basic/programming-guide/language-features/delegates/index.md)
