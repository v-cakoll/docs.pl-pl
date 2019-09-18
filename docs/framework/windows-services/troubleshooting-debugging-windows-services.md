---
title: 'Rozwiązywanie problemów: Debugowanie usług systemu Windows'
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
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="c72d6-102">Rozwiązywanie problemów: Debugowanie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c72d6-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="c72d6-103">Gdy debugujesz aplikację usługi systemu Windows, usługa i **Service Manager systemu Windows** współpracują.</span><span class="sxs-lookup"><span data-stu-id="c72d6-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="c72d6-104">**Service Manager** uruchamia usługę, wywołując <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę, a następnie czeka <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 30 sekund na zwrócenie metody.</span><span class="sxs-lookup"><span data-stu-id="c72d6-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="c72d6-105">Jeśli metoda nie zwróci tego czasu, Menedżer pokazuje błąd, że nie można uruchomić usługi.</span><span class="sxs-lookup"><span data-stu-id="c72d6-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="c72d6-106">Podczas debugowania <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody zgodnie z opisem w [temacie How to: Debuguj aplikacje](how-to-debug-windows-service-applications.md)usług systemu Windows, musisz mieć świadomość, że ten 30-sekundowy okres.</span><span class="sxs-lookup"><span data-stu-id="c72d6-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="c72d6-107">Jeśli umieścisz punkt przerwania w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodzie i nie ustawisz go w ciągu 30 sekund, Menedżer nie uruchomi usługi.</span><span class="sxs-lookup"><span data-stu-id="c72d6-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c72d6-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c72d6-108">See also</span></span>

- [<span data-ttu-id="c72d6-109">Instrukcje: Debuguj aplikacje usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c72d6-109">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="c72d6-110">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c72d6-110">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
