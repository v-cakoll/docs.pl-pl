---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: f41fd08138591a90b6173b5e4806e5ac73ff07da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662767"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a>System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
Określony transakcja została przerwana, ponieważ był niezakończonych modyfikacji, gdy sesja została zamknięta, a gdy TransactionAutoCompleteOnSessionClose została ustawiona na wartość false.  
  
## <a name="description"></a>Opis  
 Śledzone bieżącej aktywnej sesji zostało zamknięte, transakcja nie została ukończona i jest równa TransactionAutoCompleteOnSessionClose `false`.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Ślad wskazuje potencjalny błąd aplikacji, które należy zbadać.  
  
## <a name="see-also"></a>Zobacz także
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
