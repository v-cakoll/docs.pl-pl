---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7b1f6a2f4a344b566c76d0095942b84a8a4e76f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991630"
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
