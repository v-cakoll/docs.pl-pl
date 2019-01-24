---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 3b51a100677221866186b2e24f34396c012d11c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603134"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Usługa protokołu WS-AT odebrała komunikat powtarzania z trwałego uczestnika nie odpowiedział na przygotowanie. W związku z tym transakcja została przerwana.  
  
## <a name="description"></a>Opis  
 Śledzone, jeśli powtarzania wiadomość zostaje odebrana, gdy uczestnik trwałe nadal trwa przygotowywanie. Ten komunikat ma charakter niedozwolony dla tego stanu i transakcja zostanie przerwane.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Ten komunikat o błędzie może indiate, że trwałego uczestnika (w tym TransactionManagers podrzędnego) została odzyskana po awarii, chociaż jest on ustalić wyniku transakcji i jego stan żądania.  
  
## <a name="see-also"></a>Zobacz także
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
