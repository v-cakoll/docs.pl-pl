---
title: "Instrukcje: Sprawdzanie i modyfikowanie komunikatów w usłudze"
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
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c919083b165233614a01faf3d63dacd6712fbd01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="f0e16-102">Instrukcje: Sprawdzanie i modyfikowanie komunikatów w usłudze</span><span class="sxs-lookup"><span data-stu-id="f0e16-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="f0e16-103">Można inspekcja lub modyfikowanie komunikatów przychodzących lub wychodzących między [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta zaimplementowanie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> oraz wstawieniu ich do środowiska uruchomieniowego usługi.</span><span class="sxs-lookup"><span data-stu-id="f0e16-103">You can inspect or modify the incoming or outgoing messages across a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="f0e16-104">Aby uzyskać więcej informacji, zobacz [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="f0e16-104">For more information, see [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span> <span data-ttu-id="f0e16-105">Jest równoważna funkcji w usłudze <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0e16-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="f0e16-106">Aby inspekcja lub modyfikowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="f0e16-106">To inspect or modify messages</span></span>  
  
1.  <span data-ttu-id="f0e16-107">Implementowanie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f0e16-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="f0e16-108">Implementowanie <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, lub <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interfejsu w zależności od zakresu, w którym chcesz wstawić łatwo inspektora komunikatów z usługi.</span><span class="sxs-lookup"><span data-stu-id="f0e16-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3.  <span data-ttu-id="f0e16-109">Wstaw Twoje zachowanie przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metoda <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0e16-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f0e16-110">Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="f0e16-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0e16-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0e16-111">Example</span></span>  
 <span data-ttu-id="f0e16-112">W poniższych przykładach kodu pokazano, w kolejności:</span><span class="sxs-lookup"><span data-stu-id="f0e16-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="f0e16-113">Implementacja inspektora usługi.</span><span class="sxs-lookup"><span data-stu-id="f0e16-113">A service inspector implementation.</span></span>  
  
-   <span data-ttu-id="f0e16-114">Zachowanie usługi, która wstawia Inspektor.</span><span class="sxs-lookup"><span data-stu-id="f0e16-114">A service behavior that inserts the inspector.</span></span>  
  
-   <span data-ttu-id="f0e16-115">Plik konfiguracji, który ładuje i uruchamia zachowania w aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f0e16-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="f0e16-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0e16-116">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [<span data-ttu-id="f0e16-117">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="f0e16-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
