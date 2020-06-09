---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: c388a9dc3569e20639de09abc5f4941b73c561ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578054"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
Wiadomość została odrzucona przez usługę MSMQ.  
  
## <a name="description"></a>Opis  
 Ten ślad wskazuje, że wiadomość usługi MSMQ została odrzucona.  
  
 Komunikaty usługi MSMQ można odrzucić, gdy Windows Communication Foundation (WCF) (używane z usługą Msmqbinding lub MsmqIntegrationBinding) nie może ich przetworzyć. Takie komunikaty nazywa się skażonymi komunikatami. Trująca wiadomość jest odrzucana, gdy `ReceiveErrorHandling` Właściwość w sieci msmqbinding lub MsmqIntegrationBinding jest ustawiona na `Reject` . Odrzucony komunikat jest dostarczany z powrotem do [kolejki utraconych wiadomości](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)nadawcy.  
  
 Aby uzyskać więcej informacji na temat sytuacji, w których komunikaty stają się trujące i jak skonfigurować usługę do odpowiednich potrzeb, zobacz [Obsługa komunikatów trujących](../../feature-details/poison-message-handling.md).  
  
 Aby uzyskać więcej informacji na temat tego, co oznacza komunikat odrzucony w usłudze MSMQ, zobacz [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
- [Obsługa komunikatów trujących](../../feature-details/poison-message-handling.md)
- [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
