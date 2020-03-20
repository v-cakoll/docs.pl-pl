---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674813"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Zatruta wiadomość odrzucona.  
  
## <a name="description"></a>Opis  

 Ślad wskazuje, że wiadomość trucizny została napotkana, a następnie odrzucona. Dzieje się `ReceiveErrorHandling` tak, gdy właściwość na NetMsmqBinding lub MsmqIntegrationBinding jest ustawiona na `Reject`. Odrzucona wiadomość zostanie dostarczona z powrotem do [kolejki utraconych wiadomości nadawcy](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
 Aby uzyskać więcej informacji o tym, kiedy wiadomości stają się zatrute i jak skonfigurować usługę do ich właściwego obchodzenia się z nimi, zobacz [Obsługa trujących wiadomości](../../feature-details/poison-message-handling.md). Aby uzyskać więcej informacji na temat tego, co oznacza odrzucona wiadomość w programie MSMQ, zobacz [MQMarkMessageRejed .](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Obsługa zatruć-message](../../feature-details/poison-message-handling.md)
- [MQMarkMessageZasunięty](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
