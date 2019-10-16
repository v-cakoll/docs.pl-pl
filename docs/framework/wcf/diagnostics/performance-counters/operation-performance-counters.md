---
title: Liczniki wydajności operacji
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 59c75dacb2a01f1b85d67d5cc1651dbc55b6aa8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320175"
---
# <a name="operation-performance-counters"></a>Liczniki wydajności operacji
Liczniki wydajności operacji są dostępne pod obiektem wydajności `ServiceModelOperation 4.0.0.0` podczas wyświetlania z monitorem wydajności (Perfmon. exe). Każda operacja ma pojedyncze wystąpienie. Oznacza to, że jeśli dany kontrakt zawiera 10 operacji, do tego kontraktu są skojarzone 10 wystąpień liczników operacji. Wystąpienia obiektów są nazwane przy użyciu następującego wzorca:  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 Ten licznik umożliwia pomiar sposobu użycia wywołania oraz sposobu wykonywania operacji.  
  
> [!CAUTION]
> Istnieje limit długości nazwy wystąpienia licznika wydajności. Jeśli nazwa wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia wartością skrótu.  
  
## <a name="see-also"></a>Zobacz także

- [Liczniki wydajności](index.md)
