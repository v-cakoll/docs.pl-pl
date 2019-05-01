---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 9434f2f902a50a37fb3efee22fd3b18b33af9129
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997462"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a>Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
Usługa protokołu WS-AT odebrała komunikat Prepared lub Replay od nierozpoznanego uczestnika nietrwałego. Zwrócono błąd do uczestnika oświadcza, że w razie wątpliwości wyniku transakcji.  
  
## <a name="description"></a>Opis  
 Śledzone, gdy lokalny Menedżer transakcji odbiera komunikat Prepared lub Replay od lotnych rejestracji, który już ma zapomniano.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Zbadaj możliwych przyczyn opóźnień komunikaty pochodzące z uczestnika nietrwałego.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
