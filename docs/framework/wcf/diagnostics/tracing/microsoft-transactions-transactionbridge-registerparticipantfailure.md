---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: 1819a269a6775c8541f38f4aa5d733002e3c1e9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599685"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
Usługa protokołu WS-AT nie może zarejestrować uczestnika dla protokołu kontroli.  
  
## <a name="description"></a>Opis  
 Śledzone, jeśli usługa MSDTC wykryje Nieprawidłowe żądanie rejestracji. Przyczyną może być wiele żądań rejestracji ukończenia i błędy wewnętrzne.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Nie próbuj rejestrować się w celu ukończenia więcej niż raz.  Sprawdź również ciąg stanu w komunikacie śledzenia, aby określić, czy istnieje jakikolwiek element możliwy do wykonania.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
