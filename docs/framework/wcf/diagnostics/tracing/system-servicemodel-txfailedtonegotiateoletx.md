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
ms.openlocfilehash: 6c0e688e1f24171494b4adaae964ac1fc2be2309
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
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
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
