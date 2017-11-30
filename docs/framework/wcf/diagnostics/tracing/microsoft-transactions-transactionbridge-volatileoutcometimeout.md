---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1992a209bb58c0a0d6f181eb2f1ec546d50372ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Usługa protokołu WS-AT upłynął limit czasu oczekiwania na odpowiedź na komunikat wynikowy od nietrwałego uczestnika. Jeśli uczestnik powróci, wynik transakcji może być wątpliwe.  
  
## <a name="description"></a>Opis  
 Śledzone uczestnika nietrwałego postanowiła Zatwierdź lub Przerwij, ale nie odpowiedział na żądanie zatwierdzenia lub wycofania w określonym czasie.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Upewnij się, że wszystkie osoby uczestniczące w niej Volatile są w stanie odpowiedzieć w określonym czasie. Domyślny okres czasu wynosi 180 sekund.  Jeśli jest to za mało, zwiększyć `VolatileOutcomeDelay` czasomierza zasady dla usługi WS-AT.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
