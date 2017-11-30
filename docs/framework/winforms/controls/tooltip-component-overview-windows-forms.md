---
title: "ToolTip — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff2364b5c7223c265571257920a7c7e794b4921b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.ToolTip> składnika wyświetla tekst, gdy użytkownik wskazuje na formanty. Etykietka narzędzia może być skojarzony z żadnym formantem. Przykładowe zastosowanie tego składnika: Aby zaoszczędzić miejsce na formularzu, można wyświetlić na małe ikony na przycisku i używać etykietka narzędzia wyjaśnić funkcja przycisku.  
  
## <a name="working-with-the-tooltip-component"></a>Praca z ToolTip — składnik  
 A <xref:System.Windows.Forms.ToolTip> stanowi `ToolTip` właściwości wielu formantów w formularzu systemu Windows lub innych kontenera. Na przykład, jeśli zostanie umieszczony <xref:System.Windows.Forms.ToolTip> składnika w formularzu, można wyświetlić "Wpisz tutaj nazwę" <xref:System.Windows.Forms.TextBox> kontroli oraz "Kliknij tutaj, aby zapisać zmiany" dla <xref:System.Windows.Forms.Button> formantu.  
  
 Metody klucza <xref:System.Windows.Forms.ToolTip> są składnika <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> i <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Można użyć <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodę, aby ustawić etykietki narzędzi wyświetlane dla formantów. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie etykietki narzędzi dla formantów w formularzu systemu Windows w czasie projektowania](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). Właściwości klucza są <xref:System.Windows.Forms.ToolTip.Active%2A>, musi być ustawiona na `true` dla etykietki narzędzia w celu wyświetlenia, i <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, która określa długość czasu, który jest wyświetlany ciąg etykietki narzędzia, jak długo użytkownik musi wskazywać na formantu etykietki narzędzia w celu wyświetlenia i jak długie go Przejście do kolejnego elementu ToolTip pojawią się. Aby uzyskać więcej informacji, zobacz [porady: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolTip>  
 [Porady: ustawienie elementu ToolTips dla formantów w formularzu systemu Windows w czasie projektowania](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [Porady: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
