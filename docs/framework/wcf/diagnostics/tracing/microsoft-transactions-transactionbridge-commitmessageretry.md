---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: d939d525fd1c7e8f41cccbc3ca7af9726f22bdfc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571434"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a>Microsoft.Transactions.TransactionBridge.CommitMessageRetry
Ponowna próba komunikat zatwierdzenia została wysłana do uczestnika, który nie odpowiada.  
  
## <a name="description"></a>Opis  
 Śledzone w razie potrzeby lokalny Menedżer transakcji ponownie wysłać wiadomość dotyczącą zatwierdzenia do podrzędnego uczestnika, ponieważ nie otrzymała odpowiedzi w określonym czasie.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Badania potencjalnych sieci lub problemy z produktu, które uniemożliwiają są dostarczane na czas odpowiedzi.  Jeśli wiele z tych komunikatów są widoczne, może to wskazywać problemy z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi. Zarówno w przypadku problemów znacznie skróci przepływność transakcji w ramach systemu.  
  
## <a name="see-also"></a>Zobacz także
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
