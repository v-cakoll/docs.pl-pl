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
ms.openlocfilehash: 172472cf9a2e1bc7bb81448dc8793a4eaeb12da4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546559"
---
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="42b5e-102">Zarządzanie energią w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="42b5e-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="42b5e-103">Aplikacje Windows Forms korzystać z zalet funkcji zarządzania energią w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="42b5e-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="42b5e-104">Aplikacje można monitorować stan zasilania komputera i podjąć działania w przypadku zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="42b5e-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="42b5e-105">Na przykład jeśli aplikacja jest uruchomiona na komputerze przenośnym, możesz zechcieć wyłączenie pewnych funkcji w aplikacji, gdy poziom naładowania baterii komputera znajduje się w ramach określonego poziomu.</span><span class="sxs-lookup"><span data-stu-id="42b5e-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="42b5e-106">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zapewnia <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> zdarzenia, które występuje zawsze, gdy nie nastąpiła zmiana stanu zasilania, np. gdy użytkownik wstrzymuje lub wznawia działanie systemu operacyjnego lub podczas zmiany stanu zasilania ak lub stan baterii.</span><span class="sxs-lookup"><span data-stu-id="42b5e-106">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="42b5e-107"><xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Właściwość <xref:System.Windows.Forms.SystemInformation> klasy mogą być używane do wykonywania zapytań dla bieżącego stanu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="42b5e-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="42b5e-108">Oprócz <xref:System.Windows.Forms.BatteryChargeStatus> wyliczenia, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> właściwość zawiera również wyliczenia określania pojemność baterii (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) i baterią opłata w wysokości wartości procentowej (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span><span class="sxs-lookup"><span data-stu-id="42b5e-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="42b5e-109">Możesz użyć <xref:System.Windows.Forms.Application.SetSuspendState%2A> metody <xref:System.Windows.Forms.Application> hibernacji komputera lub zawieszeniu trybu.</span><span class="sxs-lookup"><span data-stu-id="42b5e-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="42b5e-110">Jeśli `force` argument ma wartość `false`, system operacyjny będzie emisję wydarzenia do wszystkich aplikacji żądanie zgody, aby zawiesić.</span><span class="sxs-lookup"><span data-stu-id="42b5e-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="42b5e-111">Jeśli `disableWakeEvent` argument ma wartość `true`, system operacyjny wyłącza wszystkie zdarzenia wznowienia.</span><span class="sxs-lookup"><span data-stu-id="42b5e-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="42b5e-112">Poniższy przykład kodu pokazuje, jak i hibernacji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="42b5e-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="42b5e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42b5e-113">See also</span></span>
- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
