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
ms.openlocfilehash: cbedb0051cbb08c2875e145a2bad35ae4d02a74e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053510"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="58c6c-102">Rozwiązywanie problemów: debugowanie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="58c6c-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="58c6c-103">Gdy debugujesz aplikację usługi systemu Windows, usługa i **Service Manager systemu Windows** współpracują.</span><span class="sxs-lookup"><span data-stu-id="58c6c-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="58c6c-104">**Service Manager** uruchamia usługę, wywołując <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę, a następnie czeka 30 sekund na zwrócenie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="58c6c-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="58c6c-105">Jeśli metoda nie zwróci tego czasu, Menedżer pokazuje błąd, że nie można uruchomić usługi.</span><span class="sxs-lookup"><span data-stu-id="58c6c-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="58c6c-106">Podczas debugowania <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody zgodnie z opisem w [instrukcje: debugowanie aplikacji usługi systemu Windows](how-to-debug-windows-service-applications.md), musisz mieć świadomość tego 30-sekundowego okresu.</span><span class="sxs-lookup"><span data-stu-id="58c6c-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="58c6c-107">Jeśli umieścisz punkt przerwania w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodzie i nie ustawisz go w ciągu 30 sekund, Menedżer nie uruchomi usługi.</span><span class="sxs-lookup"><span data-stu-id="58c6c-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58c6c-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58c6c-108">See also</span></span>

- [<span data-ttu-id="58c6c-109">Porady: debugowanie aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="58c6c-109">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="58c6c-110">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="58c6c-110">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
