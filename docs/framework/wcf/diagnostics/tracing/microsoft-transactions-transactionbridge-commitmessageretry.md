---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: f1092dd335be793fb3d2212b7b9398cc69d2f79f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474288"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a>Microsoft.Transactions.TransactionBridge.CommitMessageRetry
Ponowna próba przekazania wiadomości została wysłana do uczestnika, który nie odpowiada.  
  
## <a name="description"></a>Opis  
 Śledzone w razie potrzeby lokalnego Menedżera transakcji do wysłania wiadomości zatwierdzania do uczestnika podrzędnych, ponieważ nie otrzymano odpowiedzi w określonym czasie.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Badania potencjalnych sieci lub produktu problemy, które uniemożliwiają dostarczanie na czas odpowiedzi.  Jeśli wiele z tych wiadomości są widoczne, może to oznaczać problemy związane z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi. Problemy z obu znacząco zmniejsza przepływność transakcji w systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
