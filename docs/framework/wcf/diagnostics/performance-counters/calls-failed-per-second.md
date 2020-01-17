---
title: Wywołania zakończone niepowodzeniami na sekundę
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 110ee5c264094f80d5c7c6542c3e388e758e1665
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163166"
---
# <a name="calls-failed-per-second"></a>Wywołania zakończone niepowodzeniami na sekundę
Nazwa licznika: wywołania zakończone niepowodzeniem na sekundę  
  
## <a name="description"></a>Opis  
 Liczba wywołań z nieobsługiwanymi wyjątkami w tej operacji w drugim.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Licznik jest zwiększany za każdym razem, gdy w tej operacji występuje nieobsługiwany wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie i obsługa błędów w kontraktach i usługach](../../specifying-and-handling-faults-in-contracts-and-services.md)
