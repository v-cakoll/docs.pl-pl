---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 162452d5d12859571d78ef19cf1d838953ee7acd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596210"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a>Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
Do koordynatora, który nie odpowiada, wysłano ponowną próbę komunikatu powtórzenia.  
  
## <a name="description"></a>Opis  
 Śledzony, jeśli lokalny Menedżer transakcji jest wymagany do ponownego wysłania komunikatu powtarzania do koordynatora wyższego, ponieważ nie otrzymał odpowiedzi w danym czasie.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Zbadaj potencjalne problemy z siecią lub produktem, które uniemożliwiają dostarczenie odpowiedzi na czas.  Jeśli jest widocznych wiele z tych komunikatów, może to oznaczać problemy z infrastrukturą lub czasy nietypowej odpowiedzi. Oba problemy znacząco zmniejszają przepływność transakcji w ramach systemu.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
