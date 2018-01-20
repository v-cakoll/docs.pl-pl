---
title: "Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0772fd01c2431df3b3aea034616913bd44dc0f05
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant
Na każdym formularzy systemu Windows, możesz wyznaczyć <xref:System.Windows.Forms.Button> formantu przycisku Anuluj. Kliknięto przycisk Anuluj przy każdym naciśnięciu klawisza ESC, niezależnie od tego, który inny formant w formularzu ma fokus. Aby umożliwić użytkownikowi szybkie zakończyć operację bez zatwierdzania jakiegokolwiek działania, zwykle zaplanowano taki przycisk.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-designate-the-cancel-button"></a>Aby wyznaczyć przycisku Anuluj  
  
1.  Wybierz formularz, na którym znajduje się przycisk.  
  
2.  W **właściwości** Ustaw formularza <xref:System.Windows.Forms.Form.CancelButton%2A> właściwości <xref:System.Windows.Forms.Button> nazwy formantu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [Button, kontrolka — omówienie](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Sposoby wyboru kontrolki przycisku Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Akceptuj przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [Button, kontrolka](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
