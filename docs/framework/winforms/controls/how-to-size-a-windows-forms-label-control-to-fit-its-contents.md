---
title: 'Instrukcje: rozmiar kontrolki etykiety (Formularze systemu Windows) pasujący do jego zawartości'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: f9e7fad1f8b2b4e962f46a1e32522f47f01de2b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191877"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Instrukcje: rozmiar kontrolki etykiety (Formularze systemu Windows) pasujący do jego zawartości
Formularze Windows <xref:System.Windows.Forms.Label> formant może być w jednym lub wielu linii, które mogą być stałe w rozmiarze lub może automatycznie zmieniał swój rozmiar do uwzględnienia swój podpis. <xref:System.Windows.Forms.Label.AutoSize%2A> Właściwość pomaga rozmiaru formantów, aby dopasować większy lub mniejszy podpisów, która jest szczególnie przydatne, jeśli podpis zmieni się w czasie wykonywania.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Aby formant etykiety dynamicznie Zmień rozmiar pasujący do jego zawartości  
  
1.  Ustaw jego <xref:System.Windows.Forms.Label.AutoSize%2A> właściwość `true`.  
  
 Jeśli <xref:System.Windows.Forms.Label.AutoSize%2A> ustawiono `false`, wyrazy w <xref:System.Windows.Forms.Label.Text%2A> właściwość będzie zawijany do następnego wiersza, jeśli jest to możliwe, ale formant nie będzie rosnąć.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek etykiet formularzy systemu Windows](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Label, kontrolka — omówienie](label-control-overview-windows-forms.md)
- [Label, kontrolka](label-control-windows-forms.md)
