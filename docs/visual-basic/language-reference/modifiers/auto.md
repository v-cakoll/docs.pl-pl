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
ms.openlocfilehash: c128ab9982ae7ccd5fff34020f2750f703da16a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664606"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Określa, że Visual Basic powinien kierować ciągi zgodnie z regułami programu .NET Framework, na podstawie nazwy zewnętrznej procedury zewnętrznego został zadeklarowany.  
  
 Po wywołaniu procedury zdefiniowane poza projektem, kompilator Visual Basic nie ma dostępu do informacji, muszą mieć próby wywołania tej procedury poprawnie. Informacje te obejmują, gdzie znajduje się procedura, sposób jego identyfikacji, jego sekwencja wywoływania i zwracany typ i zestaw znaków ciągu, od go używa. [Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza to informacje niezbędne.  
  
 `charsetmodifier` Wchodzi w skład w `Declare` instrukcji dostarcza informacji zestaw znaków dla marshaling ciągów podczas wywoływania procedury zewnętrznego. Ma to również wpływ jak języka Visual Basic poszukuje zewnętrznego pliku, aby uzyskać nazwę procedury zewnętrznej. `Auto` Modyfikator Określa, że Visual Basic powinien kierować ciągi zgodnie z regułami programu .NET Framework i, należy określić, podstawowego znak zestawu usługi platformy uruchomieniowej i możliwie zmodyfikować nazwę procedury zewnętrznej, jeśli początkowe wyszukiwanie kończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz "Zestawach znaków" w [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.  
  
## <a name="remarks"></a>Uwagi  
 `Auto` Modyfikatora można używać w tym kontekście:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów urządzeń inteligentnych  
 This — słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz także
- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
