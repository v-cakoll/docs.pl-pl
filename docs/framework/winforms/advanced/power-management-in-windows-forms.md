---
title: Zarządzanie zużyciem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 9ac39df43a08f62e50116c61c4bdeda4cd1c8281
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746856"
---
# <a name="power-management-in-windows-forms"></a>Zarządzanie energią w formularzach systemu Windows
Aplikacje Windows Forms mogą korzystać z funkcji zarządzania mocą w systemie operacyjnym Windows. Aplikacje mogą monitorować stan mocy komputera i podejmować działania, gdy nastąpi zmiana stanu. Na przykład jeśli aplikacja działa na komputerze przenośnym, można wyłączyć niektóre funkcje w aplikacji, gdy opłata baterii komputera spadnie poniżej określonego poziomu.  
  
 .NET Framework zapewnia <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> zdarzenie, które występuje zawsze, gdy istnieje zmiana stanu zasilania, na przykład wstrzymanie lub wznowienie działania systemu operacyjnego albo zmiana stanu zasilania lub stanu baterii na energię. Właściwość <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> klasy <xref:System.Windows.Forms.SystemInformation> może służyć do wykonywania zapytań dotyczących bieżącego stanu, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Oprócz wyliczeń <xref:System.Windows.Forms.BatteryChargeStatus> Właściwość <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> zawiera również Wyliczenie do określania pojemności baterii (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) i stawki baterii (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Można użyć metody <xref:System.Windows.Forms.Application.SetSuspendState%2A> <xref:System.Windows.Forms.Application>, aby przełączyć komputer w tryb hibernacji lub wstrzymania. Jeśli argument `force` jest ustawiony na `false`, system operacyjny emituje zdarzenie do wszystkich aplikacji żądających uprawnienia do zawieszenia. Jeśli argument `disableWakeEvent` jest ustawiony na `true`, system operacyjny wyłącza wszystkie zdarzenia wznawiania.  
  
 Poniższy przykład kodu demonstruje sposób umieszczania komputera w stan hibernacji.  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
