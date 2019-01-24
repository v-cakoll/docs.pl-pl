---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 6aecc8f808d42c0096f6caef0574c72db6c53079
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528670"
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
