---
title: 'Porady: odwoływanie się do elementu członkowskiego wyliczenia'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 01db5b84783eda45cd7867dc8fea8a69fc18b98a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353996"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>Porady: odwoływanie się do elementu członkowskiego wyliczenia (Visual Basic)
Wyliczenia zapewniają wygodny sposób pracy z zestawami powiązanych stałych i kojarzenia wartości stałych z nazwami. Na przykład można zadeklarować Wyliczenie dla zestawu stałych całkowitych skojarzonych z dniami tygodnia, a następnie użyć nazw dni, a nie ich wartości całkowitych w kodzie.  
  
 Można uniknąć używania w pełni kwalifikowanych nazw za pomocą instrukcji `Imports`. Aby uzyskać więcej informacji, zobacz [wyliczenia i kwalifikowanie nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-refer-to-an-enumeration-member"></a>Aby odwołać się do elementu członkowskiego wyliczenia  
  
- Zakwalifikuj nazwę elementu członkowskiego z wyliczeniem. Na przykład poniższy przykład przypisuje `Saturday` element członkowski `FirstDayOfWeek` wyliczenia do zmiennej `DayValue`.  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: deklarowanie wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Instrukcje: Iterowanie przez Wyliczenie w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
