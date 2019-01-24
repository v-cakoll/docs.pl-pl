---
title: Liczniki wydajności usługi
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: bf0b12e6d4954c0a1392554d7269a7d539a77dc1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545598"
---
# <a name="service-performance-counters"></a>Liczniki wydajności usługi
Liczniki wydajności usługi zmierzyć zachowanie usługi jako całość i może służyć do diagnozowania wydajności całą usługę. Można go znaleźć w `ServiceModelService 4.0.0.0` obiekt wydajności podczas wyświetlania przy użyciu Monitora wydajności (Perfmon.exe). Wystąpienia są nazywane przy użyciu następującego wzorca:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  Obowiązuje limit długości nazwy wystąpienia licznika wydajności. Gdy nazwę wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia z wartością skrótu.  
  
## <a name="see-also"></a>Zobacz także
- [Liczniki wydajności](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
