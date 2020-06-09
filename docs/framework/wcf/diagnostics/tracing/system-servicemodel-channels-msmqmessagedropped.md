---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 4b016f53a75d9527a5cd1bbadacacd650b7f35b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601920"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
Wiadomość została porzucona przez usługę MSMQ.  
  
## <a name="description"></a>Opis  
 Śledzenie wskazuje, że komunikat usługi MSMQ został porzucony. Komunikaty usługi MSMQ można porzucić, gdy Windows Communication Foundation (WCF) (używane z usługą Msmqbinding lub MsmqIntegrationBinding) nie może ich przetworzyć. Takie komunikaty nazywa się skażonymi komunikatami.  
  
 Trująca wiadomość jest usuwana, gdy `ReceiveErrorHandling` Właściwość w sieci msmqbinding lub MsmqIntegrationBinding jest ustawiona na `Drop` . Usunięty komunikat jest usuwany z kolejki i nie jest już możliwy do odzyskania.  
  
 Aby uzyskać więcej informacji na temat sytuacji, w których komunikaty stają się trujące i jak skonfigurować usługę do odpowiednich potrzeb, zobacz [Obsługa komunikatów trujących](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
- [Obsługa komunikatów trujących](../../feature-details/poison-message-handling.md)
