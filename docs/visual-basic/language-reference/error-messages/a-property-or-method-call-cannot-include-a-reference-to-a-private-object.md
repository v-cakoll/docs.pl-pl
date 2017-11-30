---
title: "Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cce2bc67beb7e4ac0664b5b7240f5eb3ea0204f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
 [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)
