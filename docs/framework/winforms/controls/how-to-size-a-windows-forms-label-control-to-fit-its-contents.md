---
title: 'Porady: rozmiar formantu etykiety (Formularze systemu Windows) pasujący do jego zawartości'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: e067966b606d77ceb9d11d2784c0d5f73ad332a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Porady: rozmiar formantu etykiety (Formularze systemu Windows) pasujący do jego zawartości
Formularze systemu Windows <xref:System.Windows.Forms.Label> formant może być jednym lub wielu linii, które mogą być stałym rozmiarze lub można automatycznie zmieniany aby zmieścił się w jego podpis. <xref:System.Windows.Forms.Label.AutoSize%2A> Właściwość pomaga rozmiaru formantów w celu dopasowania większy lub mniejszy podpisów, która jest szczególnie przydatne, jeśli zmieni podpis w czasie wykonywania.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Aby utworzyć etykietę kontroli dynamicznie Zmień rozmiar pasujący do jego zawartości  
  
1.  Ustaw jego <xref:System.Windows.Forms.Label.AutoSize%2A> właściwości `true`.  
  
 Jeśli <xref:System.Windows.Forms.Label.AutoSize%2A> ustawiono `false`, wyrazy w <xref:System.Windows.Forms.Label.Text%2A> właściwości będzie zawijany do następnego wiersza, jeśli to możliwe, ale kontrolka nie będzie rosnąć.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek Label formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [Label, kontrolka — omówienie](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Label, kontrolka](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
