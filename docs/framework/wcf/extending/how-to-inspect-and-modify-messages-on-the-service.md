---
title: 'Instrukcje: Sprawdzanie i modyfikowanie komunikatów w usłudze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: ec1c60bc2b3e966c576de260dfe3b06a05ab84c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488078"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Instrukcje: Sprawdzanie i modyfikowanie komunikatów w usłudze
Można inspekcja lub modyfikowanie komunikatów przychodzących lub wychodzących przez klienta usługi Windows Communication Foundation (WCF) przez zaimplementowanie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> oraz wstawieniu ich do środowiska uruchomieniowego usługi. Aby uzyskać więcej informacji, zobacz [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Jest równoważna funkcji w usłudze <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
### <a name="to-inspect-or-modify-messages"></a>Aby inspekcja lub modyfikowanie komunikatów  
  
1.  Implementowanie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interfejsu.  
  
2.  Implementowanie <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, lub <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interfejsu w zależności od zakresu, w którym chcesz wstawić łatwo inspektora komunikatów z usługi.  
  
3.  Wstaw Twoje zachowanie przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metoda <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach kodu pokazano, w kolejności:  
  
-   Implementacja inspektora usługi.  
  
-   Zachowanie usługi, która wstawia Inspektor.  
  
-   Plik konfiguracji, który ładuje i uruchamia zachowania w aplikacji usługi.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
