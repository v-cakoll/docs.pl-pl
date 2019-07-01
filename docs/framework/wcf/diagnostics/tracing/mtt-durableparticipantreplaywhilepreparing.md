---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 93354fbdd0c1726280526ca07a8b3dd1c57c8a25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486772"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Usługa protokołu WS-AT odebrała komunikat powtarzania z trwałego uczestnika nie odpowiedział na przygotowanie. W związku z tym transakcja została przerwana.  
  
## <a name="description"></a>Opis  
 Śledzone, jeśli powtarzania wiadomość zostaje odebrana, gdy uczestnik trwałe nadal trwa przygotowywanie. Ten komunikat ma charakter niedozwolony dla tego stanu i transakcja zostanie przerwane.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów

Ten komunikat o błędzie może wskazywać, że trwałego uczestnika (w tym TransactionManagers podrzędnego) została odzyskana po awarii; jednak nie ma pewności o wyniku transakcji i jego stan żądania.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
