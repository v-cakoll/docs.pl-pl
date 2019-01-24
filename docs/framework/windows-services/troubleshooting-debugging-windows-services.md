---
title: 'Rozwiązywanie problemów: Debugowanie usług Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
author: ghogen
ms.openlocfilehash: cdffb3a8ce9c5119a0a17a8bc7e6ca78276423f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745678"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="5c8fd-102">Rozwiązywanie problemów: Debugowanie usług Windows</span><span class="sxs-lookup"><span data-stu-id="5c8fd-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="5c8fd-103">Podczas debugowania aplikacji usługi Windows, usługi i **Windows Service Manager** wchodzić w interakcje.</span><span class="sxs-lookup"><span data-stu-id="5c8fd-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="5c8fd-104">**Programu Service Manager** uruchamia usługi, wywołując <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, a następnie czeka 30 sekund w przypadku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="5c8fd-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="5c8fd-105">Jeśli metoda nie zwraca w tym okresie, Menedżer pokazuje błąd, nie można uruchomić usługi.</span><span class="sxs-lookup"><span data-stu-id="5c8fd-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="5c8fd-106">Podczas debugowania <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda zgodnie z opisem w [jak: Debugowanie aplikacji usług Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), należy pamiętać o tym okresie 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="5c8fd-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="5c8fd-107">Jeśli umieścisz punkt przerwania w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody i nie wkraczaj przez nią w ciągu 30 sekund, nie można uruchomić Menedżera usługi.</span><span class="sxs-lookup"><span data-stu-id="5c8fd-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8fd-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c8fd-108">See also</span></span>
- [<span data-ttu-id="5c8fd-109">Instrukcje: Debugowanie aplikacji usług Windows</span><span class="sxs-lookup"><span data-stu-id="5c8fd-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="5c8fd-110">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5c8fd-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
