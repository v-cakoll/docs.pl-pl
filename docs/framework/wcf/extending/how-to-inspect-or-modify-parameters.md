---
title: 'Instrukcje: sprawdzanie lub modyfikowanie parametrów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 2e294b7970a58fad9385802470a514e5a9240495
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766867"
---
# <a name="how-to-inspect-or-modify-parameters"></a>Instrukcje: sprawdzanie lub modyfikowanie parametrów
Można sprawdzić i modyfikować wiadomości przychodzących lub wychodzących dla jednej operacji na obiekt klienta usługi Windows Communication Foundation (WCF) lub usługi WCF poprzez implementację <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interfejsu i wstawiania ich do środowiska uruchomieniowego klienta lub usługę. Zwykle to zachowanie operacja służy do dodawania inspektorzy parametr dla jednej operacji. innych zachowań może służyć do zapewnienia łatwy dostęp do środowiska uruchomieniowego w zakresie większa. Aby uzyskać więcej informacji, zobacz [rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md) i [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>Inspekcja lub modyfikowanie parametrów  
  
1. Implementowanie <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interfejsu.  
  
2. Implementowanie <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (w zależności od wymagany zakres) do dodania usługi Inspektor parametru do listy <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> właściwości.  
  
3. Wstaw swoje zachowanie przed wywołaniem <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metody <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Przykład  
 Pokaż w poniższych przykładach kodu w kolejności:  
  
- Implementacja Inspektor parametru.  
  
- Implementacja zachowanie, który wstawia Inspektor parametru za pomocą <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>i <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.  
  
- Plik konfiguracji, który ładuje i uruchamia zachowanie punktu końcowego w aplikacji klienckiej, aby wstawić Inspektor parametru na komputerze klienckim.  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
