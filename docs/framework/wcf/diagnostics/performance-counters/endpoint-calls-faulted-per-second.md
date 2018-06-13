---
title: 'Punkt końcowy: Wywołania zwracające błędy na sekundę'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 927f5370237b2502899d61f0b8d4bd79c8e00ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472547"
---
# <a name="endpoint-calls-faulted-per-second"></a>Punkt końcowy: Wywołania zwracające błędy na sekundę
Nazwa licznika: Wywołania zwracające błędy na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań, które zwrócone błędy na ten punkt końcowy na sekundę.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)  
  
 W aplikacji Windows Communication Foundation (WCF) metody usługi komunikują się za pomocą protokołu SOAP komunikatów "fault" informacje o błędzie przetwarzania. Błędach SOAP są typów komunikatów, które są zawarte w metadanych dla operacji usługi i dlatego należy utworzyć kontrakt błędu, w której klienci mogą używać, aby ich wykonanie bardziej niezawodne lub interakcyjne. Ponieważ błędach SOAP są wyrażane klientom w postaci XML, są one bardzo interoperacyjne.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
