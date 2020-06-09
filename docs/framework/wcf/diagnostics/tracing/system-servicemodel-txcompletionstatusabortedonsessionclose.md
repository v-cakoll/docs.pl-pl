---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: c398fc52d5924c033500b95924f9287b43cc9e9d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576606"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a>System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
Określona transakcja została przerwana, ponieważ została zakończona, gdy sesja została zamknięta i TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute będący została ustawiona na wartość false.  
  
## <a name="description"></a>Opis  
 Śledzone, jeśli bieżąca aktywna sesja została zamknięta i transakcja nie została ukończona, a TransactionAutoCompleteOnSessionClose jest ustawiona na `false` .  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Ten ślad wskazuje potencjalną usterkę aplikacji, która powinna zostać zbadana.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
