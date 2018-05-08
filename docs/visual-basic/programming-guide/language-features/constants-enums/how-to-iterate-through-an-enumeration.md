---
title: 'Porady: iterowanie za pomocą wyliczania w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 06609d38c805e5f073a2f3a299ecc3aa7cf7be01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Porady: iterowanie za pomocą wyliczania w Visual Basic
Wyliczenia oferują wygodny do pracy z zestawów powiązanych stałych i do skojarzenia z nazwami wartości stałych. Do iteracji wyliczenie, można go przenieść do tablicy przy użyciu <xref:System.Enum.GetValues%2A> metody. Można również wykonać iterację przy użyciu wyliczania `For...Each` instrukcji, za pomocą <xref:System.Enum.GetNames%2A> lub <xref:System.Enum.GetValues%2A> metodę, aby wyodrębnić wartość ciągu lub liczbowe.  
  
### <a name="to-iterate-through-an-enumeration"></a>Aby wykonać iterację — wyliczenie  
  
-   Deklarowanie tablicy i przekonwertować go z wyliczenia <xref:System.Enum.GetValues%2A> metoda przed przekazaniem tablicy jako użytkownik będzie innej zmiennej. W poniższym przykładzie przedstawiono każdy element członkowski wyliczenia <xref:Microsoft.VisualBasic.FirstDayOfWeek> zgodnie z jego iterację wyliczenia.  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Porady: deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
