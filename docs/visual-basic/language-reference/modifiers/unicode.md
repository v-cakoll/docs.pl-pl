---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: a61fd8e10c39569d92dd84180f678a1ff05a9310
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595725"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości Unicode, niezależnie od tego, nazwę procedury zewnętrznej, został zadeklarowany.  
  
 Po wywołaniu procedury zdefiniowany poza projektem, kompilator Visual Basic nie ma dostępu do informacji musi mieć w celu wywołania tej procedury poprawnie. Informacje te obejmują lokalizacji procedurą, jak określono, jego sekwencja wywoływania oraz zwracany typ i ciąg znaków ustaw go używa. [Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i przekazywać te informacje niezbędne.  
  
 `charsetmodifier` Części w `Declare` instrukcji dostarcza informacje zestaw znaków kierowanie ciągów podczas wywoływania procedury zewnętrznego. Wpływa to również na jak Visual Basic wyszukuje plik zewnętrznych dla nazwę procedury zewnętrznej. `Unicode` Modyfikator Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości Unicode i sprawdzić procedurę bez modyfikowania jej nazwy podczas wyszukiwania.  
  
 Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.  
  
## <a name="remarks"></a>Uwagi  
 `Unicode` Modyfikatora można używać w tym kontekście:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 To słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
