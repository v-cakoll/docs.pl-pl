---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 02e275fa212128c65beda4bc3703949e75ea5092
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220893"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a>Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
Ponowna próba przygotowania wiadomość została wysłana do uczestnika, który nie odpowiada.  
  
## <a name="description"></a>Opis  
 Śledzone w razie potrzeby lokalny Menedżer transakcji próba wysłania wiadomości przygotowania do podrzędnego uczestnika, ponieważ nie otrzymała odpowiedzi w określonym czasie.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Badania potencjalnych sieci lub problemy z produktu, które uniemożliwiają są dostarczane na czas odpowiedzi.  Jeśli wiele z tych komunikatów są widoczne, może to wskazywać problemy z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi. Zarówno w przypadku problemów może znacząco zmniejszyć przepływność transakcji w ramach systemu.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
