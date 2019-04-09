---
title: 'Usługa: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: d87d5f06d0c9a3849ec80a3d1c7badefde7cf372
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167495"
---
# <a name="service-calls-failed-per-second"></a>Usługa: Wywołania zakończone niepowodzeniami na sekundę
Nazwa komputera: Wywołania zakończone niepowodzeniami na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań, ma nieobsługiwane wyjątki, które są odbierane przez tę usługę na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 W zarządzanym kodzie są zgłaszane wyjątki, gdy wystąpią błędy.  
  
 W zarządzanym kodzie są zgłaszane wyjątki, gdy wystąpią błędy.  
  
 Ten licznik jest zwiększany za każdym razem, gdy zostanie nieobsługiwany wyjątek w tej usłudze.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
