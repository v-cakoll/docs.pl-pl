---
title: 'Usługa: Wywołania zakończone niepowodzeniami na sekundę'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: a043cf30fa67707aca3edf50cf23372ade5e5a42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559895"
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
