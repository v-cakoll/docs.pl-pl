---
title: "Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 044fa4ab2e9a37038e9db9a2784fad4190713806
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj przy użyciu narzędzia Projektant
Na każdym formularzy systemu Windows, możesz wyznaczyć <xref:System.Windows.Forms.Button> formantu na przycisk Akceptuj, znanej także jako przycisk domyślny. Przy każdym naciśnięciu klawisza ENTER zostanie kliknięty przycisk domyślny, niezależnie od tego, który inny formant w formularzu ma fokus. Wyjątki, aby się to, gdy formant fokus jest inny przycisk — w takim przypadku zostanie kliknięty przycisk z fokusem — lub wielowierszowego pola tekstowego lub kontrolki niestandardowej, która traps klawisz ENTER.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-designate-the-accept-button"></a>Aby wyznaczyć na przycisk Akceptuj  
  
1.  Wybierz formularz, na którym znajduje się przycisk.  
  
2.  W **właściwości** Ustaw formularza <xref:System.Windows.Forms.Form.AcceptButton%2A> właściwości <xref:System.Windows.Forms.Button> nazwy formantu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Informacje o kontrolce przycisku](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Sposoby wyboru formantu przycisku formularzy systemu Windows](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [Button — formant](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
