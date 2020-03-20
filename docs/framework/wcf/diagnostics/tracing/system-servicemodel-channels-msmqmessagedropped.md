---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674799"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
Usługa MSMQ upuściła wiadomość.  
  
## <a name="description"></a>Opis  
 Śledzenie wskazuje, że komunikat usługi MSMQ został porzucony. Komunikaty usługi MSMQ mogą zostać usunięte, gdy program Windows Communication Foundation (WCF) (używany z programem NetMsmqBinding lub MsmqIntegrationBinding) nie jest w stanie ich przetworzyć. Takie wiadomości są określane jako wiadomości trucizny.  
  
 Komunikat o trucinie `ReceiveErrorHandling` jest odrzucany, gdy właściwość na NetMsmqBinding `Drop`lub MsmqIntegrationBinding jest ustawiona na . Porzucona wiadomość jest usuwana z kolejki i nie można jej już odzyskać.  
  
 Aby uzyskać więcej informacji o tym, kiedy wiadomości stają się zatrute i jak skonfigurować usługę do ich właściwego obchodzenia się z nimi, zobacz [Obsługa trujących wiadomości](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Obsługa zatruć-message](../../feature-details/poison-message-handling.md)
