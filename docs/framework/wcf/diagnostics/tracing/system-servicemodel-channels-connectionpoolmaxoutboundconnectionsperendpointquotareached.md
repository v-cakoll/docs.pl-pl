---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 4f51777ae690178b83d353f72e63a6f2958b1592
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674586"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a>Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
Usługa protokołu WS-AT nie można zarejestrować transakcji za pomocą dostępnego kontekstu koordynacji.  
  
## <a name="description"></a>Opis  
 Śledzone po nie można zarejestrować transakcji protokołu 2pc danej usługi MSDTC.  Można to zrobić, ponieważ transakcja nie istnieje, rejestrowanie nie jest już dozwolona lub zbyt wiele rejestracji znajdują się już.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Sprawdź, czy ciąg stanu w ramach komunikat śledzenia do ustalenia, czy istnieje dowolny element informacje z możliwością działania.  
  
## <a name="see-also"></a>Zobacz także
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
