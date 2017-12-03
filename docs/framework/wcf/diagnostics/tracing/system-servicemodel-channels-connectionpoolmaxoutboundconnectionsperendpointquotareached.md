---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f90ba7a245b36b24c190304f34a4481d1abda121
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a>Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
Usługa protokołu WS-AT nie można zarejestrować transakcji za pomocą dostępnego kontekstu koordynacji.  
  
## <a name="description"></a>Opis  
 Śledzone po nie można zarejestrować transakcji dla protokołu podanego 2pc usługi MSDTC.  Może to nastąpić, ponieważ transakcja nie istnieje, rejestrowanie nie jest dozwolony lub są już zbyt wiele rejestracji.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Sprawdź, czy ciąg stanu w komunikat śledzenia do ustalenia, czy istnieje dowolny element przydatnych wyników.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
