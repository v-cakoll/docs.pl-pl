---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 0a28eec659b48d5add4c53bc8c16972892e65099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487909"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Nie można przenieść ani usunąć wiadomości.  
  
## <a name="description"></a>Opis  
 Śledzenie wskazuje wystąpił błąd podczas próby przenoszenia, usunąć lub odrzucić wiadomości MSMQ.  
  
 Wiadomości usługi MSMQ są wykorzystywane przez Windows Communication Foundation (WCF) (w przypadku użycia z NetMsmqBinding lub MsmqIntegrationBinding). Ślad jest powiązany z wybranym wartość `ReceiveErrorHandling` właściwość NetMsmqBinding lub MsmqIntegrationBinding.  
  
 Ta śledzenia nie jest świadczy o ogólny błąd systemu. Jednak wskazuje, że wybrana zanieczyszczonych dyspozycji wiadomości nie powiodło się dla wiadomości. Zobacz [obsługi wiadomości Poison](http://go.microsoft.com/fwlink/?LinkID=99546) więcej szczegółów na kiedy zaczynają skażone wiadomości i konfigurowania usługi do odpowiednią obsługę.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
