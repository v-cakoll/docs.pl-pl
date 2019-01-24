---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 0dc74b784d8a9ed3ab27bb4b8d3de34143f6ce07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639487"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="d6762-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="d6762-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="d6762-103">Id: 139</span><span class="sxs-lookup"><span data-stu-id="d6762-103">Id: 139</span></span>  
  
 <span data-ttu-id="d6762-104">Ważność: Błąd</span><span class="sxs-lookup"><span data-stu-id="d6762-104">Severity: Error</span></span>  
  
 <span data-ttu-id="d6762-105">Kategoria: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="d6762-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="d6762-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d6762-106">Description</span></span>  
 <span data-ttu-id="d6762-107">To zdarzenie oznacza, że wpis dziennika odzyskiwania koordynatora został uszkodzony i nie może być zdeserializowany.</span><span class="sxs-lookup"><span data-stu-id="d6762-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="d6762-108">Z tego błędu może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="d6762-108">Data loss may result from this error.</span></span> <span data-ttu-id="d6762-109">Listy zdarzeń identyfikator transakcji, odzyskiwania danych (kodowanie Base64), wyjątków, nazwa procesu i proces identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="d6762-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6762-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6762-110">See also</span></span>
- [<span data-ttu-id="d6762-111">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="d6762-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="d6762-112">Informacje ogólne o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d6762-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
