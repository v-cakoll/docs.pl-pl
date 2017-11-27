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
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="05d54-102">Instrukcje: Inspekcja lub modyfikowanie parametrów</span><span class="sxs-lookup"><span data-stu-id="05d54-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="05d54-103">Można inspekcja lub modyfikowanie komunikatów przychodzących lub wychodzących dla jednej operacji na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obiektu klienta lub [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi zaimplementowanie <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interfejs oraz wstawieniu ich do środowiska uruchomieniowego klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="05d54-103">You can inspect or modify the incoming or outgoing messages for a single operation on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client object or a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="05d54-104">Zwykle to zachowanie działania jest używana do dodawania inspektorzy parametr dla jednej operacji. innych zachowań może służyć do zapewnienia łatwego dostępu do środowiska wykonawczego w zakresie większa.</span><span class="sxs-lookup"><span data-stu-id="05d54-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="05d54-105">Aby uzyskać więcej informacji, zobacz [rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md) i [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="05d54-105">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md) and [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="05d54-106">Sprawdzanie lub modyfikowanie parametrów</span><span class="sxs-lookup"><span data-stu-id="05d54-106">Inspecting or Modifying Parameters</span></span>  
  
1.  <span data-ttu-id="05d54-107">Implementowanie <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="05d54-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="05d54-108">Implementowanie <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (w zależności od zakresu wymagane) można dodać Inspektor sieci parametru jednej <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="05d54-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3.  <span data-ttu-id="05d54-109">Wstaw Twoje zachowanie przed wywołaniem <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metoda <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05d54-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="05d54-110">Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="05d54-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05d54-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="05d54-111">Example</span></span>  
 <span data-ttu-id="05d54-112">W poniższych przykładach kodu pokazano, w kolejności:</span><span class="sxs-lookup"><span data-stu-id="05d54-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="05d54-113">Implementacja inspektora parametru.</span><span class="sxs-lookup"><span data-stu-id="05d54-113">A parameter inspector implementation.</span></span>  
  
-   <span data-ttu-id="05d54-114">Implementacja zachowanie wstawia inspektora parametru za pomocą <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>i <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05d54-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="05d54-115">Plik konfiguracji, który ładuje i uruchamia zachowania punktu końcowego w aplikacji klienta, aby wstawić inspektora parametru na kliencie.</span><span class="sxs-lookup"><span data-stu-id="05d54-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="05d54-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05d54-116">See Also</span></span>  
 [<span data-ttu-id="05d54-117">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="05d54-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
