---
title: Auto (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e32c4c910567829a4f5c59b48020db4dfbbeb7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Określa, że Visual Basic powinien kierować ciągi zgodnie z regułami programu .NET Framework oparte na zewnętrzną nazwę procedury zewnętrznej został zadeklarowany.  
  
 Po wywołaniu procedury zdefiniowany poza projektem, kompilator Visual Basic nie ma dostępu do informacji musi mieć do wywołania tej procedury poprawnie. Informacje te obejmują lokalizacji procedurą, jak określono, jego sekwencja wywoływania oraz zwracany typ i ciąg znaków ustaw go używa. [Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i przekazywać te informacje niezbędne.  
  
 `charsetmodifier` Części w `Declare` instrukcji dostarcza informacji zestaw znaków dla organizowanie ciągów podczas wywoływania procedury zewnętrznego. Wpływa to również na jak Visual Basic wyszukuje plik zewnętrznych dla nazwę procedury zewnętrznej. `Auto` Modyfikator Określa, że Visual Basic powinien kierować ciągi zgodnie z regułami programu .NET Framework i powinien ustalić podstawowy zestaw czasu wykonywania platformy i prawdopodobnie znaków zmodyfikować nazwę procedury zewnętrznej, jeśli początkowe wyszukiwanie kończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz "Zestawów znaków" w [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.  
  
## <a name="remarks"></a>Uwagi  
 `Auto` Modyfikatora można używać w tym kontekście:  
  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 To słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
