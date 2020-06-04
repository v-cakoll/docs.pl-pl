---
title: 'Porady: grupowanie związanych wartości stałych'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: d2393af8b0c2b0c2e528f9908a78fbc7f182c8cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414443"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Porady: grupowanie związanych wartości stałych (Visual Basic)
Wyliczenie jest najlepszym sposobem grupowania powiązanych ze sobą stałych. Wyliczenie można utworzyć przy użyciu `Enum` instrukcji w sekcji deklaracji klasy lub modułu. Aby uzyskać więcej informacji, zobacz [How to: DECLARE a Enumeration](how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Aby pogrupować powiązane wartości stałe  
  
1. Napisz deklarację zawierającą poziom dostępu do kodu, `Enum` słowo kluczowe i prawidłową nazwę. Ten przykład tworzy `Private` Wyliczenie `temperatureValues` .  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. Zdefiniuj stałe w wyliczeniu. Ten przykład tworzy `Public` Wyliczenie `temperatureValues` i przypisuje jego wartości.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md)
- [Porady: odwoływanie się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md)
- [Kiedy stosować wyliczanie](when-to-use-an-enumeration.md)
- [Stałe — Przegląd](constants-overview.md)
- [Stała i typy literałów](constant-and-literal-data-types.md)
- [Stałe i wyliczenia](../../../language-reference/constants-and-enumerations.md)
