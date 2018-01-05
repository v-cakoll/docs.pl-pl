---
title: "Liczniki wydajności usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8145ff12f5a9befdef3cbf5edf69e5162c4d7014
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service-performance-counters"></a>Liczniki wydajności usługi
Liczniki wydajności usługi zmierzyć zachowanie usługi jako całość i może służyć do diagnozowania wydajność całej usługi. Można go znaleźć w `ServiceModelService 4.0.0.0` obiekt wydajności w przypadku wyświetlania z Monitora wydajności (Perfmon.exe). Wystąpienia są nazywane przy użyciu następującego wzorca:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  Istnieje limit na długość nazwy wystąpienia licznika wydajności. Gdy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nazwę wystąpienia licznika przekracza maksymalną długość [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Zamienia część nazwy wystąpienia wartość skrótu.  
  
## <a name="see-also"></a>Zobacz też  
 [Liczniki wydajności](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
