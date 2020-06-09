---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 31fb8d466c76c7490aa80dfcab089332af4036a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589135"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Usługa protokołu WS-AT otrzymała komunikat powtarzania od trwałego uczestnika, który nie odpowiedział na przygotowanie. W związku z tym transakcja została przerwana.  
  
## <a name="description"></a>Opis  
 Śledzone w przypadku odebrania komunikatu powtarzania, gdy trwały uczestnik nadal trwa przygotowywanie. Jest to niedozwolony komunikat dla tego stanu i transakcja zostanie przerwana.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów

Otrzymanie tego błędu może wskazywać, że trwały uczestnik (w tym podrzędny TransactionManagers) odzyskał sprawność po awarii; nie należy jednak pamiętać o wyniku transakcji i żądania jego stanu.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
