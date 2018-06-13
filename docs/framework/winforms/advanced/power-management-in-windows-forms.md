---
title: Zarządzanie energią w formularzach systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 845cc9c910d63dfc7460bba0d5368b5b1e63efcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523494"
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
