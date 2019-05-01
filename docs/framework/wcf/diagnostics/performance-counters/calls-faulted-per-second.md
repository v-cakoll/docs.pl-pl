---
title: Wywołania zwracające błędy na sekundę
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: 5b7569b6a00757fbb863b90b25b44815a349ab07
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797400"
---
# <a name="calls-faulted-per-second"></a>Wywołania zwracające błędy na sekundę
Nazwa komputera: Wywołania zwracające błędy na sekundę  
  
## <a name="description"></a>Opis  
 Liczba wywołań, które zwróciły błędy na tę operację za chwilę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują się przy użyciu protokołu SOAP wiadomości błędu informacje o błędzie przetwarzania. Błędy protokołu SOAP są typy komunikatów, które są zawarte w metadanych dla operacji usługowej i z tego względu utworzyć kontrakt błędu, w której klienci mogą używać się ich wykonanie, bardziej niezawodne lub interaktywne. Ponieważ błędach SOAP są wyrażone klientom w postaci XML, są one bardzo międzyoperacyjnych.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
