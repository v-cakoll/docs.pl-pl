---
title: 'Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: faffeafc0cbe67c3b40297144ec85acd94956da9
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45528292"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant
W każdym formularzu Windows, można wyznaczyć <xref:System.Windows.Forms.Button> formantu przycisk Anuluj. Kliknięto przycisk Anuluj w każdym przypadku, gdy użytkownik naciśnie klawisz ESC, niezależnie od tego, którego fokus ma inne kontrolki na formularzu. Taki przycisk jest zwykle zaprogramowane umożliwia użytkownikowi szybkie zakończyć operację bez zobowiązania do dowolnej akcji.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-designate-the-cancel-button"></a>Aby wyznaczyć przycisk Anuluj  
  
1.  Wybierz formularz, w którym znajduje się przycisk.  
  
2.  W **właściwości** okna, ustaw dla formularza <xref:System.Windows.Forms.Form.CancelButton%2A> właściwość <xref:System.Windows.Forms.Button> jego nazwy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [Button, kontrolka — omówienie](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Sposoby wyboru kontrolki przycisku Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Akceptuj przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [Button, kontrolka](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
