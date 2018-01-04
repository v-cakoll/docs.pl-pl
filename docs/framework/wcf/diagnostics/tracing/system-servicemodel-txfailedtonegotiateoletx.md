---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb632712a4f7855c16593ac313221f588040d0fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
Nie negocjacji protokołu OleTransactions dla kontekstu koordynacji określony.  
  
## <a name="description"></a>Opis  
 Śledzone podczas transakcji przychodzącej z informacjami o OleTx nie może użyć dołączone informacje OleTx i będzie awaryjne można zamiast niego protokołu WS-AT.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Wskazuje potencjalny problem z RPC usługi MSDTC komunikacji między komputerami. Jeśli wiele z tych śladów pojawiają się w dzienniku, może spowodować radykalne spadek wydajności.  Jeśli OleTx nie jest wymagana, ustaw `OleTxUpgradeEnabled` na 0 w konfiguracji rejestru WS-AT.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
