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
ms.openlocfilehash: 6bb9b4f30a88ece93b17ff2510087b220d538738
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979722"
---
# <a name="power-management-in-windows-forms"></a>Zarządzanie energią w formularzach systemu Windows
Aplikacje Windows Forms korzystać z zalet funkcji zarządzania energią w systemie operacyjnym Windows. Aplikacje można monitorować stan zasilania komputera i podjąć działania w przypadku zmiany stanu. Na przykład jeśli aplikacja jest uruchomiona na komputerze przenośnym, możesz zechcieć wyłączenie pewnych funkcji w aplikacji, gdy poziom naładowania baterii komputera znajduje się w ramach określonego poziomu.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zapewnia <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> zdarzenia, które występuje zawsze, gdy nie nastąpiła zmiana stanu zasilania, np. gdy użytkownik wstrzymuje lub wznawia działanie systemu operacyjnego lub podczas zmiany stanu zasilania ak lub stan baterii. <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Właściwość <xref:System.Windows.Forms.SystemInformation> klasy mogą być używane do wykonywania zapytań dla bieżącego stanu, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Oprócz <xref:System.Windows.Forms.BatteryChargeStatus> wyliczenia, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> właściwość zawiera również wyliczenia określania pojemność baterii (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) i baterią opłata w wysokości wartości procentowej (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Możesz użyć <xref:System.Windows.Forms.Application.SetSuspendState%2A> metody <xref:System.Windows.Forms.Application> hibernacji komputera lub zawieszeniu trybu. Jeśli `force` argument ma wartość `false`, system operacyjny będzie emisję wydarzenia do wszystkich aplikacji żądanie zgody, aby zawiesić. Jeśli `disableWakeEvent` argument ma wartość `true`, system operacyjny wyłącza wszystkie zdarzenia wznowienia.  
  
 Poniższy przykład kodu pokazuje, jak i hibernacji na komputerze.  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
