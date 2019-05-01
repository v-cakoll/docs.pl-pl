---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e56a9ed1d837af27d481282e0e106d537ec41ee3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997753"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
Nie można zarejestrować uczestnika dla protokołu kontroli usługi protokołu WS-AT.  
  
## <a name="description"></a>Opis  
 Śledzone, jeśli usługa MSDTC wykrywa nieprawidłowe żądanie rejestracji. Może to być spowodowane przez wiele żądań rejestracji uzupełniania i wewnętrzne błędy.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Nie należy próbować Zarejestruj się w celu ukończenia więcej niż jeden raz.  Ponadto sprawdź, czy ciąg stanu w ramach komunikat śledzenia do ustalenia, czy istnieje dowolny element informacje z możliwością działania.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
