---
title: Liczniki wydajności usługi
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 18a9e6336b70341f5da9c7b73cbd3f9bd3f958c7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044274"
---
# <a name="service-performance-counters"></a>Liczniki wydajności usługi
Liczniki wydajności usługi mierzą zachowanie usługi jako całość i mogą służyć do diagnozowania wydajności całej usługi. Można je znaleźć w `ServiceModelService 4.0.0.0` obiekcie wydajności podczas wyświetlania z monitorem wydajności (Perfmon. exe). Wystąpienia są nazwane przy użyciu następującego wzorca:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
> Istnieje limit długości nazwy wystąpienia licznika wydajności. Jeśli nazwa wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia wartością skrótu.  
  
## <a name="see-also"></a>Zobacz także

- [Liczniki wydajności](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
