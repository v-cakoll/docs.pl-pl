---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 3f51d1269f5ca89f4f02257c8accef3423aa7eb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472686"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="63aa1-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="63aa1-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="63aa1-103">Identyfikator: 139</span><span class="sxs-lookup"><span data-stu-id="63aa1-103">Id: 139</span></span>  
  
 <span data-ttu-id="63aa1-104">Ważność: błąd</span><span class="sxs-lookup"><span data-stu-id="63aa1-104">Severity: Error</span></span>  
  
 <span data-ttu-id="63aa1-105">Kategoria: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="63aa1-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="63aa1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="63aa1-106">Description</span></span>  
 <span data-ttu-id="63aa1-107">To zdarzenie oznacza, że pozycji dziennika odzyskiwania koordynatora był uszkodzony i nie może być zdeserializowany.</span><span class="sxs-lookup"><span data-stu-id="63aa1-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="63aa1-108">Z tego błędu może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="63aa1-108">Data loss may result from this error.</span></span> <span data-ttu-id="63aa1-109">Listy zdarzeń identyfikator transakcji, dane odzyskiwania (kodowanie Base64), wyjątek, nazwa procesu i procesu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="63aa1-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63aa1-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63aa1-110">See Also</span></span>  
 [<span data-ttu-id="63aa1-111">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="63aa1-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="63aa1-112">Informacje ogólne o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="63aa1-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
