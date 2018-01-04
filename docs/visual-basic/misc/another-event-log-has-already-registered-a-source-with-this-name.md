---
title: "Inny dziennik zdarzeń zarejestrowała już źródło o tej nazwie"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f04afd5d061a44f572d95abfb0173ad6fa2ac27
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="5bff6-102">Inny dziennik zdarzeń zarejestrowała już źródło o tej nazwie</span><span class="sxs-lookup"><span data-stu-id="5bff6-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="5bff6-103">Podjęto próbę zapisu do dziennika zdarzeń gdzie określone źródło jest zarejestrowany w innym dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5bff6-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="5bff6-104">Należy ustawić <xref:System.Diagnostics.EventLog.Source%2A> właściwości użytkownika <xref:System.Diagnostics.EventLog> wystąpienie składnika przed składnika dokona wpisu w dzienniku.</span><span class="sxs-lookup"><span data-stu-id="5bff6-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="5bff6-105">W takim przypadku system sprawdza, czy określone źródło jest zarejestrowana z dziennika zdarzeń, do którego jest pisanie składnika i wywołania <xref:System.Diagnostics.EventLog.CreateEventSource%2A> w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="5bff6-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5bff6-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5bff6-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="5bff6-107">Usuń skojarzenie źródła przy pierwszym użyciu dziennika <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> lub <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5bff6-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="5bff6-108">Zarejestruj źródło nowy dziennik.</span><span class="sxs-lookup"><span data-stu-id="5bff6-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bff6-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5bff6-109">See Also</span></span>  
 [<span data-ttu-id="5bff6-110">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="5bff6-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

