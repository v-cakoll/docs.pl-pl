---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 27402017e5e79194578719fd0c921dfc1e047b80
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512963"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Zarządzanie skażonymi komunikatami odrzucone.  
  
## <a name="description"></a>Opis  
 Śledzenie wskazuje, że zarządzanie skażonymi komunikatami został napotkany i następnie odrzucenia. W takim przypadku `ReceiveErrorHandling` właściwość NetMsmqBinding lub MsmqIntegrationBinding jest ustawiona na `Reject`. Odrzucone komunikat jest dostarczany do nadawcy [kolejki utraconych wiadomości](https://go.microsoft.com/fwlink/?LinkId=99544).  
  
 Zobacz [obsługi komunikatów Poison](https://go.microsoft.com/fwlink/?LinkId=99546) więcej informacji na temat po wiadomości stają się zanieczyszczone oraz sposób konfigurowania usługi odpowiednio je obsłużyć. Zobacz [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) dodatkowe szczegóły dotyczące odrzuconych komunikatów oznacza w usłudze MSMQ.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Obsługa komunikatów poison](https://go.microsoft.com/fwlink/?LinkId=99546)  
 [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548)
