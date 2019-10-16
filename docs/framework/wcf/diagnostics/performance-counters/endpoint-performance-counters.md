---
title: Liczniki wydajności w punkcie końcowym
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 1b0f7462fea8843bcb0a0938a8034f405f30a6fb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320515"
---
# <a name="endpoint-performance-counters"></a>Liczniki wydajności w punkcie końcowym
Liczniki wydajności punktów końcowych przechwytują dane, które ujawniają, w jaki sposób punkt końcowy akceptuje komunikaty. Można je znaleźć w obiekcie wydajności `ServiceModelEndpoint 4.0.0.0` podczas wyświetlania z monitorem wydajności. Wystąpienia są nazwane przy użyciu tego wzorca:  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 Dane są podobne do tych zebranych dla poszczególnych operacji, ale są agregowane w całym punkcie końcowym.  
  
> [!CAUTION]
> Istnieje limit długości nazwy wystąpienia licznika wydajności. Jeśli nazwa wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia wartością skrótu.  
  
## <a name="see-also"></a>Zobacz także

- [Liczniki wydajności](index.md)
