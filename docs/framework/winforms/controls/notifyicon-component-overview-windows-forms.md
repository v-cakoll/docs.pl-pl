---
title: "NotifyIcon — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c909537bd4c52a546faeb83c6e9291c4de76d76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.NotifyIcon> składnik jest zazwyczaj używany do wyświetlania ikon dla procesów, które są uruchomione w tle i nie pokazuj użytkownika interfejsu większość czasu. Przykładem może być programu ochrony przed wirusami, którego mogą uzyskać dostęp, klikając ikonę w obszarze powiadomień stanu na pasku zadań.  
  
## <a name="key-properties-of-notifyicons"></a>Właściwości klucza obiektu NotifyIcons  
 Każdy <xref:System.Windows.Forms.NotifyIcon> składnik Wyświetla pojedynczą ikonę w obszarze stanu. Jeśli masz trzy procesy w tle i ma być wyświetlana ikona, dla każdego należy dodać trzy <xref:System.Windows.Forms.NotifyIcon> składników do formularza. Właściwości klucza obiektu <xref:System.Windows.Forms.NotifyIcon> są składnika <xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. <xref:System.Windows.Forms.NotifyIcon.Icon%2A> Właściwość ustawia ikonę, która jest wyświetlana w obszarze stanu. Aby pojawia się ikona <xref:System.Windows.Forms.NotifyIcon.Visible%2A> musi mieć ustawioną właściwość `true`.  
  
 Jeśli używasz [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], masz dostęp do dużych biblioteki standardowe obrazów, które można używać z <xref:System.Windows.Forms.NotifyIcon> formantu.  
  
## <a name="notifyicons-options"></a>Opcje NotifyIcons  
 Możesz skojarzyć porady dymek, menu skrótów i etykietki narzędzi z <xref:System.Windows.Forms.NotifyIcon> ułatwiających użytkownika.  
  
 Można wyświetlić dymek porady dotyczące <xref:System.Windows.Forms.NotifyIcon> przez wywołanie metody <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> metody, określając zakres czasu chcesz etykieta dymka do wyświetlenia. Można również określić tekst, ikonę i tytuł etykieta dymka z <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> i <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>odpowiednio. <xref:System.Windows.Forms.NotifyIcon>składniki można również skojarzyć etykietki narzędzi i menu skrótów. Aby uzyskać więcej informacji, zobacz [informacje o składniku ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) i [informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.NotifyIcon>  
 [NotifyIcon, składnik](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)
