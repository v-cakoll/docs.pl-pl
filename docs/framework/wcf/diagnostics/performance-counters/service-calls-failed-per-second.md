---
title: "Usługa: Wywołania zakończone niepowodzeniami na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2072a686d5d424f90ac2f32cf5fc11564b07542c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-failed-per-second"></a>Usługa: Wywołania zakończone niepowodzeniami na sekundę
Nazwa licznika: Wywołania zakończone niepowodzeniami na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań ma nieobsługiwane wyjątki, które są odbierane przez tę usługę na sekundę.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)  
  
 W kodzie zarządzanym wyjątki są zgłaszane w przypadku wystąpienia błędów.  
  
 W kodzie zarządzanym wyjątki są zgłaszane w przypadku wystąpienia błędów.  
  
 Ten licznik jest zwiększany za każdym razem, gdy jest nieobsługiwany w tej usłudze.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
