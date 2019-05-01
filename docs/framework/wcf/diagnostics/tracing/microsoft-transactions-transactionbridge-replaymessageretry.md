---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 0c9e79709f5929e1fa123a8d1695ca720046e9e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997526"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a>Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
Ponowna próba komunikat powtarzania została wysłana do koordynator nie odpowiada.  
  
## <a name="description"></a>Opis  
 Śledzone w razie potrzeby lokalny Menedżer transakcji do wysłania wiadomości powtarzania koordynatorem wyższego poziomu, ponieważ nie otrzymała odpowiedzi w określonym czasie.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Badania potencjalnych sieci lub problemy z produktu, które uniemożliwiają są dostarczane na czas odpowiedzi.  Jeśli wiele z tych komunikatów są widoczne, może to wskazywać problemy z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi. Zarówno w przypadku problemów znacznie skróci przepływność transakcji w ramach systemu.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
