---
title: 'Instrukcje: Grupowanie związanych wartości stałych razem (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 9174bcd2385103cf7fa1daf3133e388f9b4998a4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843765"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Instrukcje: Grupowanie związanych wartości stałych razem (Visual Basic)
Wyliczenie to najlepszy sposób, aby zgrupować pokrewnych stałych. Utwórz wyliczenie z `Enum` instrukcji w sekcji deklaracji klasy lub modułu. Aby uzyskać więcej informacji, zobacz [jak: Deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Do grupy powiązanych wartości stałych  
  
1.  Zapis deklarację, że obejmuje poziom dostępu do kodu, `Enum` — słowo kluczowe i prawidłową nazwę. Ten przykład tworzy `Private` wyliczenia, `temperatureValues`.  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2.  Definiowanie stałych w wyliczeniu. Ten przykład tworzy `Public` wyliczenie `temperatureValues` i przypisuje jej wartości.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
