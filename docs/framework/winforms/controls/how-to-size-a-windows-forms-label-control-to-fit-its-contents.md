---
title: "Porady: rozmiar formantu etykiety (Formularze systemu Windows) pasujący do jego zawartości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd89d72264e5837d2c41fcb0ab024a7b16f4205b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Porady: rozmiar formantu etykiety (Formularze systemu Windows) pasujący do jego zawartości
Formularze systemu Windows <xref:System.Windows.Forms.Label> formant może być jednym lub wielu linii, które mogą być stałym rozmiarze lub można automatycznie zmieniany aby zmieścił się w jego podpis. <xref:System.Windows.Forms.Label.AutoSize%2A> Właściwość pomaga rozmiaru formantów w celu dopasowania większy lub mniejszy podpisów, która jest szczególnie przydatne, jeśli zmieni podpis w czasie wykonywania.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Aby utworzyć etykietę kontroli dynamicznie Zmień rozmiar pasujący do jego zawartości  
  
1.  Ustaw jego <xref:System.Windows.Forms.Label.AutoSize%2A> właściwości `true`.  
  
 Jeśli <xref:System.Windows.Forms.Label.AutoSize%2A> ustawiono `false`, wyrazy w <xref:System.Windows.Forms.Label.Text%2A> właściwości będzie zawijany do następnego wiersza, jeśli to możliwe, ale kontrolka nie będzie rosnąć.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie klawiszy dostępu za pomocą formantów etykiet formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [Informacje o formancie etykiety](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Label — formant](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
