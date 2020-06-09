---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: f37bc252e12aef94d77c0745d36b5c8232a169eb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599740"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a>Microsoft.Transactions.TransactionBridge.CommitMessageRetry
Do uczestnika, który nie odpowiada, wysłano ponowną próbę komunikatu zatwierdzenia.  
  
## <a name="description"></a>Opis  
 Śledzony, jeśli lokalny Menedżer transakcji jest wymagany do ponownego wysłania komunikatu zatwierdzenia do uczestnika podrzędnego, ponieważ nie otrzymał odpowiedzi w danym czasie.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Zbadaj potencjalne problemy z siecią lub produktem, które uniemożliwiają dostarczenie odpowiedzi na czas.  Jeśli jest widocznych wiele z tych komunikatów, może to oznaczać problemy z infrastrukturą lub czasy nietypowej odpowiedzi. Oba problemy znacząco zmniejszają przepływność transakcji w ramach systemu.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
