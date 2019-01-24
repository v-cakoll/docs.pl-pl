---
title: Stałe muszą być typu wewnętrznego lub wyliczeniowego, a nie typu klasy, struktury, parametru typu lub tablicy
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 0f4cb04558bf9768de22f432a1c59203643aba6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595845"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>Stałe muszą być typu wewnętrznego lub wyliczeniowego, a nie typu klasy, struktury, parametru typu lub tablicy
Podjęto próbę deklarowanie stałej jako klasy, struktury lub typ tablicy lub jako parametr typu zdefiniowane przez zawierającego typu ogólnego.  
  
 Stałe muszą być typu wewnętrznego (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, lub `UShort`), lub `Enum` typu na podstawie jednego z typów całkowitych.  
  
 **Identyfikator błędu:** BC30424  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Deklarowanie stałej jako funkcja wewnętrzna lub `Enum` typu.  
  
2.  Stała może być również specjalna wartość takich jak `True`, `False`, lub `Nothing`. Kompilator traktuje te wstępnie zdefiniowane wartości jako odpowiedniego typu wewnętrznego.  
  
## <a name="see-also"></a>Zobacz także
- [Stałe i wyliczenia](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Typy danych](../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
