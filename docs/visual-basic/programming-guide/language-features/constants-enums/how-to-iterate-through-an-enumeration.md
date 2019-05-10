---
title: 'Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: c3fd7e6f7e8e4fcabf279975f7ffc2d848679396
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645247"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic
Wyliczenia zapewniają wygodny sposób pracy z zestawami pokrewnych stałych i skojarzyć wartości stałych o nazwach. Do iteracji, za pomocą wyliczania, można go przenieść do tablicy przy użyciu <xref:System.Enum.GetValues%2A> metody. Można również wykonać iterację przy użyciu wyliczenia `For...Each` instrukcji, za pomocą <xref:System.Enum.GetNames%2A> lub <xref:System.Enum.GetValues%2A> metodę, aby uzyskać wartość ciągu lub liczbowe.  
  
### <a name="to-iterate-through-an-enumeration"></a>Do iteracji przez wyliczenie  
  
- Deklarowanie tablicy i przekonwertować ją za pomocą wyliczenia <xref:System.Enum.GetValues%2A> metoda przed przekazaniem tablicy, jak będą inne zmienne. Poniższy przykład wyświetla każdy element członkowski wyliczenia <xref:Microsoft.VisualBasic.FirstDayOfWeek> jako iteruje wyliczenia.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Instrukcje: Deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
