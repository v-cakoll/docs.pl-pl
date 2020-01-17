---
title: 'Punkt końcowy: wywołania zakończone niepowodzeniem na sekundę'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 25e504221097505e622a3ba60f0c7e85ec455f36
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163621"
---
# <a name="endpoint-calls-failed-per-second"></a>Punkt końcowy: wywołania zakończone niepowodzeniem na sekundę
Nazwa licznika: wywołania zakończone niepowodzeniem na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań, które mają Nieobsłużone wyjątki i są odbierane przez ten punkt końcowy w drugim.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Licznik jest zwiększany za każdym razem, gdy w tym punkcie końcowym występuje nieobsługiwany wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie i obsługa błędów w kontraktach i usługach](../../specifying-and-handling-faults-in-contracts-and-services.md)
