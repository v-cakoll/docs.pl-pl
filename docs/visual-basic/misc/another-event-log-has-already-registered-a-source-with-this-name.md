---
title: Inny dziennika zdarzeń została już zarejestrowana źródło o tej nazwie
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: b32169b79521ec7d0c429e1dce641aca9d747bb1
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58032150"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="395db-102">Inny dziennika zdarzeń została już zarejestrowana źródło o tej nazwie</span><span class="sxs-lookup"><span data-stu-id="395db-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="395db-103">Nastąpiła próba zapisu do dziennika zdarzeń, gdzie określona źródłowa jest zarejestrowany w innym dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="395db-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="395db-104">Należy ustawić <xref:System.Diagnostics.EventLog.Source%2A> właściwości usługi <xref:System.Diagnostics.EventLog> wystąpienie składnika przed składnika zapisuje wpis dziennika.</span><span class="sxs-lookup"><span data-stu-id="395db-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="395db-105">W takim przypadku system sprawdza, czy określone źródło jest zarejestrowany w dzienniku zdarzeń, do którego jest pisanie składnika i wywołania <xref:System.Diagnostics.EventLog.CreateEventSource%2A> w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="395db-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="395db-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="395db-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="395db-107">Usuń skojarzenie źródła z pierwszym przy użyciu dziennika <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> lub <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="395db-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="395db-108">Zarejestruj nowy dziennik źródła.</span><span class="sxs-lookup"><span data-stu-id="395db-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395db-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="395db-109">See also</span></span>

- [<span data-ttu-id="395db-110">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="395db-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
