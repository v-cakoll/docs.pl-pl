---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 0addf987eac62c750a3c418e1b1c431d3f9bc1b0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198949"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
Usługa MSMQ odrzucił komunikat.  
  
## <a name="description"></a>Opis  
 Ślad wskazuje, że wiadomości usługi MSMQ została odrzucona.  
  
 Gdy (używany z NetMsmqBinding lub MsmqIntegrationBinding) Windows Communication Foundation (WCF) nie będzie mógł je przetworzyć można odrzucić wiadomości usługi MSMQ. Takie wiadomości są określane jako skażone komunikaty. Zarządzanie skażonymi komunikatami zostanie odrzucone po `ReceiveErrorHandling` NetMsmqBinding lub MsmqIntegrationBinding zostaje ustalona `Reject`. Odrzucone komunikat jest dostarczany do nadawcy [kolejki utraconych wiadomości](https://go.microsoft.com/fwlink/?LinkID=99544).  
  
 Zobacz [obsługi komunikatów Poison](https://go.microsoft.com/fwlink/?LinkID=99546) więcej informacji na temat po wiadomości stają się zanieczyszczone oraz sposób konfigurowania usługi odpowiednio je obsłużyć.  
  
 Zobacz [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) dodatkowe szczegóły dotyczące odrzuconych komunikatów oznacza w usłudze MSMQ.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Obsługa komunikatów poison](https://go.microsoft.com/fwlink/?LinkID=99546)  
 [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548)
