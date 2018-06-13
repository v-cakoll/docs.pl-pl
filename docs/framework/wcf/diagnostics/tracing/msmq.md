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
# <a name="msmq"></a>Usługa MSMQ
W aplikacji, usługi MSMQ nie dodatkowe działania jest przekazywana z kanału w kolejce do usługi MSMQ, a usługi MSMQ do kanału w kolejce.  
  
 Ponadto identyfikator wiadomości MSMQ i identyfikator komunikatu SOAP (wraz z identyfikator działania, jeśli taka istnieje) są śledzone w ramach śladów zwrócony w operacji wysyłania.  
  
 Identyfikator wiadomości MSMQ i identyfikator komunikatu SOAP (wraz z działania, którego identyfikator, jeśli istnieje) są śledzone w ramach śladów zwrócony w operacji odbierania.  
  
 Wymagane transferów w operacji odbierania są wykonywane podobnie do innego transportu (odbieranie bajtów -> procesu wiadomości -> operacji).
