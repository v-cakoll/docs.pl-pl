---
title: Liczniki wydajności operacji
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 16608132c6557f8612d42402a2cb2c49fcc29637
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566095"
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
