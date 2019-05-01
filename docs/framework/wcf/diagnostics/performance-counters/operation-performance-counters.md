---
title: Liczniki wydajności operacji
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: d4f5755129fecb62e6a4da98a2bf642c5e20f9c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916204"
---
# <a name="operation-performance-counters"></a>Liczniki wydajności operacji
Liczniki wydajności operacji znajdują się w obszarze `ServiceModelOperation 4.0.0.0` obiekt wydajności podczas wyświetlania przy użyciu Monitora wydajności (Perfmon.exe). Każda operacja ma poszczególnych wystąpień. Oznacza to jeśli danego kontraktu operacje 10, 10 wystąpień licznika operacji skojarzonych z tej Umowy. Wystąpienia obiektu są nazywane przy użyciu następującego wzorca:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Ten licznik umożliwia pomiar sposobu używania wywołania i jak dobrze działa operacja.  
  
> [!CAUTION]
>  Obowiązuje limit długości nazwy wystąpienia licznika wydajności. Gdy nazwę wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia z wartością skrótu.  
  
## <a name="see-also"></a>Zobacz także

- [Liczniki wydajności](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
