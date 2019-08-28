---
title: Liczniki wydajności operacji
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 7a9b35346333f7b910802ff2a1b1769d177f3952
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040320"
---
# <a name="operation-performance-counters"></a>Liczniki wydajności operacji
Liczniki wydajności operacji są dostępne w `ServiceModelOperation 4.0.0.0` obiekcie wydajności podczas wyświetlania z monitorem wydajności (Perfmon. exe). Każda operacja ma pojedyncze wystąpienie. Oznacza to, że jeśli dany kontrakt zawiera 10 operacji, do tego kontraktu są skojarzone 10 wystąpień liczników operacji. Wystąpienia obiektów są nazwane przy użyciu następującego wzorca:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Ten licznik umożliwia pomiar sposobu użycia wywołania oraz sposobu wykonywania operacji.  
  
> [!CAUTION]
> Istnieje limit długości nazwy wystąpienia licznika wydajności. Jeśli nazwa wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia wartością skrótu.  
  
## <a name="see-also"></a>Zobacz także

- [Liczniki wydajności](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
