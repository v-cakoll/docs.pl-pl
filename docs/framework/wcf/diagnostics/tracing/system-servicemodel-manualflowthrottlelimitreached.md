---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 86d47ab0a83ff3e4a68bfa8ccf1349cf2b345b23
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597739"
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
