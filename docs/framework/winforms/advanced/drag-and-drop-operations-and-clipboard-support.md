---
title: Operacje przeciągania i upuszczania oraz obsługa schowka
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: 05cc79abdeb41cd3bfb7db21ebb206eb309ad5d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522575"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a>Operacje przeciągania i upuszczania oraz obsługa schowka
Można włączyć operacji przeciągania i upuszczania użytkownika w aplikacji systemu Windows dzięki obsłudze szereg zdarzeń, głównie <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia.  
  
 Można też wdrożyć techniczną Wycinanie/kopiowanie/wklejanie użytkownika i transfer danych użytkownika do Schowka w aplikacjach opartych na systemie Windows przy użyciu wywołania metody proste.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przewodnik: wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 Wyjaśniono, jak rozpocząć operację przeciągania i upuszczania.  
  
 [Instrukcje: wykonywanie operacji przeciągania i upuszczania między aplikacjami](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 Przedstawiono sposób wykonania operacji przeciągania i upuszczania między aplikacjami.  
  
 [Instrukcje: dodawanie danych do schowka](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 Opisuje sposób programowane wstawianie informacji ze Schowka.  
  
 [Instrukcje: pobieranie danych ze schowka](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 Opisuje sposób dostępu do danych przechowywanych w Schowku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Funkcjonalność przeciągania i upuszczania w formularzach Windows Forms](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 Opisuje metody, zdarzeń i klasy używane do implementowania zachowanie przeciągania i upuszczania.  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 W tym artykule opisano mogli dokładnie zapoznać się zdarzenia, które żąda uprawnień, aby kontynuować operację przeciągania.  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 W tym artykule opisano mogli dokładnie zapoznać się metody, która jest podstawą rozpoczyna operację przeciągania.  
  
 <xref:System.Windows.Forms.Clipboard>  
 Zobacz też [porady: wysyłanie danych do Active podrzędnych MDI](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).
