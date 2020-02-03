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
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="1ffdc-102">Zarządzanie energią w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1ffdc-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="1ffdc-103">Aplikacje Windows Forms mogą korzystać z funkcji zarządzania mocą w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="1ffdc-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="1ffdc-104">Aplikacje mogą monitorować stan mocy komputera i podejmować działania, gdy nastąpi zmiana stanu.</span><span class="sxs-lookup"><span data-stu-id="1ffdc-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="1ffdc-105">Na przykład jeśli aplikacja działa na komputerze przenośnym, można wyłączyć niektóre funkcje w aplikacji, gdy opłata baterii komputera spadnie poniżej określonego poziomu.</span><span class="sxs-lookup"><span data-stu-id="1ffdc-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="1ffdc-106">.NET Framework zapewnia <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> zdarzenie, które występuje zawsze, gdy istnieje zmiana stanu zasilania, na przykład wstrzymanie lub wznowienie działania systemu operacyjnego albo zmiana stanu zasilania lub stanu baterii na energię.</span><span class="sxs-lookup"><span data-stu-id="1ffdc-106">The .NET Framework provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="1ffdc-107">Właściwość <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> klasy <xref:System.Windows.Forms.SystemInformation> może służyć do wykonywania zapytań dotyczących bieżącego stanu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1ffdc-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="1ffdc-108">Oprócz wyliczeń <xref:System.Windows.Forms.BatteryChargeStatus> Właściwość <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> zawiera również Wyliczenie do określania pojemności baterii (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) i stawki baterii (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span><span class="sxs-lookup"><span data-stu-id="1ffdc-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="1ffdc-109">Można użyć metody <xref:System.Windows.Forms.Application.SetSuspendState%2A> <xref:System.Windows.Forms.Application>, aby przełączyć komputer w tryb hibernacji lub wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="1ffdc-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="1ffdc-110">Jeśli argument `force` jest ustawiony na `false`, system operacyjny emituje zdarzenie do wszystkich aplikacji żądających uprawnienia do zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="1ffdc-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="1ffdc-111">Jeśli argument `disableWakeEvent` jest ustawiony na `true`, system operacyjny wyłącza wszystkie zdarzenia wznawiania.</span><span class="sxs-lookup"><span data-stu-id="1ffdc-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="1ffdc-112">Poniższy przykład kodu demonstruje sposób umieszczania komputera w stan hibernacji.</span><span class="sxs-lookup"><span data-stu-id="1ffdc-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1ffdc-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ffdc-113">See also</span></span>

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
