---
title: 'Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: e0eaa90c8450888ea325470db5d4adae555f8d82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972331"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj przy użyciu narzędzia Projektant
W każdym formularzu Windows, można wyznaczyć <xref:System.Windows.Forms.Button> formantu na przycisk Akceptuj, znany także jako przycisk domyślny. Zawsze wtedy, gdy użytkownik naciśnie klawisz ENTER, jest kliknięty przycisk domyślny, niezależnie od tego, którego fokus ma inne kontrolki na formularzu. Wyjątki, aby się to w przypadku kontrolki z fokusem inny przycisk — w takim przypadku zostanie kliknięty przycisk z fokusem — lub wielowierszowego pola tekstowego lub formant niestandardowy, który traps klawisz ENTER.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-designate-the-accept-button"></a>Aby wyznaczyć na przycisk Akceptuj  
  
1. Wybierz formularz, w którym znajduje się przycisk.  
  
2. W **właściwości** okna, ustaw dla formularza <xref:System.Windows.Forms.Form.AcceptButton%2A> właściwość <xref:System.Windows.Forms.Button> jego nazwy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Button, kontrolka — omówienie](button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Anuluj, przy użyciu narzędzia Projektant](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button, kontrolka](button-control-windows-forms.md)
