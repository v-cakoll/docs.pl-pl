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
ms.openlocfilehash: 8beea344d233794ddc36d7fc53db1c01be84399f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="50b7f-102">Inny dziennik zdarzeń zarejestrowała już źródło o tej nazwie</span><span class="sxs-lookup"><span data-stu-id="50b7f-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="50b7f-103">Podjęto próbę zapisu do dziennika zdarzeń gdzie określone źródło jest zarejestrowany w innym dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="50b7f-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="50b7f-104">Należy ustawić <xref:System.Diagnostics.EventLog.Source%2A> właściwości użytkownika <xref:System.Diagnostics.EventLog> wystąpienie składnika przed składnika dokona wpisu w dzienniku.</span><span class="sxs-lookup"><span data-stu-id="50b7f-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="50b7f-105">W takim przypadku system sprawdza, czy określone źródło jest zarejestrowana z dziennika zdarzeń, do którego jest pisanie składnika i wywołania <xref:System.Diagnostics.EventLog.CreateEventSource%2A> w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="50b7f-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="50b7f-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="50b7f-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="50b7f-107">Usuń skojarzenie źródła przy pierwszym użyciu dziennika <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> lub <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="50b7f-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="50b7f-108">Zarejestruj źródło nowy dziennik.</span><span class="sxs-lookup"><span data-stu-id="50b7f-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b7f-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50b7f-109">See Also</span></span>  
 [<span data-ttu-id="50b7f-110">My.Application.log — obiekt</span><span class="sxs-lookup"><span data-stu-id="50b7f-110">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="50b7f-111">Porady: usuwanie źródłem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="50b7f-111">How to: Remove an Event Source</span></span>](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)  
 [<span data-ttu-id="50b7f-112">Porady: Dodawanie aplikacji jako źródło wpisów dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="50b7f-112">How to: Add Your Application as a Source of Event Log Entries</span></span>](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)
