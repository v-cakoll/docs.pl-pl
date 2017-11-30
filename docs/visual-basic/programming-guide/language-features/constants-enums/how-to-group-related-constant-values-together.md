---
title: "Porady: grupowanie związanych wartości stałych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be57b56047654d6eb3536bb0b8f63eca27decdb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Porady: grupowanie związanych wartości stałych (Visual Basic)
Wyliczenie to najlepszy sposób, aby grupować powiązane stałe. Utwórz wyliczenie z `Enum` instrukcji w sekcji deklaracji klasy lub module. Aby uzyskać więcej informacji, zobacz [porady: deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Do grupy związanych wartości stałych  
  
1.  Zapis deklaracji, która zawiera poziom dostępu kodu, `Enum` — słowo kluczowe i prawidłową nazwę. Ten przykład tworzy `Private` wyliczenia, `temperatureValues`.  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  Definiowanie stałych w wyliczeniu. Ten przykład tworzy `Public` wyliczenie `temperatureValues` i przypisuje jej wartości.  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Porady: odwołuje się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Stałe — Przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Stała i typy literałów](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
