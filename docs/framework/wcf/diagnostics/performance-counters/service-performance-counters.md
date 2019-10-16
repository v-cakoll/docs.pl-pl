---
title: Liczniki wydajności usługi
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 929ddcb2f271b7488270ea39e7a3a0037158c855
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320030"
---
# <a name="service-performance-counters"></a>Liczniki wydajności usługi
Liczniki wydajności usługi mierzą zachowanie usługi jako całość i mogą służyć do diagnozowania wydajności całej usługi. Można je znaleźć w obiekcie wydajności `ServiceModelService 4.0.0.0` podczas wyświetlania z monitorem wydajności (Perfmon. exe). Wystąpienia są nazwane przy użyciu następującego wzorca:  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> Istnieje limit długości nazwy wystąpienia licznika wydajności. Jeśli nazwa wystąpienia licznika Windows Communication Foundation (WCF) przekracza maksymalną długość, WCF zastępuje część nazwy wystąpienia wartością skrótu.  
  
## <a name="see-also"></a>Zobacz także

- [Liczniki wydajności](index.md)
