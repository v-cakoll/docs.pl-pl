---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: fb69c3c737a0e77b05e08ab8d8282069feb069bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095688"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a>System.ServiceModel.ManualFlowThrottleLimitReached
System.ServiceModel.ManualFlowThrottleLimitReached  
  
## <a name="description"></a>Opis  
 System osiągnął limit ustawiony dla ograniczania ManualFlowControlLimit. Wartość ograniczenia przepustowości można zmienić, modyfikując właściwość ManualFlowControlLimit ServiceHost lub obiekt InstanceContext, jeśli ma to zastosowanie.  
  
 Ślad jest emitowane, gdy limit kontroli przepływu ręczne początkowo jest ograniczona do 0. Kolejne zmiany na wartość 0 nie są śledzone. Przepływ sterowania limit w kontekście wystąpienia śledzona jest jeden raz dla każdego kontekstu.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
