---
title: Usługa MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 5e157da25829a0741de988d1d6dde0318a93b109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663729"
---
# <a name="msmq"></a><span data-ttu-id="31603-102">Usługa MSMQ</span><span class="sxs-lookup"><span data-stu-id="31603-102">MSMQ</span></span>
<span data-ttu-id="31603-103">W aplikacji usługi MSMQ żadne dodatkowe działanie jest przenoszona z umieszczonych w kolejce kanału usługi MSMQ i z usługi MSMQ do kanału umieszczonych w kolejce.</span><span class="sxs-lookup"><span data-stu-id="31603-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="31603-104">Ponadto identyfikator wiadomości usługi MSMQ i identyfikator komunikatu protokołu SOAP (oraz identyfikator działania, jeśli taka istnieje) są śledzone w ramach śladów kanału umieszczonych w kolejce na operację wysyłania.</span><span class="sxs-lookup"><span data-stu-id="31603-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="31603-105">Identyfikator wiadomości usługi MSMQ i identyfikator komunikatu protokołu SOAP (wraz z działanie, którego identyfikator, jeśli taki istnieje) są śledzone w ramach ślady kanału umieszczonych w kolejce operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="31603-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="31603-106">Wymagane transferów w operacji odbierania są wykonywane w podobny sposób do innego transportu (odbieranie bajtów -> Przetwórz komunikat -> operacji).</span><span class="sxs-lookup"><span data-stu-id="31603-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
