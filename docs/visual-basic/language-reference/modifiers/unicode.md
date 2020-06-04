---
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: 9b1bc40bb52244deefc0486d3a40c4b961ad1ee5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402684"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Określa, że Visual Basic powinny kierować wszystkie ciągi do wartości Unicode, niezależnie od nazwy zadeklarowanej procedury zewnętrznej.  
  
 Po wywołaniu procedury zdefiniowanej poza projektem, kompilator Visual Basic nie ma dostępu do informacji, które muszą mieć w celu poprawnego wywołania procedury. Informacje te obejmują miejsce, w którym znajduje się procedura, sposób jego identyfikacji, jego sekwencję wywoływania i zwracany typ oraz zestaw znaków użytych w ciągu. [Instrukcja DECLARE](../statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza te niezbędne informacje.  
  
 `charsetmodifier`Część w `Declare` instrukcji dostarcza informacje zestawu znaków do organizowania ciągów podczas wywołania procedury zewnętrznej. Ma także wpływ na to, w jaki sposób Visual Basic przeszukuje zewnętrzny plik dla nazwy procedury zewnętrznej. `Unicode`Modyfikator określa, że Visual Basic powinien kierować wszystkie ciągi do wartości Unicode i należy odszukać procedurę bez modyfikowania jej nazwy podczas wyszukiwania.  
  
 Jeśli nie określono modyfikatora zestawu znaków, `Ansi` jest to ustawienie domyślne.  
  
## <a name="remarks"></a>Uwagi  
 `Unicode`Modyfikator może być używany w tym kontekście:  
  
 [Declare — Instrukcja](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 To słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz też

- [Ansi](ansi.md)
- [Automatycznie](auto.md)
- [Słowa kluczowe](../keywords/index.md)
