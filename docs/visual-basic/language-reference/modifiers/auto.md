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
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351618"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Określa, że Visual Basic powinny organizować ciągi zgodnie z regułami .NET Framework na podstawie zewnętrznej nazwy procedury zewnętrznej.  
  
 Po wywołaniu procedury zdefiniowanej poza projektem, kompilator Visual Basic nie ma dostępu do informacji, które muszą być wymagane do poprawnego wywołania procedury. Informacje te obejmują miejsce, w którym znajduje się procedura, sposób jego identyfikacji, jego sekwencję wywoływania i zwracany typ oraz zestaw znaków użytych w ciągu. [Instrukcja DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza te niezbędne informacje.  
  
 Część `charsetmodifier` w instrukcji `Declare` dostarcza informacje o zestawie znaków do organizowania ciągów podczas wywołania procedury zewnętrznej. Ma także wpływ na to, w jaki sposób Visual Basic przeszukuje zewnętrzny plik dla nazwy procedury zewnętrznej. Modyfikator `Auto` określa, że Visual Basic powinny kierować ciągi zgodnie z regułami .NET Framework i że powinien określać podstawowy zestaw znaków platformy czasu wykonywania, a także zmodyfikować nazwę procedury zewnętrznej, jeśli początkowe wyszukiwanie nie powiedzie się. Aby uzyskać więcej informacji, zobacz "zestawy znaków" w [instrukcji DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Jeśli nie określono modyfikatora zestawu znaków, `Ansi` jest wartością domyślną.  
  
## <a name="remarks"></a>Uwagi  
 Modyfikator `Auto` może być używany w tym kontekście:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów urządzeń inteligentnych  
 To słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz także

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
