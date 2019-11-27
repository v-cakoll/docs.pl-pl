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
ms.openlocfilehash: 0c38c2b81af7b4cb8fd1723853a09c5413f805af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344740"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Określa, że Visual Basic powinny kierować wszystkie ciągi do wartości American National Standards Institute (ANSI), niezależnie od nazwy zadeklarowanej procedury zewnętrznej.  
  
 Po wywołaniu procedury zdefiniowanej poza projektem kompilator Visual Basic nie ma dostępu do informacji potrzebnych do poprawnego wywołania procedury. Informacje te obejmują miejsce, w którym znajduje się procedura, sposób jego identyfikacji, jego sekwencję wywoływania i zwracany typ oraz zestaw znaków użytych w ciągu. [Instrukcja DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza te niezbędne informacje.  
  
 Część `charsetmodifier` w instrukcji `Declare` dostarcza informacje o zestawie znaków do organizowania ciągów podczas wywołania procedury zewnętrznej. Ma także wpływ na to, w jaki sposób Visual Basic przeszukuje zewnętrzny plik dla nazwy procedury zewnętrznej. Modyfikator `Ansi` określa, że Visual Basic powinien kierować wszystkie ciągi do wartości ANSI i należy odszukać procedurę bez modyfikowania jej nazwy podczas wyszukiwania.  
  
 Jeśli nie określono modyfikatora zestawu znaków, `Ansi` jest wartością domyślną.  
  
## <a name="remarks"></a>Uwagi  
 Modyfikator `Ansi` może być używany w tym kontekście:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 To słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz także

- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
