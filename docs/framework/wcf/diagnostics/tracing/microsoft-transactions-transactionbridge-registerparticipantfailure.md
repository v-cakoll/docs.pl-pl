---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 16b0261a53df29b1fc2049c25375c651735a524c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
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
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
