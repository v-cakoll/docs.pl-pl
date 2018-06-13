---
title: Auto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 414998b4bef526060e7ba4f584fa071fbd0acaa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595878"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Określa, że Visual Basic powinien kierować ciągi zgodnie z regułami programu .NET Framework oparte na zewnętrzną nazwę procedury zewnętrznej został zadeklarowany.  
  
 Po wywołaniu procedury zdefiniowany poza projektem, kompilator Visual Basic nie ma dostępu do informacji musi mieć do wywołania tej procedury poprawnie. Informacje te obejmują lokalizacji procedurą, jak określono, jego sekwencja wywoływania oraz zwracany typ i ciąg znaków ustaw go używa. [Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i przekazywać te informacje niezbędne.  
  
 `charsetmodifier` Części w `Declare` instrukcji dostarcza informacji zestaw znaków dla organizowanie ciągów podczas wywoływania procedury zewnętrznego. Wpływa to również na jak Visual Basic wyszukuje plik zewnętrznych dla nazwę procedury zewnętrznej. `Auto` Modyfikator Określa, że Visual Basic powinien kierować ciągi zgodnie z regułami programu .NET Framework i powinien ustalić podstawowy zestaw czasu wykonywania platformy i prawdopodobnie znaków zmodyfikować nazwę procedury zewnętrznej, jeśli początkowe wyszukiwanie kończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz "Zestawów znaków" w [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.  
  
## <a name="remarks"></a>Uwagi  
 `Auto` Modyfikatora można używać w tym kontekście:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 To słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
