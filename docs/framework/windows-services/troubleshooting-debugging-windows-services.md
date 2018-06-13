---
title: 'Rozwiązywanie problemów: debugowanie usług systemu Windows'
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
manager: douge
ms.openlocfilehash: 77a0c19c2da2d1886beaf396650fa024fc1243a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510140"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="655ec-102">Rozwiązywanie problemów: debugowanie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="655ec-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="655ec-103">Podczas debugowania aplikacji usługi systemu Windows, usługi i **Windows Service Manager** interakcji.</span><span class="sxs-lookup"><span data-stu-id="655ec-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="655ec-104">**Programu Service Manager** uruchamia usługi przez wywołanie metody <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, a następnie czeka 30 sekund na <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="655ec-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="655ec-105">Jeśli metoda nie zwraca w tym okresie, Menedżer pokazuje błąd, nie można uruchomić usługi.</span><span class="sxs-lookup"><span data-stu-id="655ec-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="655ec-106">Podczas debugowania <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody zgodnie z opisem w [porady: debugowanie aplikacji usług systemu Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), należy pamiętać o tym okres 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="655ec-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="655ec-107">Jeśli punkt przerwania w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> — metoda i przy jego użyciu nie krok w ciągu 30 sekund, nie można uruchomić Menedżera usługi.</span><span class="sxs-lookup"><span data-stu-id="655ec-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="655ec-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="655ec-108">See Also</span></span>  
 [<span data-ttu-id="655ec-109">Instrukcje: debugowanie aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="655ec-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="655ec-110">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="655ec-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
