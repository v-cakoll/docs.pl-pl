---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a00a6a06fd5214f1f65bdb6369839d717078da77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Usługa protokołu WS-AT odebrał komunikat powtarzania od trwałego uczestnika, który nie odpowiada na przygotowanie. W rezultacie transakcja została przerwana.  
  
## <a name="description"></a>Opis  
 Śledzone, gdy zostaje otrzymany komunikat powtarzania, gdy nadal przygotowuje trwałego uczestnika. Jest to niedozwolone komunikatu dla tego stanu i transakcja ma być przerwane.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Ten komunikat o błędzie może indiate, że trwałego uczestnika (w tym TransactionManagers podrzędnego) odzyskał sprawność po awarii, jednak jest nieznany wynik transakcji i jego stan żądania.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
