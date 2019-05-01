---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: faf4a07badb71588c601cd9390e4d8e3f187e629
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969653"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="099e2-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="099e2-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="099e2-103">Id: 139</span><span class="sxs-lookup"><span data-stu-id="099e2-103">Id: 139</span></span>  
  
 <span data-ttu-id="099e2-104">Ważność: Błąd</span><span class="sxs-lookup"><span data-stu-id="099e2-104">Severity: Error</span></span>  
  
 <span data-ttu-id="099e2-105">Kategoria: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="099e2-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="099e2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="099e2-106">Description</span></span>  
 <span data-ttu-id="099e2-107">To zdarzenie oznacza, że wpis dziennika odzyskiwania koordynatora został uszkodzony i nie może być zdeserializowany.</span><span class="sxs-lookup"><span data-stu-id="099e2-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="099e2-108">Z tego błędu może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="099e2-108">Data loss may result from this error.</span></span> <span data-ttu-id="099e2-109">Listy zdarzeń identyfikator transakcji, odzyskiwania danych (kodowanie Base64), wyjątków, nazwa procesu i proces identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="099e2-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="099e2-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="099e2-110">See also</span></span>

- [<span data-ttu-id="099e2-111">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="099e2-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="099e2-112">Informacje ogólne o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="099e2-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
