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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15be4b6bfb84a0aa843e3d62861a9195e125a04e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="msmq"></a>Usługa MSMQ
W aplikacji, usługi MSMQ nie dodatkowe działania jest przekazywana z kanału w kolejce do usługi MSMQ, a usługi MSMQ do kanału w kolejce.  
  
 Ponadto identyfikator wiadomości MSMQ i identyfikator komunikatu SOAP (wraz z identyfikator działania, jeśli taka istnieje) są śledzone w ramach śladów zwrócony w operacji wysyłania.  
  
 Identyfikator wiadomości MSMQ i identyfikator komunikatu SOAP (wraz z działania, którego identyfikator, jeśli istnieje) są śledzone w ramach śladów zwrócony w operacji odbierania.  
  
 Wymagane transferów w operacji odbierania są wykonywane podobnie do innego transportu (odbieranie bajtów -> procesu wiadomości -> operacji).
