---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: b64f61d25c3be87019151cbf560becd3384ec182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475634"
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
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
