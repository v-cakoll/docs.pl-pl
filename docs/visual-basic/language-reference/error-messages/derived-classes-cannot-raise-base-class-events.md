---
title: "Klasy pochodne nie mogą wywoływać zdarzeń klasy bazowej"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Klasy pochodne nie mogą wywoływać zdarzeń klasy bazowej
Zdarzenie można wywoływane tylko z miejsca deklaracji, w którym jest zadeklarowany. W związku z tym klasy nie mogą wywoływać zdarzeń z żadną inną klasę, nawet jedną, z którego pochodzi.  
  
 **Identyfikator błędu:** BC30029  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przenieś `Event` instrukcji lub `RaiseEvent` instrukcji, dzięki czemu są one w tej samej klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent — instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
