---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 3fa5ec62c5e8ac83f3f81fb406499b7e596b3dac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969510"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
Usługa MSMQ porzucić komunikatu.  
  
## <a name="description"></a>Opis  
 Śledzenia wskazuje, że wiadomości usługi MSMQ został porzucony. Gdy (używany z NetMsmqBinding lub MsmqIntegrationBinding) Windows Communication Foundation (WCF) nie będzie mógł je przetworzyć można porzucić wiadomości usługi MSMQ. Takie wiadomości są określane jako skażone komunikaty.  
  
 Zarządzanie skażonymi komunikatami zostało porzucone, kiedy `ReceiveErrorHandling` NetMsmqBinding lub MsmqIntegrationBinding zostaje ustalona `Drop`. Porzucone komunikat zostanie usunięty z kolejki i nie jest już możliwe do odzyskania.  
  
 Zobacz [obsługi komunikatów Poison](https://go.microsoft.com/fwlink/?LinkID=99546) więcej informacji na temat po wiadomości stają się zanieczyszczone oraz sposób konfigurowania usługi odpowiednio je obsłużyć.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Obsługa komunikatów poison](https://go.microsoft.com/fwlink/?LinkID=99546)
