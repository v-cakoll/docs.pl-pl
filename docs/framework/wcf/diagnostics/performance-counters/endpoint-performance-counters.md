---
title: Liczniki wydajności w punkcie końcowym
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 8354cff600f8c16a5ab9b4f6efd3c0b93a46276c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="endpoint-performance-counters"></a>Liczniki wydajności w punkcie końcowym
Liczniki wydajności punktu końcowego przechwytywania danych, który pokazuje, jak punkt końcowy jest akceptowanie komunikatów. Można go znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności. Wystąpienia są nazywane użycia tego wzorca:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Dane przypomina gromadzone dla poszczególnych działań, ale tylko jest agregowana przez punkt końcowy.  
  
> [!CAUTION]
>  Istnieje limit na długość nazwy wystąpienia licznika wydajności. Gdy nazwę wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF Zamienia część nazwy wystąpienia wartość skrótu.  
  
## <a name="see-also"></a>Zobacz też  
 [Liczniki wydajności](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
