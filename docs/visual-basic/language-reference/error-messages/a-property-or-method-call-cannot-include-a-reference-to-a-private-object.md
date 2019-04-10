---
title: Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 04124ca044ad8dbff58f85230d7e10ea336d41e7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341481"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
Wśród możliwe przyczyny tego błędu są:  
  
-   Klient wywoływane właściwości lub metody składnika spoza procesu i Próbowano przekazać odwołanie do obiektu prywatnego jako jeden z argumentów.  
  
-   Składnik spoza procesu wywołano metodę wywołania zwrotnego na jego klienta i Próbowano przekazać odwołanie do obiektu prywatnego.  
  
-   Składnik spoza procesu próbował przekazać odwołanie do obiektu prywatnego jako argument zdarzenia, który został on wywoływanie.  
  
-   Klient próbował przypisać odwołanie do obiektu prywatnego `ByRef` argument był on obsługi zdarzeń.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Usuń odwołanie.  
  
## <a name="see-also"></a>Zobacz także

- [Private](../../../visual-basic/language-reference/modifiers/private.md)
