---
title: Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 1f36526eab1bc0964bf89398b6e0f3e74d09fdc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583828"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
Wśród możliwych przyczyn tego błędu są:  
  
-   Klient wywoływane właściwości lub metody składnika poza procesem i próbował przekazać odwołanie do obiektu prywatnego jako jeden z argumentów.  
  
-   Składnik poza procesem wywołać metodę wywołania zwrotnego dla klienta i próbował przekazać odwołanie do obiektu prywatnego.  
  
-   Składnik poza procesem Próbowano przekazać odwołanie do obiektu prywatnego jako argument zdarzenia, który został wywoływanie zdarzeń.  
  
-   Klient próbował przypisać odwołania do obiektu prywatnego `ByRef` argument był on obsługi zdarzeń.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Usuń odwołanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)
