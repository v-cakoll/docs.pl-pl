---
title: "Usługa MSMQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a827cc89917a26552c77dc742cb12aa2d49d1d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="msmq"></a><span data-ttu-id="57b4b-102">Usługa MSMQ</span><span class="sxs-lookup"><span data-stu-id="57b4b-102">MSMQ</span></span>
<span data-ttu-id="57b4b-103">W aplikacji, usługi MSMQ nie dodatkowe działania jest przekazywana z kanału w kolejce do usługi MSMQ, a usługi MSMQ do kanału w kolejce.</span><span class="sxs-lookup"><span data-stu-id="57b4b-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="57b4b-104">Ponadto identyfikator wiadomości MSMQ i identyfikator komunikatu SOAP (wraz z identyfikator działania, jeśli taka istnieje) są śledzone w ramach śladów zwrócony w operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="57b4b-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="57b4b-105">Identyfikator wiadomości MSMQ i identyfikator komunikatu SOAP (wraz z działania, którego identyfikator, jeśli istnieje) są śledzone w ramach śladów zwrócony w operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="57b4b-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="57b4b-106">Wymagane transferów w operacji odbierania są wykonywane podobnie do innego transportu (odbieranie bajtów -> procesu wiadomości -> operacji).</span><span class="sxs-lookup"><span data-stu-id="57b4b-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
