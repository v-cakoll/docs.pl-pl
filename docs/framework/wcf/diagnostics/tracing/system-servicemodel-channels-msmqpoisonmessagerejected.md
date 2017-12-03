---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55ae2ed6ac8a02218fa4c13063fb8b8a8c474fd8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Trująca wiadomość została odrzucona.  
  
## <a name="description"></a>Opis  
 Śledzenie wskazuje, że Trująca wiadomość została napotkano i następnie odrzucone. W takim przypadku `ReceiveErrorHandling` ma ustawioną właściwość NetMsmqBinding lub MsmqIntegrationBinding `Reject`. Odrzucone wiadomości jest dostarczany do nadawcy [kolejki utraconych wiadomości](http://go.microsoft.com/fwlink/?LinkId=99544).  
  
 Zobacz [obsługi wiadomości Poison](http://go.microsoft.com/fwlink/?LinkId=99546) więcej szczegółów na kiedy zaczynają skażone wiadomości i konfigurowania usługi do odpowiednią obsługę. Zobacz [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) uzyskać więcej informacji dotyczących komunikatów odrzuconych oznacza w usłudze MSMQ.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Poison komunikat — Obsługa](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)
