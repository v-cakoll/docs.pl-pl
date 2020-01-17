---
title: Wywołania zwracające błędy na sekundę
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: 37fd47a3e4ca474338a4a6ae1117c2626acb546f
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163153"
---
# <a name="calls-faulted-per-second"></a>Wywołania zwracające błędy na sekundę
Nazwa licznika: Błędne wywołania na sekundę  
  
## <a name="description"></a>Opis  
 Liczba wywołań, które zwróciły błędy do tej operacji w drugim.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują przetwarzanie informacji o błędach przy użyciu komunikatów błędów protokołu SOAP. Błędy protokołu SOAP to typy komunikatów, które są zawarte w metadanych dla operacji usługi, dlatego należy utworzyć kontrakt błędów, którego klienci mogą używać do bardziej niezawodnego lub interaktywnego wykonania. Ponieważ błędy protokołu SOAP są wyrażane dla klientów w formularzu XML, są one wysoce interoperacyjne.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie i obsługa błędów w kontraktach i usługach](../../specifying-and-handling-faults-in-contracts-and-services.md)
