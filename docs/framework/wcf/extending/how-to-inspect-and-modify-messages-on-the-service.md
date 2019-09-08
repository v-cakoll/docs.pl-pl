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
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="fb4a3-102">Instrukcje: sprawdzanie i modyfikowanie komunikatów w usłudze</span><span class="sxs-lookup"><span data-stu-id="fb4a3-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="fb4a3-103">Możesz sprawdzić lub zmodyfikować komunikaty przychodzące lub wychodzące dla klienta Windows Communication Foundation (WCF), implementując <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> i wstawiając go do środowiska uruchomieniowego usługi.</span><span class="sxs-lookup"><span data-stu-id="fb4a3-103">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="fb4a3-104">Aby uzyskać więcej informacji, zobacz [rozszerzanie dyspozytorów](extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="fb4a3-104">For more information, see [Extending Dispatchers](extending-dispatchers.md).</span></span> <span data-ttu-id="fb4a3-105">Równoważna funkcja w usłudze to <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb4a3-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="fb4a3-106">Aby sprawdzić lub zmodyfikować komunikaty</span><span class="sxs-lookup"><span data-stu-id="fb4a3-106">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="fb4a3-107">Implementowanie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fb4a3-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="fb4a3-108">Zaimplementuj Interfejs <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> , lub, w zależności od zakresu, w którym chcesz łatwo wstawić inspektora komunikatów usługi. <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fb4a3-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3. <span data-ttu-id="fb4a3-109">Wstaw zachowanie przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metody <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>na.</span><span class="sxs-lookup"><span data-stu-id="fb4a3-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fb4a3-110">Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="fb4a3-110">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb4a3-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb4a3-111">Example</span></span>  
 <span data-ttu-id="fb4a3-112">Poniższy przykład kodu pokazuje, w kolejności:</span><span class="sxs-lookup"><span data-stu-id="fb4a3-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="fb4a3-113">Implementacja inspektora usługi.</span><span class="sxs-lookup"><span data-stu-id="fb4a3-113">A service inspector implementation.</span></span>  
  
- <span data-ttu-id="fb4a3-114">Zachowanie usługi, które wstawia inspektora.</span><span class="sxs-lookup"><span data-stu-id="fb4a3-114">A service behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="fb4a3-115">Plik konfiguracji, który ładuje i uruchamia zachowanie w aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="fb4a3-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="fb4a3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb4a3-116">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="fb4a3-117">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="fb4a3-117">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
