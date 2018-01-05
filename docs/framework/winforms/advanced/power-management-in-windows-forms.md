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
ms.workload: dotnet
ms.openlocfilehash: a7600ae42194b3333c404d217c2605a226df99e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="0ca8d-102">Zarządzanie energią w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0ca8d-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="0ca8d-103">Aplikacje Windows Forms możliwość korzystania z funkcji zarządzania energią w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="0ca8d-104">Aplikacje można monitorować stan zasilania komputera i podejmij akcję po zmianie stanu.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="0ca8d-105">Na przykład jeśli aplikacja jest uruchomiona na komputerze przenośnym, możesz wyłączyć pewnych funkcji w aplikacji, gdy poziom naładowania baterii komputera znajduje się w obszarze pewnego poziomu.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="0ca8d-106">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zapewnia <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> zdarzenie, które występuje zawsze, gdy nastąpiła zmiana stanu zasilania, np. gdy użytkownik wstrzymuje lub wznawia działanie systemu operacyjnego lub po zmianie stanu zasilania ak lub stan baterii.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-106">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="0ca8d-107"><xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Właściwość <xref:System.Windows.Forms.SystemInformation> klasa może być używana do zapytań o bieżącym stanie, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="0ca8d-108">Oprócz <xref:System.Windows.Forms.BatteryChargeStatus> wyliczenia, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> właściwość zawiera również wyliczenia określania pojemność baterii (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) i baterii obciążania procent (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span><span class="sxs-lookup"><span data-stu-id="0ca8d-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="0ca8d-109">Można użyć <xref:System.Windows.Forms.Application.SetSuspendState%2A> metody <xref:System.Windows.Forms.Application> hibernacji komputera lub trybu wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="0ca8d-110">Jeśli `force` argument ma wartość `false`, system operacyjny będzie emisję wydarzenia do wszystkich aplikacji, które chce uzyskać uprawnienia do wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="0ca8d-111">Jeśli `disableWakeEvent` argument ma wartość `true`, system operacyjny wyłącza wszystkie zdarzenia wznowienia.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="0ca8d-112">Poniższy przykład kodu pokazuje, jak wprowadzić komputera w stan hibernacji.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0ca8d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ca8d-113">See Also</span></span>  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
