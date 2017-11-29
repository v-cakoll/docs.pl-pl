---
title: CoordinatorRecoveryLogEntryCorrupt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1db6f8dc4136623f35767c122dbea46fd4706b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="e3fe7-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="e3fe7-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="e3fe7-103">Identyfikator: 139</span><span class="sxs-lookup"><span data-stu-id="e3fe7-103">Id: 139</span></span>  
  
 <span data-ttu-id="e3fe7-104">Ważność: błąd</span><span class="sxs-lookup"><span data-stu-id="e3fe7-104">Severity: Error</span></span>  
  
 <span data-ttu-id="e3fe7-105">Kategoria: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="e3fe7-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="e3fe7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e3fe7-106">Description</span></span>  
 <span data-ttu-id="e3fe7-107">To zdarzenie oznacza, że pozycji dziennika odzyskiwania koordynatora był uszkodzony i nie może być zdeserializowany.</span><span class="sxs-lookup"><span data-stu-id="e3fe7-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="e3fe7-108">Z tego błędu może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="e3fe7-108">Data loss may result from this error.</span></span> <span data-ttu-id="e3fe7-109">Listy zdarzeń identyfikator transakcji, dane odzyskiwania (kodowanie Base64), wyjątek, nazwa procesu i procesu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="e3fe7-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3fe7-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3fe7-110">See Also</span></span>  
 [<span data-ttu-id="e3fe7-111">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e3fe7-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="e3fe7-112">Informacje ogólne o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="e3fe7-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
