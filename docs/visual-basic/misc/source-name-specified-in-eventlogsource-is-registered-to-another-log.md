---
title: Nazwa źródła w parametru EventLogSource została zarejestrowana do dziennika, inne niż określone w EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 4de98bef87b871036c3c5730ff09cf94c1df2918
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584574"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="20149-102">Nazwa źródła w parametru EventLogSource została zarejestrowana do dziennika, inne niż określone w EventLogName</span><span class="sxs-lookup"><span data-stu-id="20149-102">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>
<span data-ttu-id="20149-103">`EventLog` Próbuje do odwoływania się do źródła, który jest zarejestrowany w innym dzienniku.</span><span class="sxs-lookup"><span data-stu-id="20149-103">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="20149-104">Jeśli piszesz wpisów do dziennika zdarzeń, należy określić <xref:System.Diagnostics.EventLog.Source%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="20149-104">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="20149-105"><xref:System.Diagnostics.EventLog.Source%2A> Właściwość rejestruje składnika z dziennika zdarzeń jako poprawne źródło wpisów.</span><span class="sxs-lookup"><span data-stu-id="20149-105">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="20149-106">Pojedyncze źródło może być skojarzony z (i w związku z tym zapis wpisów, aby) tylko jeden dziennik zdarzeń w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="20149-106">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="20149-107">Domyślnie, jeśli zostanie podjęta próba zapisu bez po raz pierwszy masz zarejestrowane składnika jako poprawne źródło, system automatycznie rejestruje źródło dziennika zdarzeń, przy użyciu wartości <xref:System.Diagnostics.EventLog.Source%2A> właściwość jako ciąg źródłowy.</span><span class="sxs-lookup"><span data-stu-id="20149-107">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="20149-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="20149-108">To correct this error</span></span>  
  
-   <span data-ttu-id="20149-109">Upewnij się, że źródło jest zarejestrowany poprawną dziennika.</span><span class="sxs-lookup"><span data-stu-id="20149-109">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="20149-110">Aby to zrobić, należy użyć <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody lub jednej z jej przeciążeń, aby określić ciąg, który unikatowo identyfikuje składnika w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="20149-110">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20149-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20149-111">See also</span></span>
- [<span data-ttu-id="20149-112">Administrowanie usługą dzienników zdarzeń</span><span class="sxs-lookup"><span data-stu-id="20149-112">Administering Event Logs</span></span>](https://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)
- [<span data-ttu-id="20149-113">Odwołania do dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="20149-113">Event Log References</span></span>](https://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)
- [<span data-ttu-id="20149-114">Instrukcje: Dodaj aplikację jako źródło wpisów dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="20149-114">How to: Add Your Application as a Source of Event Log Entries</span></span>](https://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)
- [<span data-ttu-id="20149-115">Instrukcje: Usuń źródła zdarzeń</span><span class="sxs-lookup"><span data-stu-id="20149-115">How to: Remove an Event Source</span></span>](https://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
