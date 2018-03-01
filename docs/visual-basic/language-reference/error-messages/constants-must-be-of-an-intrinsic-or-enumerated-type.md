---
title: "Stałe muszą być typu wewnętrznego lub wyliczeniowego, a nie typu klasy, struktury, parametru typu lub tablicy"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 702472751810c2d2bd08ece944ef0ffafc2049b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>Stałe muszą być typu wewnętrznego lub wyliczeniowego, a nie typu klasy, struktury, parametru typu lub tablicy
Podjęto próbę deklarowanie stałej jako klasy, struktury lub typ tablicy lub jako parametr typu określone przez zawierającego typu ogólnego.  
  
 Stałe muszą być typu wewnętrznego (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, lub `UShort`), lub `Enum` typu na podstawie jednego z typów całkowitych.  
  
 **Identyfikator błędu:** BC30424  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Deklarowanie stałej jako funkcja wewnętrzna lub `Enum` typu.  
  
2.  Stała również może być wartością specjalne takie jak `True`, `False`, lub `Nothing`. Kompilator uwzględnia tych wstępnie zdefiniowanych wartości jako wewnętrzne odpowiedniego typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe i wyliczenia](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Typy danych](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)
