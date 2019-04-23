---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 562399c1d45dc73c7c88bd165e9f95ee1bcfa19d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125085"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Zarządzanie skażonymi komunikatami odrzucone.  
  
## <a name="description"></a>Opis  
 Śledzenie wskazuje, że zarządzanie skażonymi komunikatami został napotkany i następnie odrzucenia. W takim przypadku `ReceiveErrorHandling` właściwość NetMsmqBinding lub MsmqIntegrationBinding jest ustawiona na `Reject`. Odrzucone komunikat jest dostarczany do nadawcy [kolejki utraconych wiadomości](https://go.microsoft.com/fwlink/?LinkId=99544).  
  
 Zobacz [obsługi komunikatów Poison](https://go.microsoft.com/fwlink/?LinkId=99546) więcej informacji na temat po wiadomości stają się zanieczyszczone oraz sposób konfigurowania usługi odpowiednio je obsłużyć. Zobacz [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) dodatkowe szczegóły dotyczące odrzuconych komunikatów oznacza w usłudze MSMQ.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Obsługa komunikatów poison](https://go.microsoft.com/fwlink/?LinkId=99546)
- [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548)
