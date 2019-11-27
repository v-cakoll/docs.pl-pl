---
title: 'Instrukcje: Iterowanie przez Wyliczenie'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 6e8fd6760565a73d9d3b3d1d02fc872992eea354
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354022"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Porady: iterowanie za pomocą wyliczania w Visual Basic
Wyliczenia zapewniają wygodny sposób pracy z zestawami powiązanych stałych i kojarzenia wartości stałych z nazwami. Aby wykonać iterację wyliczenia, można przenieść go do tablicy przy użyciu metody <xref:System.Enum.GetValues%2A>. Można również wykonać iterację w wyliczeniu przy użyciu instrukcji `For...Each`, używając metody <xref:System.Enum.GetNames%2A> lub <xref:System.Enum.GetValues%2A> do wyodrębnienia ciągu lub wartości liczbowej.  
  
### <a name="to-iterate-through-an-enumeration"></a>Aby wykonać iterację wyliczenia  
  
- Zadeklaruj tablicę i przekonwertuj Wyliczenie na nią przy użyciu metody <xref:System.Enum.GetValues%2A> przed przekazaniem tablicy tak jak każda inna zmienna. Poniższy przykład wyświetla każdy element członkowski wyliczenia <xref:Microsoft.VisualBasic.FirstDayOfWeek> podczas iteracji przez wyliczenie.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Instrukcje: deklarowanie wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
