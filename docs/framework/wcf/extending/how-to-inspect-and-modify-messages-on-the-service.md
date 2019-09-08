---
title: 'Instrukcje: sprawdzanie i modyfikowanie komunikatów w usłudze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 1356983361c483170d9d7365932b788f2421bf09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795601"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Instrukcje: sprawdzanie i modyfikowanie komunikatów w usłudze
Możesz sprawdzić lub zmodyfikować komunikaty przychodzące lub wychodzące dla klienta Windows Communication Foundation (WCF), implementując <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> i wstawiając go do środowiska uruchomieniowego usługi. Aby uzyskać więcej informacji, zobacz [rozszerzanie dyspozytorów](extending-dispatchers.md). Równoważna funkcja w usłudze to <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
### <a name="to-inspect-or-modify-messages"></a>Aby sprawdzić lub zmodyfikować komunikaty  
  
1. Implementowanie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interfejsu.  
  
2. Zaimplementuj Interfejs <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> , lub, w zależności od zakresu, w którym chcesz łatwo wstawić inspektora komunikatów usługi. <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>  
  
3. Wstaw zachowanie przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metody <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>na. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, w kolejności:  
  
- Implementacja inspektora usługi.  
  
- Zachowanie usługi, które wstawia inspektora.  
  
- Plik konfiguracji, który ładuje i uruchamia zachowanie w aplikacji usługi.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md)
