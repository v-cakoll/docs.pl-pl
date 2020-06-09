---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2c9ea77cdd76d4593c2ee5b09a4b917677b8925f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601416"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
Nie można ukończyć negocjacji protokołu OleTransactions dla określonego kontekstu koordynacji.  
  
## <a name="description"></a>Opis  
 Śledzone w przypadku, gdy transakcja przychodząca z informacjami OleTx nie może używać dołączonych informacji OleTx i zostanie przywrócona w zamian przy użyciu protokołu WS-AT.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Wskazuje potencjalny problem z komunikacją RPC usługi MSDTC między maszynami. Jeśli wiele z tych śladów jest wyświetlanych w dzienniku, może wynikać drastyczne zmniejszenie wydajności.  Jeśli OleTx nie jest wymagana, ustaw wartość `OleTxUpgradeEnabled` 0 w konfiguracji rejestru WS-AT.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
