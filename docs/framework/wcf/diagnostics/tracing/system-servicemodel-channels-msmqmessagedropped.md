---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55b489bcad85eff5adba16f6f40493c88e476505
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
Usługa MSMQ porzucony komunikat.  
  
## <a name="description"></a>Opis  
 Śledzenie wskazuje, że wiadomości MSMQ został porzucony. Wiadomości usługi MSMQ można porzucić kiedy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (używany z NetMsmqBinding lub MsmqIntegrationBinding) nie może ich przetworzyć. Takie komunikaty są określane jako skażone wiadomości.  
  
 Trująca wiadomość jest przerywane po `ReceiveErrorHandling` ma ustawioną właściwość NetMsmqBinding lub MsmqIntegrationBinding `Drop`. Porzucone wiadomości zostanie usunięta z kolejki i nie jest już możliwe do odzyskania.  
  
 Zobacz [obsługi wiadomości Poison](http://go.microsoft.com/fwlink/?LinkID=99546) więcej szczegółów na kiedy zaczynają skażone wiadomości i konfigurowania usługi do odpowiednią obsługę.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Poison komunikat — Obsługa](http://go.microsoft.com/fwlink/?LinkID=99546)
