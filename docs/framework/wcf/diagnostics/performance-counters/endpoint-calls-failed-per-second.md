---
title: 'Punkt końcowy: wywołania zakończone niepowodzeniem na sekundę'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 9634f8a170bb2fae2f15c3f00dcabb95d512c74e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321458"
---
# <a name="endpoint-calls-failed-per-second"></a>Punkt końcowy: wywołania zakończone niepowodzeniem na sekundę
Nazwa licznika: wywołania zakończone niepowodzeniem na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań, które mają Nieobsłużone wyjątki i są odbierane przez ten punkt końcowy w drugim.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Licznik jest zwiększany za każdym razem, gdy w tym punkcie końcowym występuje nieobsługiwany wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie i obsługa błędów w kontraktach i usługach](../../specifying-and-handling-faults-in-contracts-and-services.md)
