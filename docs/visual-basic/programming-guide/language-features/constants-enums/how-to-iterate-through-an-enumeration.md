---
title: "Porady: iterowanie za pomocą wyliczania w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 439e6eae7d475316625a2cc1d3a70a9e7181f68a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Porady: iterowanie za pomocą wyliczania w Visual Basic
Wyliczenia oferują wygodny do pracy z zestawów powiązanych stałych i do skojarzenia z nazwami wartości stałych. Do iteracji wyliczenie, można go przenieść do tablicy przy użyciu <xref:System.Enum.GetValues%2A> metody. Można również wykonać iterację przy użyciu wyliczania `For...Each` instrukcji, za pomocą <xref:System.Enum.GetNames%2A> lub <xref:System.Enum.GetValues%2A> metodę, aby wyodrębnić wartość ciągu lub liczbowe.  
  
### <a name="to-iterate-through-an-enumeration"></a>Aby wykonać iterację — wyliczenie  
  
-   Deklarowanie tablicy i przekonwertować go z wyliczenia <xref:System.Enum.GetValues%2A> metoda przed przekazaniem tablicy jako użytkownik będzie innej zmiennej. W poniższym przykładzie przedstawiono każdy element członkowski wyliczenia <xref:Microsoft.VisualBasic.FirstDayOfWeek> zgodnie z jego iterację wyliczenia.  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Enumerations — Przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Porady: deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Porady: Określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Porady: odwołuje się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
