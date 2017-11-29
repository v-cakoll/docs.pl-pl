---
title: "Zarządzanie energią w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e12f39a63a4f81e6deec4512a4e18ad2bda7e5e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="power-management-in-windows-forms"></a>Zarządzanie energią w formularzach systemu Windows
Aplikacje Windows Forms możliwość korzystania z funkcji zarządzania energią w systemie operacyjnym Windows. Aplikacje można monitorować stan zasilania komputera i podejmij akcję po zmianie stanu. Na przykład jeśli aplikacja jest uruchomiona na komputerze przenośnym, możesz wyłączyć pewnych funkcji w aplikacji, gdy poziom naładowania baterii komputera znajduje się w obszarze pewnego poziomu.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zapewnia <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> zdarzenie, które występuje zawsze, gdy nastąpiła zmiana stanu zasilania, np. gdy użytkownik wstrzymuje lub wznawia działanie systemu operacyjnego lub po zmianie stanu zasilania ak lub stan baterii. <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Właściwość <xref:System.Windows.Forms.SystemInformation> klasa może być używana do zapytań o bieżącym stanie, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Oprócz <xref:System.Windows.Forms.BatteryChargeStatus> wyliczenia, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> właściwość zawiera również wyliczenia określania pojemność baterii (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) i baterii obciążania procent (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Można użyć <xref:System.Windows.Forms.Application.SetSuspendState%2A> metody <xref:System.Windows.Forms.Application> hibernacji komputera lub trybu wstrzymania. Jeśli `force` argument ma wartość `false`, system operacyjny będzie emisję wydarzenia do wszystkich aplikacji, które chce uzyskać uprawnienia do wstrzymania. Jeśli `disableWakeEvent` argument ma wartość `true`, system operacyjny wyłącza wszystkie zdarzenia wznowienia.  
  
 Poniższy przykład kodu pokazuje, jak wprowadzić komputera w stan hibernacji.  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
