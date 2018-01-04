---
title: "Porady: wykonywanie mapowania i zmniejszanie operacji przeciągania i upuszczania między aplikacjami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 514c283575ca54e74d23ae31d3590979be2c3ef0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a>Porady: wykonywanie mapowania i zmniejszanie operacji przeciągania i upuszczania między aplikacjami
Wykonywanie operacji przeciągania i upuszczania między aplikacjami nie różni się od włączenie tej akcji w aplikacji, pod warunkiem, obie aplikacje, które są zaangażowane działają zgodnie z między "kontraktu" <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> i <xref:System.Windows.Forms.DragEventArgs.Effect%2A> właściwości.  
  
 W poniższej procedurze użyjesz aplikacji systemu Windows, które możesz utworzyć i WordPad edytora tekstów, który jest dołączony do systemu operacyjnego Windows w celu wykonania operacji przeciągania i upuszczania między aplikacjami. WordPad ma określone dozwolone efekty tekst jest przeciągnięto i Upuszczono; aplikacji systemu Windows, który będzie pisanie kodu dla będzie działać z tych skutków, dzięki czemu może można pomyślnie ukończyć operacji przeciągania i upuszczania.  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a>Aby wykonać procedurę przeciągania i upuszczania między aplikacjami  
  
1.  Tworzenie nowej aplikacji formularzy systemu Windows.  
  
2.  Dodaj <xref:System.Windows.Forms.TextBox> sterowania do formularza.  
  
3.  Skonfiguruj <xref:System.Windows.Forms.TextBox> formantu, aby odbierać dane porzucone.  
  
     Aby uzyskać więcej informacji, zobacz [wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
4.  Uruchamianie aplikacji opartych na systemie Windows, a aplikacja jest uruchomiona, uruchom program WordPad.  
  
     Program WordPad jest zainstalowany w systemie Windows, która zezwala na wykonywanie operacji przeciągania i upuszczania edytora tekstu. Nie jest dostępny, naciskając klawisz **Start** przycisku, wybierając **Uruchom**, a następnie wpisując `WordPad` w polu tekstowym **Uruchom** okno dialogowe i klikając **OK**.  
  
5.  Po otwarciu WordPad, wpisz ciąg tekstowy do niego.  
  
6.  Za pomocą myszy, zaznacz tekst, a następnie przeciągnij zaznaczony tekst do <xref:System.Windows.Forms.TextBox> formantu do aplikacji opartych na systemie Windows.  
  
     Który obserwować, gdy wskaźnik myszy zostanie na <xref:System.Windows.Forms.TextBox> formantu (i w związku z tym, zgłoś <xref:System.Windows.Forms.Control.DragEnter> zdarzeń), zmiany kursora, a mogą porzucić zaznaczonego tekstu do <xref:System.Windows.Forms.TextBox> formantu.  
  
     Ponadto można skonfigurować sieci <xref:System.Windows.Forms.TextBox> kontrolki, które umożliwia ciągów tekstowych przeciągnąć i upuścić na WordPad. Aby uzyskać więcej informacji, zobacz [wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dodawanie danych do schowka](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [Instrukcje: pobieranie danych ze schowka](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [Operacje przeciągania i upuszczania oraz obsługa schowka](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
