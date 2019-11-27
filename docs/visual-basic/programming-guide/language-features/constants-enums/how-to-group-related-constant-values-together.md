---
title: 'Porady: grupowanie związanych wartości stałych'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 151eefee4f69e1db8ba40f91334da8a051b95732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354029"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Porady: grupowanie związanych wartości stałych (Visual Basic)
Wyliczenie jest najlepszym sposobem grupowania powiązanych ze sobą stałych. Wyliczenie można utworzyć za pomocą instrukcji `Enum` w sekcji deklaracji klasy lub modułu. Aby uzyskać więcej informacji, zobacz [How to: DECLARE a Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Aby pogrupować powiązane wartości stałe  
  
1. Napisz deklarację zawierającą poziom dostępu do kodu, słowo kluczowe `Enum` i prawidłową nazwę. Ten przykład tworzy Wyliczenie `Private`, `temperatureValues`.  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. Zdefiniuj stałe w wyliczeniu. Ten przykład tworzy `Public` Wyliczenie `temperatureValues` i przypisuje jego wartości.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
