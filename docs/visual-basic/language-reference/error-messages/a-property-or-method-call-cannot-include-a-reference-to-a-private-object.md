---
title: Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 36c71cdb345d0fdc0da2b58865a1f11956bcb944
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409975"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej

Wśród możliwych przyczyn tego błędu są:  
  
- Klient wywołał właściwość lub metodę składnika out-of-process i próbował przekazać odwołanie do obiektu prywatnego jako jednego z argumentów.  
  
- Składnik poza procesem wywołał metodę wywołania zwrotnego na kliencie i próbował przekazać odwołanie do obiektu prywatnego.  
  
- Składnik, który podjął próbę przekazania odwołania do prywatnego obiektu jako argument zdarzenia, które było podwyższane.  
  
- Klient próbował przypisać odwołanie do obiektu prywatnego do `ByRef` argumentu zdarzenia, które obsłużył.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Usuń odwołanie.  
  
## <a name="see-also"></a>Zobacz też

- [Użytek](../modifiers/private.md)
