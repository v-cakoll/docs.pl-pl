---
title: 'Usługa: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: e165348a71101b21fa66bd4907c43335b1e476e4
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163985"
---
# <a name="service-calls-failed-per-second"></a>Usługa: Wywołania zakończone niepowodzeniami na sekundę
Nazwa licznika: wywołania zakończone niepowodzeniem na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań, które mają Nieobsłużone wyjątki i są odbierane przez tę usługę w drugim.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 W kodzie zarządzanym wyjątki są generowane, gdy wystąpią błędy.  
  
 W kodzie zarządzanym wyjątki są generowane, gdy wystąpią błędy.  
  
 Licznik jest zwiększany za każdym razem, gdy w tej usłudze występuje nieobsługiwany wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie i obsługa błędów w kontraktach i usługach](../../specifying-and-handling-faults-in-contracts-and-services.md)
