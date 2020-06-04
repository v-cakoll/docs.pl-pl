---
title: 'Instrukcje: iterowanie za pomocą wyliczania'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: fb6fbdd45ca0e84ccb9fc55296d78e3867d5fe25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414430"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Porady: iterowanie za pomocą wyliczania w Visual Basic
Wyliczenia zapewniają wygodny sposób pracy z zestawami powiązanych stałych i kojarzenia wartości stałych z nazwami. Aby wykonać iterację wyliczenia, można przenieść go do tablicy przy użyciu <xref:System.Enum.GetValues%2A> metody. Można również wykonać iterację w wyliczeniu przy użyciu `For...Each` instrukcji, <xref:System.Enum.GetNames%2A> używając <xref:System.Enum.GetValues%2A> metody lub do wyodrębnienia ciągu lub wartości liczbowej.  
  
### <a name="to-iterate-through-an-enumeration"></a>Aby wykonać iterację wyliczenia  
  
- Zadeklaruj tablicę i przekonwertuj jej Wyliczenie na <xref:System.Enum.GetValues%2A> metodę przed przekazaniem tablicy, tak jak każda inna zmienna. Poniższy przykład wyświetla każdy element członkowski wyliczenia <xref:Microsoft.VisualBasic.FirstDayOfWeek> podczas iteracji przez wyliczenie.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Zobacz też

- [Enumerations — Przegląd](enumerations-overview.md)
- [Instrukcje: deklarowanie wyliczenia](how-to-declare-enumerations.md)
- [Kiedy stosować wyliczanie](when-to-use-an-enumeration.md)
- [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Porady: odwoływanie się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md)
- [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md)
- [Tablice](../arrays/index.md)
