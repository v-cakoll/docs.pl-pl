---
title: "Instrukcje: Inspekcja lub modyfikowanie parametrów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 71e96dc3cf448b2e67b8a039f28a12df8360c76a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inspect-or-modify-parameters"></a>Instrukcje: Inspekcja lub modyfikowanie parametrów
Można inspekcja lub modyfikowanie komunikatów przychodzących lub wychodzących dla jednej operacji na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obiektu klienta lub [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi zaimplementowanie <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interfejs oraz wstawieniu ich do środowiska uruchomieniowego klienta lub usługi. Zwykle to zachowanie działania jest używana do dodawania inspektorzy parametr dla jednej operacji. innych zachowań może służyć do zapewnienia łatwego dostępu do środowiska wykonawczego w zakresie większa. Aby uzyskać więcej informacji, zobacz [rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md) i [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>Sprawdzanie lub modyfikowanie parametrów  
  
1.  Implementowanie <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interfejsu.  
  
2.  Implementowanie <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (w zależności od zakresu wymagane) można dodać Inspektor sieci parametru jednej <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> właściwości.  
  
3.  Wstaw Twoje zachowanie przed wywołaniem <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metoda <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach kodu pokazano, w kolejności:  
  
-   Implementacja inspektora parametru.  
  
-   Implementacja zachowanie wstawia inspektora parametru za pomocą <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>i <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.  
  
-   Plik konfiguracji, który ładuje i uruchamia zachowania punktu końcowego w aplikacji klienta, aby wstawić inspektora parametru na kliencie.  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
