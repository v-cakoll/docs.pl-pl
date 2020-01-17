---
title: 'Punkt końcowy: Wywołania zwracające błędy na sekundę'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: ead4b074748307f30d16557c3359f730880595da
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163543"
---
# <a name="endpoint-calls-faulted-per-second"></a>Punkt końcowy: Wywołania zwracające błędy na sekundę
Nazwa licznika: wywołania z błędami na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań, które zwróciły błędy do tego punktu końcowego w drugim.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 W aplikacjach Windows Communication Foundation (WCF) metody usługi komunikują przetwarzanie informacji o błędach przy użyciu komunikatów błędów protokołu SOAP. Błędy protokołu SOAP to typy komunikatów, które są zawarte w metadanych dla operacji usługi, dlatego należy utworzyć kontrakt błędów, którego klienci mogą używać do bardziej niezawodnego lub interaktywnego wykonania. Ponieważ błędy protokołu SOAP są wyrażane dla klientów w formularzu XML, są one wysoce interoperacyjne.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie i obsługa błędów w kontraktach i usługach](../../specifying-and-handling-faults-in-contracts-and-services.md)
