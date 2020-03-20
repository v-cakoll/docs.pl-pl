---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674789"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Nie można przenieść ani usunąć wiadomości.  
  
## <a name="description"></a>Opis  
 Śledzenie wskazuje, że wystąpił błąd podczas próby przeniesienia, usunięcia lub odrzucenia wiadomości MSMQ.  
  
 Wiadomości MSMQ są używane przez Windows Communication Foundation (WCF) (gdy są używane z NetMsmqBinding lub MsmqIntegrationBinding). Ten ślad jest związany z wybraną wartością `ReceiveErrorHandling` właściwości w netmsmqBinding lub MsmqIntegrationBinding.  
  
 Ten ślad nie wskazuje na ogólną awarię systemu. Jednak wskazuje, że wybrana dyspozycja wiadomości trująca nie powiodła się dla wiadomości. Aby uzyskać więcej informacji o tym, kiedy wiadomości stają się zatrute i jak skonfigurować usługę do ich właściwego obchodzenia się z nimi, zobacz [Obsługa trujących wiadomości](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
