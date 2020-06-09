---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 8b81cdcaf74aca044260495867b2c4f1de517682
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593753"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Nie można przenieść ani usunąć wiadomości.  
  
## <a name="description"></a>Opis  
 Ślad wskazuje, że wystąpił błąd podczas próby przeniesienia, usunięcia lub odrzucenia komunikatu usługi MSMQ.  
  
 Komunikaty usługi MSMQ są wykorzystywane przez Windows Communication Foundation (WCF) (gdy są używane z usługą Msmqbinding lub MsmqIntegrationBinding). Ten ślad jest powiązany z wybraną wartością `ReceiveErrorHandling` właściwości w usłudze msmqbinding lub MsmqIntegrationBinding.  
  
 Ślad ten nie wskazuje ogólnego błędu systemu. Oznacza to jednak, że dla komunikatu nie powiodła się Dyspozycja wybranego zatrucia komunikatów. Aby uzyskać więcej informacji na temat sytuacji, w których komunikaty stają się trujące i jak skonfigurować usługę do odpowiednich potrzeb, zobacz [Obsługa komunikatów trujących](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
