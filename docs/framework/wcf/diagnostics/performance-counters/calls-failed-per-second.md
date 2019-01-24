---
title: Wywołania zakończone niepowodzeniami na sekundę
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: bad37e0124698209955603c1b7d8a1aec4b87418
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521052"
---
# <a name="calls-failed-per-second"></a>Wywołania zakończone niepowodzeniami na sekundę
Nazwa komputera: Wywołania zakończone niepowodzeniami na sekundę  
  
## <a name="description"></a>Opis  
 Liczba wywołań z nieobsługiwanych wyjątków w tę operację za chwilę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 Ten licznik jest zwiększona za każdym, gdy jest nieobsługiwany w tej operacji.  
  
## <a name="see-also"></a>Zobacz także
- [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
