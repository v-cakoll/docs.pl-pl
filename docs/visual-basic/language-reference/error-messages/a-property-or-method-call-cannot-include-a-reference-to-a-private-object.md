---
title: Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 53f9052555555a5b9dcb038dfee9cd54dc2b4251
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976197"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej

Wśród możliwych przyczyn tego błędu są:  
  
- Klient wywołał właściwość lub metodę składnika out-of-process i próbował przekazać odwołanie do obiektu prywatnego jako jednego z argumentów.  
  
- Składnik poza procesem wywołał metodę wywołania zwrotnego na kliencie i próbował przekazać odwołanie do obiektu prywatnego.  
  
- Składnik, który podjął próbę przekazania odwołania do prywatnego obiektu jako argument zdarzenia, które było podwyższane.  
  
- Klient próbował przypisać odwołanie do obiektu prywatnego do argumentu `ByRef` zdarzenia, które obsłużył.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Usuń odwołanie.  
  
## <a name="see-also"></a>Zobacz także

- [Private](../../../visual-basic/language-reference/modifiers/private.md)
