---
title: 'Rozwiązywanie problemów: debugowanie usług systemu Windows'
description: Wprowadzenie do debugowania usług systemu Windows. Gdy debugujesz aplikację usługi systemu Windows, usługa i Service Manager systemu Windows współpracują.
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
ms.openlocfilehash: 935f5dcbd369ba5d723cc0e947ba708afdd590ea
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925543"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="83871-104">Rozwiązywanie problemów: debugowanie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="83871-104">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="83871-105">Gdy debugujesz aplikację usługi systemu Windows, usługa i **Service Manager systemu Windows** współpracują.</span><span class="sxs-lookup"><span data-stu-id="83871-105">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="83871-106">**Service Manager** uruchamia usługę <xref:System.ServiceProcess.ServiceBase.OnStart%2A> , wywołując metodę, a następnie czeka 30 sekund na <xref:System.ServiceProcess.ServiceBase.OnStart%2A> zwrócenie metody.</span><span class="sxs-lookup"><span data-stu-id="83871-106">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="83871-107">Jeśli metoda nie zwróci tego czasu, Menedżer pokazuje błąd, że nie można uruchomić usługi.</span><span class="sxs-lookup"><span data-stu-id="83871-107">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="83871-108">Podczas debugowania <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody zgodnie z opisem w [instrukcje: debugowanie aplikacji usługi systemu Windows](how-to-debug-windows-service-applications.md), musisz mieć świadomość tego 30-sekundowego okresu.</span><span class="sxs-lookup"><span data-stu-id="83871-108">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="83871-109">Jeśli umieścisz punkt przerwania w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodzie i nie ustawisz go w ciągu 30 sekund, Menedżer nie uruchomi usługi.</span><span class="sxs-lookup"><span data-stu-id="83871-109">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83871-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83871-110">See also</span></span>

- [<span data-ttu-id="83871-111">Instrukcje: Debugowanie aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="83871-111">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="83871-112">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="83871-112">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
