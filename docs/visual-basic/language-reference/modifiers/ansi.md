---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 67792e52c21555bef46548e9ab0a6ebd32061071
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373203"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Określa, że Visual Basic powinny kierować wszystkie ciągi do wartości American National Standards Institute (ANSI), niezależnie od nazwy zadeklarowanej procedury zewnętrznej.  
  
 Po wywołaniu procedury zdefiniowanej poza projektem kompilator Visual Basic nie ma dostępu do informacji potrzebnych do poprawnego wywołania procedury. Informacje te obejmują miejsce, w którym znajduje się procedura, sposób jego identyfikacji, jego sekwencję wywoływania i zwracany typ oraz zestaw znaków użytych w ciągu. [Instrukcja DECLARE](../statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza te niezbędne informacje.  
  
 `charsetmodifier`Część w `Declare` instrukcji dostarcza informacje zestawu znaków do organizowania ciągów podczas wywołania procedury zewnętrznej. Ma także wpływ na to, w jaki sposób Visual Basic przeszukuje zewnętrzny plik dla nazwy procedury zewnętrznej. `Ansi`Modyfikator określa, że Visual Basic powinny kierować wszystkie ciągi do wartości ANSI i należy odszukać procedurę bez modyfikowania jej nazwy podczas wyszukiwania.  
  
 Jeśli nie określono modyfikatora zestawu znaków, `Ansi` jest to ustawienie domyślne.  
  
## <a name="remarks"></a>Uwagi  
 `Ansi`Modyfikator może być używany w tym kontekście:  
  
 [Declare — Instrukcja](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 To słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz też

- [Automatycznie](auto.md)
- [Unicode](unicode.md)
- [Słowa kluczowe](../keywords/index.md)
