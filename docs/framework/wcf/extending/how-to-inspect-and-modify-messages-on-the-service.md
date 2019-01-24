---
title: 'Instrukcje: Sprawdzanie i modyfikowanie komunikatów w usłudze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 19487d3f401260a7a32e9aab63b8c2a75feccbd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599637"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Instrukcje: Sprawdzanie i modyfikowanie komunikatów w usłudze
Można sprawdzić lub modyfikowanie komunikatów przychodzących lub wychodzących przez klienta usługi Windows Communication Foundation (WCF) przez zaimplementowanie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> oraz wstawieniu ich do środowiska uruchomieniowego usługi. Aby uzyskać więcej informacji, zobacz [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Jest równoważna funkcji w usłudze <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
### <a name="to-inspect-or-modify-messages"></a>Aby inspekcja lub modyfikowanie komunikatów  
  
1.  Implementowanie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interfejsu.  
  
2.  Implementowanie <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, lub <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interfejs, w zależności od zakresu, jaką chcesz łatwo wprowadzić swoje Inspektor wiadomości usługi.  
  
3.  Wstaw swoje zachowanie przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metody <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Przykład  
 Pokaż w poniższych przykładach kodu w kolejności:  
  
-   Implementacja usługi Inspektor interfejsu.  
  
-   Zachowanie usługi, który wstawia Inspektor.  
  
-   Plik konfiguracji, który ładuje i uruchamia działanie w aplikacji usługi.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
