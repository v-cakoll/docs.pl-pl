---
title: 'Usługa: Wywołania zwracające błędy na sekundę'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: c9af93c7cc0f07ced4435c98fd307e7a7976687f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580086"
---
# <a name="service-calls-faulted-per-second"></a>Usługa: Wywołania zwracające błędy na sekundę
Nazwa komputera: Wywołania zwracające błędy na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań, które zwróciły błędy do tej usługi na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują się przy użyciu protokołu SOAP wiadomości błędu informacje o błędzie przetwarzania. Błędy protokołu SOAP są typy komunikatów, które są zawarte w metadanych dla operacji usługowej i z tego względu utworzyć kontrakt błędu, w której klienci mogą używać się ich wykonanie, bardziej niezawodne lub interaktywne. Ponieważ błędach SOAP są wyrażone klientom w postaci XML, są one bardzo międzyoperacyjnych.  
  
## <a name="see-also"></a>Zobacz także
- [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
