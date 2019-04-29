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
# <a name="msmq"></a>Usługa MSMQ
W aplikacji usługi MSMQ żadne dodatkowe działanie jest przenoszona z umieszczonych w kolejce kanału usługi MSMQ i z usługi MSMQ do kanału umieszczonych w kolejce.  
  
 Ponadto identyfikator wiadomości usługi MSMQ i identyfikator komunikatu protokołu SOAP (oraz identyfikator działania, jeśli taka istnieje) są śledzone w ramach śladów kanału umieszczonych w kolejce na operację wysyłania.  
  
 Identyfikator wiadomości usługi MSMQ i identyfikator komunikatu protokołu SOAP (wraz z działanie, którego identyfikator, jeśli taki istnieje) są śledzone w ramach ślady kanału umieszczonych w kolejce operacji odbierania.  
  
 Wymagane transferów w operacji odbierania są wykonywane w podobny sposób do innego transportu (odbieranie bajtów -> Przetwórz komunikat -> operacji).
