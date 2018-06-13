---
title: Usługa MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 5e157da25829a0741de988d1d6dde0318a93b109
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475289"
---
# <a name="msmq"></a><span data-ttu-id="692e8-102">Usługa MSMQ</span><span class="sxs-lookup"><span data-stu-id="692e8-102">MSMQ</span></span>
<span data-ttu-id="692e8-103">W aplikacji, usługi MSMQ nie dodatkowe działania jest przekazywana z kanału w kolejce do usługi MSMQ, a usługi MSMQ do kanału w kolejce.</span><span class="sxs-lookup"><span data-stu-id="692e8-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="692e8-104">Ponadto identyfikator wiadomości MSMQ i identyfikator komunikatu SOAP (wraz z identyfikator działania, jeśli taka istnieje) są śledzone w ramach śladów zwrócony w operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="692e8-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="692e8-105">Identyfikator wiadomości MSMQ i identyfikator komunikatu SOAP (wraz z działania, którego identyfikator, jeśli istnieje) są śledzone w ramach śladów zwrócony w operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="692e8-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="692e8-106">Wymagane transferów w operacji odbierania są wykonywane podobnie do innego transportu (odbieranie bajtów -> procesu wiadomości -> operacji).</span><span class="sxs-lookup"><span data-stu-id="692e8-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
