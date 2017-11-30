---
title: "Liczniki wydajności operacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83460e1c4db17938466051269dbeba3f19e0b40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operation-performance-counters"></a>Liczniki wydajności operacji
Liczniki wydajności operacji znajdują się w obszarze `ServiceModelOperation 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności (Perfmon.exe). Każda operacja wymaga poszczególnych wystąpień. Oznacza to jeśli dany kontrakt operacji 10, 10 wystąpień licznika operacji są skojarzone z tej Umowy. Wystąpienia obiektu są nazywane przy użyciu następującego wzorca:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Ten licznik umożliwia pomiarów sposobu używania połączenia i jak wykonywanie operacji.  
  
> [!CAUTION]
>  Istnieje limit na długość nazwy wystąpienia licznika wydajności. Gdy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nazwę wystąpienia licznika przekracza maksymalną długość [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Zamienia część nazwy wystąpienia wartość skrótu.  
  
## <a name="see-also"></a>Zobacz też  
 [Liczniki wydajności](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
