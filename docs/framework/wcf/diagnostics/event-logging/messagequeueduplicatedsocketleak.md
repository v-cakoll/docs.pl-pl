---
title: MessageQueueDuplicatedSocketLeak
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ea58a826920d440ab903270f796a3d94d17ad47
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="cd380-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="cd380-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="cd380-103">Identyfikator: 165</span><span class="sxs-lookup"><span data-stu-id="cd380-103">Id: 165</span></span>  
  
 <span data-ttu-id="cd380-104">Ważność: błąd</span><span class="sxs-lookup"><span data-stu-id="cd380-104">Severity: Error</span></span>  
  
 <span data-ttu-id="cd380-105">Kategoria: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="cd380-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="cd380-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cd380-106">Description</span></span>  
 <span data-ttu-id="cd380-107">To zdarzenie oznacza, że wystąpił błąd podczas wysyłania zduplikowanego gniazda.</span><span class="sxs-lookup"><span data-stu-id="cd380-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="cd380-108">Ta dojścia jest teraz ujawnione w procesie.</span><span class="sxs-lookup"><span data-stu-id="cd380-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="cd380-109">Zdarzenie zawiera źródła, wyjątek, nazwa procesu i identyfikatora procesu.</span><span class="sxs-lookup"><span data-stu-id="cd380-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd380-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd380-110">See Also</span></span>  
 [<span data-ttu-id="cd380-111">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="cd380-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="cd380-112">Informacje ogólne o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="cd380-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
