---
title: Dopasuj rozmiar kontrolki etykiety do jej zawartości
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743775"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Porady: rozmiar formantu etykiety (Formularze systemu Windows) pasujący do jego zawartości
Formant Windows Forms <xref:System.Windows.Forms.Label> może być jednowierszowy lub Wielowierszowy i może być ustalony w rozmiarze lub może automatycznie zmieniać rozmiar w celu dopasowania go do podpisu. Właściwość <xref:System.Windows.Forms.Label.AutoSize%2A> ułatwia dopasowanie rozmiaru formantów do większych lub mniejszych napisów, co jest szczególnie przydatne, gdy podpis zostanie zmieniony w czasie wykonywania.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Aby dopasować rozmiar kontrolki etykiety dynamicznie do jej zawartości  
  
1. Ustaw jej Właściwość <xref:System.Windows.Forms.Label.AutoSize%2A> na `true`.  
  
 Jeśli <xref:System.Windows.Forms.Label.AutoSize%2A> jest ustawiona na `false`, słowa określone we właściwości <xref:System.Windows.Forms.Label.Text%2A> zostaną zawinięte do następnego wiersza, jeśli jest to możliwe, ale formant nie zostanie powiększony.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek Label formularzy Windows Forms](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Label, kontrolka — omówienie](label-control-overview-windows-forms.md)
- [Label, kontrolka](label-control-windows-forms.md)
