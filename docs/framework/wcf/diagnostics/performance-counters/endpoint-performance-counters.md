---
title: Liczniki wydajności w punkcie końcowym
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 2352bc82998c8e87e72f331104446bac4fcb9fda
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040585"
---
# <a name="endpoint-performance-counters"></a>Liczniki wydajności w punkcie końcowym
Liczniki wydajności punktów końcowych przechwytują dane, które ujawniają, w jaki sposób punkt końcowy akceptuje komunikaty. Można je znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekcie wydajności podczas wyświetlania z monitorem wydajności. Wystąpienia są nazwane przy użyciu tego wzorca:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Dane są podobne do tych zebranych dla poszczególnych operacji, ale są agregowane w całym punkcie końcowym.  
  
> [!CAUTION]
> Istnieje limit długości nazwy wystąpienia licznika wydajności. Jeśli nazwa wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia wartością skrótu.  
  
## <a name="see-also"></a>Zobacz także

- [Liczniki wydajności](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
