---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 042908b8427de2de0de96bbb32df7be018bb915c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości Unicode, niezależnie od tego, nazwę procedury zewnętrznej, został zadeklarowany.  
  
 Po wywołaniu procedury zdefiniowany poza projektem, kompilator Visual Basic nie ma dostępu do informacji musi mieć w celu wywołania tej procedury poprawnie. Informacje te obejmują lokalizacji procedurą, jak określono, jego sekwencja wywoływania oraz zwracany typ i ciąg znaków ustaw go używa. [Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i przekazywać te informacje niezbędne.  
  
 `charsetmodifier` Części w `Declare` instrukcji dostarcza informacje zestaw znaków kierowanie ciągów podczas wywoływania procedury zewnętrznego. Wpływa to również na jak Visual Basic wyszukuje plik zewnętrznych dla nazwę procedury zewnętrznej. `Unicode` Modyfikator Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości Unicode i sprawdzić procedurę bez modyfikowania jej nazwy podczas wyszukiwania.  
  
 Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.  
  
## <a name="remarks"></a>Uwagi  
 `Unicode` Modyfikatora można używać w tym kontekście:  
  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 To słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
