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
ms.openlocfilehash: b3c9452f8d144fb18ea3efcb35b85caed80e8692
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778680"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości Unicode, niezależnie od nazwy procedury zewnętrznego został zadeklarowany.  
  
 Po wywołaniu procedury zdefiniowane poza projektem, kompilator Visual Basic nie ma dostępu do informacji, że musi mieć, aby prawidłowo wywołać procedurę. Informacje te obejmują, gdzie znajduje się procedura, sposób jego identyfikacji, jego sekwencja wywoływania i zwracany typ i zestaw znaków ciągu, od go używa. [Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza to informacje niezbędne.  
  
 `charsetmodifier` Wchodzi w skład w `Declare` instrukcji dostarcza informacji zestawu znaków na przeprowadzanie marshalingu ciągów podczas wywoływania procedury zewnętrznego. Ma to również wpływ jak języka Visual Basic poszukuje zewnętrznego pliku, aby uzyskać nazwę procedury zewnętrznej. `Unicode` Modyfikator Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości Unicode i sprawdzić procedurę bez modyfikowania jej nazwy podczas wyszukiwania.  
  
 Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.  
  
## <a name="remarks"></a>Uwagi  
 `Unicode` Modyfikatora można używać w tym kontekście:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów urządzeń inteligentnych  
 This — słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz także

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
