---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674776"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
Usługa MSMQ odrzuciła tę wiadomość.  
  
## <a name="description"></a>Opis  
 Ten ślad wskazuje, że komunikat usługi MSMQ został odrzucony.  
  
 Komunikaty usługi MSMQ można odrzucić, gdy program Windows Communication Foundation (WCF) (używany z programem NetMsmqBinding lub MsmqIntegrationBinding) nie jest w stanie ich przetworzyć. Takie wiadomości są określane jako wiadomości trucizny. Komunikat poison zostanie odrzucony, `ReceiveErrorHandling` gdy właściwość na NetMsmqBinding lub MsmqIntegrationBinding jest ustawiona na `Reject`. Odrzucona wiadomość zostanie dostarczona z powrotem do [kolejki utraconych wiadomości nadawcy](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).  
  
 Aby uzyskać więcej informacji o tym, kiedy wiadomości stają się zatrute i jak skonfigurować usługę do ich właściwego obchodzenia się z nimi, zobacz [Obsługa trujących wiadomości](../../feature-details/poison-message-handling.md).  
  
 Aby uzyskać więcej informacji na temat tego, co oznacza odrzucona wiadomość w programie MSMQ, zobacz [MQMarkMessageRejed .](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Obsługa zatruć-message](../../feature-details/poison-message-handling.md)
- [MQMarkMessageZasunięty](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
