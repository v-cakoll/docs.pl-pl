---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: fac3682a955ed0caf21fdb1dea48672bf3bdea77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704579"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Usługa protokołu WS-AT upłynął limit czasu oczekiwania na odpowiedź na komunikat o wyniku z uczestnika nietrwałego. Wyniku transakcji może być w stanie wątpliwości, jeśli zwróci uczestnika.  
  
## <a name="description"></a>Opis  
 Śledzone, gdy Volatile uczestnika, który zdecydował się na zatwierdzenia lub przerwania, ale nie odpowiedział na żądanie zatwierdzenia lub wycofania w określonym czasie.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Upewnij się, że wszyscy uczestnicy Volatile mogą odpowiadać w określonym czasie. Domyślny okres to 180 sekund.  Jeśli to za mało, zwiększyć `VolatileOutcomeDelay` zasady WS-AT czasomierza.  
  
## <a name="see-also"></a>Zobacz także
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
