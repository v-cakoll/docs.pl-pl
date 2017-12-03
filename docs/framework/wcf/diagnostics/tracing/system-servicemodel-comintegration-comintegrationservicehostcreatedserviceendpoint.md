---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 474895e7fbcf1b9ed7ad7da6d28313ae4894f720
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Nie można przenieść ani usunąć wiadomości.  
  
## <a name="description"></a>Opis  
 Śledzenie wskazuje wystąpił błąd podczas próby przenoszenia, usunąć lub odrzucić wiadomości MSMQ.  
  
 Wiadomości usługi MSMQ są zatrudnieni przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (w przypadku użycia z NetMsmqBinding lub MsmqIntegrationBinding). Ślad jest powiązany z wybranym wartość `ReceiveErrorHandling` właściwość NetMsmqBinding lub MsmqIntegrationBinding.  
  
 Ta śledzenia nie jest świadczy o ogólny błąd systemu. Jednak wskazuje, że wybrana zanieczyszczonych dyspozycji wiadomości nie powiodło się dla wiadomości. Zobacz [obsługi wiadomości Poison](http://go.microsoft.com/fwlink/?LinkID=99546) więcej szczegółów na kiedy zaczynają skażone wiadomości i konfigurowania usługi do odpowiednią obsługę.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
