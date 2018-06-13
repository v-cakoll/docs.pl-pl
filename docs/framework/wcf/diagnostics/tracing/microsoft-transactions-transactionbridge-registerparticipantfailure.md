---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: fb5e50e7332269690a200334ef936dd0d5525e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475117"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
Usługa protokołu WS-AT nie może zarejestrować uczestnika dla protokołu sterowania.  
  
## <a name="description"></a>Opis  
 Śledzone, jeśli usługi MSDTC wykryje nieprawidłowe żądanie rejestracji. Może to być spowodowane przez wiele żądań rejestracji uzupełniania i błędy wewnętrzne.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Nie należy próbować rejestrowanie się w celu ukończenia więcej niż raz.  Ponadto sprawdź, czy ciągu stanu w komunikat śledzenia do ustalenia, czy istnieje dowolny element przydatnych wyników.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
