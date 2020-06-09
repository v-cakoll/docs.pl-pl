---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: dd2a0b67ec140aa2e6fe1abad8e85c0206abd8ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579024"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Przekroczono limit czasu usługi protokołu WS-AT podczas oczekiwania na odpowiedź na komunikat o wyniku z nietrwałego uczestnika. Wynik transakcji może być wątpliwy, jeśli uczestnik zwróci wartość.  
  
## <a name="description"></a>Opis  
 Śledzenie, gdy uczestnik trwały zdecydował się zatwierdzić lub przerwać, ale nie odpowiedział na żądanie zatwierdzenia lub wycofania w określonym czasie.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Upewnij się, że wszyscy uczestnicy nietrwałe mogą reagować w danym czasie. Domyślny okres to 180 sekund.  Jeśli jest to niewystarczające, należy zwiększyć `VolatileOutcomeDelay` zasady czasomierza dla usługi WS-AT.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
