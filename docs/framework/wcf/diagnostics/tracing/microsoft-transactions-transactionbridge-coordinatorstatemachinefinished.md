---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 8cc32e7b38bfd1bdafd2377ad759f98b248d722e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710459"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a>Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
Automatu stanów dla rejestracji koordynatora została wprowadzona w stan zakończenia.  
  
## <a name="description"></a>Opis  
 Śledzone, gdy lokalny Menedżer transakcji uważa, że rejestracja przełożonego koordynatora zakończeniu przetwarzania 2pc. Wynik dla rejestracji może być przydzielony, Aborted lub zapomnianych. Również śledzona jest, gdy lokalny Menedżer transakcji głosów tylko do odczytu podczas przygotowywania.  
  
## <a name="see-also"></a>Zobacz także
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
