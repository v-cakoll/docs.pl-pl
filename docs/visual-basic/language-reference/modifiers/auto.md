---
title: Auto
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: b9bdeed55788252c71b8fb1c995c140cbfdf60eb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373131"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Określa, że Visual Basic powinny organizować ciągi zgodnie z regułami .NET Framework na podstawie zewnętrznej nazwy procedury zewnętrznej.  
  
 Po wywołaniu procedury zdefiniowanej poza projektem, kompilator Visual Basic nie ma dostępu do informacji, które muszą być wymagane do poprawnego wywołania procedury. Informacje te obejmują miejsce, w którym znajduje się procedura, sposób jego identyfikacji, jego sekwencję wywoływania i zwracany typ oraz zestaw znaków użytych w ciągu. [Instrukcja DECLARE](../statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza te niezbędne informacje.  
  
 `charsetmodifier`Część w `Declare` instrukcji dostarcza informacje zestawu znaków do organizowania ciągów podczas wywołania procedury zewnętrznej. Ma także wpływ na to, w jaki sposób Visual Basic przeszukuje zewnętrzny plik dla nazwy procedury zewnętrznej. `Auto`Modyfikator określa, że Visual Basic powinny kierować ciągi zgodnie z regułami .NET Framework i że powinien określać podstawowy zestaw znaków platformy czasu wykonywania, a także zmodyfikować nazwę procedury zewnętrznej, jeśli początkowe wyszukiwanie nie powiedzie się. Aby uzyskać więcej informacji, zobacz "zestawy znaków" w [instrukcji DECLARE](../statements/declare-statement.md).  
  
 Jeśli nie określono modyfikatora zestawu znaków, `Ansi` jest to ustawienie domyślne.  
  
## <a name="remarks"></a>Uwagi  
 `Auto`Modyfikator może być używany w tym kontekście:  
  
 [Declare — Instrukcja](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 To słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz też

- [Ansi](ansi.md)
- [Unicode](unicode.md)
- [Słowa kluczowe](../keywords/index.md)
