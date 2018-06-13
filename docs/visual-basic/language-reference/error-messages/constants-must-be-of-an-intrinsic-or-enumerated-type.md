---
title: Stałe muszą być typu wewnętrznego lub wyliczeniowego, a nie typu klasy, struktury, parametru typu lub tablicy
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 9039376fc4d1f67ca9b526e46eaf28a0b1a3943c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587485"
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
