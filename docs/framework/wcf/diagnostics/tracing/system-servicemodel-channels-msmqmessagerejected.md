---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 4feeb1b57d79c7445d51f5d688b0a9f55e761542
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997539"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
Usługa MSMQ odrzucił komunikat.  
  
## <a name="description"></a>Opis  
 Ślad wskazuje, że wiadomości usługi MSMQ została odrzucona.  
  
 Gdy (używany z NetMsmqBinding lub MsmqIntegrationBinding) Windows Communication Foundation (WCF) nie będzie mógł je przetworzyć można odrzucić wiadomości usługi MSMQ. Takie wiadomości są określane jako skażone komunikaty. Zarządzanie skażonymi komunikatami zostanie odrzucone po `ReceiveErrorHandling` NetMsmqBinding lub MsmqIntegrationBinding zostaje ustalona `Reject`. Odrzucone komunikat jest dostarczany do nadawcy [kolejki utraconych wiadomości](https://go.microsoft.com/fwlink/?LinkID=99544).  
  
 Zobacz [obsługi komunikatów Poison](https://go.microsoft.com/fwlink/?LinkID=99546) więcej informacji na temat po wiadomości stają się zanieczyszczone oraz sposób konfigurowania usługi odpowiednio je obsłużyć.  
  
 Zobacz [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) dodatkowe szczegóły dotyczące odrzuconych komunikatów oznacza w usłudze MSMQ.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Obsługa komunikatów poison](https://go.microsoft.com/fwlink/?LinkID=99546)
- [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548)
