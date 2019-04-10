---
title: MessageQueueDuplicatedSocketLeak
ms.date: 03/30/2017
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
ms.openlocfilehash: 8533d53dc6a2d4510ffec2dcbf0e9bef15cde6ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206125"
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="c3cda-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="c3cda-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="c3cda-103">Id: 165</span><span class="sxs-lookup"><span data-stu-id="c3cda-103">Id: 165</span></span>  
  
 <span data-ttu-id="c3cda-104">Ważność: Błąd</span><span class="sxs-lookup"><span data-stu-id="c3cda-104">Severity: Error</span></span>  
  
 <span data-ttu-id="c3cda-105">Kategoria: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="c3cda-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="c3cda-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c3cda-106">Description</span></span>  
 <span data-ttu-id="c3cda-107">To zdarzenie oznacza, że wystąpił błąd podczas wysyłania zduplikowane gniazda.</span><span class="sxs-lookup"><span data-stu-id="c3cda-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="c3cda-108">Tego dojścia jest teraz ujawnione w procesie.</span><span class="sxs-lookup"><span data-stu-id="c3cda-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="c3cda-109">Zdarzenie zawiera źródła, wyjątków, nazwa procesu i identyfikatora procesu.</span><span class="sxs-lookup"><span data-stu-id="c3cda-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3cda-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3cda-110">See also</span></span>

- [<span data-ttu-id="c3cda-111">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="c3cda-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="c3cda-112">Informacje ogólne o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="c3cda-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
