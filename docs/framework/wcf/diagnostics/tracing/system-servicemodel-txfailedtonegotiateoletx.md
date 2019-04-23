---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2de1aa51d58d9d86f953e027fd3f7f172e3887d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097567"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
Negocjacji protokołu OleTransactions nie można ukończyć dla kontekstu określonego koordynacji.  
  
## <a name="description"></a>Opis  
 Śledzone transakcji przychodzących z informacjami o OleTx nie może użyć dołączone informacje OleTx, gdy będzie awaryjne za pomocą WS-AT zamiast tego.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Wskazuje potencjalny problem za pomocą usługi MSDTC RPC łączności między maszynami. Jeśli wiele ślady te pojawiają się w dzienniku, może to skutkować drastycznym spadku wydajności.  Jeśli OleTx jest niepożądany, należy ustawić `OleTxUpgradeEnabled` na 0 w konfiguracji rejestru WS-AT.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
