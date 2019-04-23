---
title: 'Instrukcje: sprawdzanie lub modyfikowanie parametrów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 2e294b7970a58fad9385802470a514e5a9240495
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303976"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="c4e6c-102">Instrukcje: sprawdzanie lub modyfikowanie parametrów</span><span class="sxs-lookup"><span data-stu-id="c4e6c-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="c4e6c-103">Można sprawdzić i modyfikować wiadomości przychodzących lub wychodzących dla jednej operacji na obiekt klienta usługi Windows Communication Foundation (WCF) lub usługi WCF poprzez implementację <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interfejsu i wstawiania ich do środowiska uruchomieniowego klienta lub usługę.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-103">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="c4e6c-104">Zwykle to zachowanie operacja służy do dodawania inspektorzy parametr dla jednej operacji. innych zachowań może służyć do zapewnienia łatwy dostęp do środowiska uruchomieniowego w zakresie większa.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="c4e6c-105">Aby uzyskać więcej informacji, zobacz [rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md) i [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="c4e6c-105">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md) and [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="c4e6c-106">Inspekcja lub modyfikowanie parametrów</span><span class="sxs-lookup"><span data-stu-id="c4e6c-106">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="c4e6c-107">Implementowanie <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="c4e6c-108">Implementowanie <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (w zależności od wymagany zakres) do dodania usługi Inspektor parametru do listy <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="c4e6c-109">Wstaw swoje zachowanie przed wywołaniem <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metody <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c4e6c-110">Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="c4e6c-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4e6c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4e6c-111">Example</span></span>  
 <span data-ttu-id="c4e6c-112">Pokaż w poniższych przykładach kodu w kolejności:</span><span class="sxs-lookup"><span data-stu-id="c4e6c-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="c4e6c-113">Implementacja Inspektor parametru.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-113">A parameter inspector implementation.</span></span>  
  
-   <span data-ttu-id="c4e6c-114">Implementacja zachowanie, który wstawia Inspektor parametru za pomocą <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>i <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="c4e6c-115">Plik konfiguracji, który ładuje i uruchamia zachowanie punktu końcowego w aplikacji klienckiej, aby wstawić Inspektor parametru na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c4e6c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4e6c-116">See also</span></span>

- [<span data-ttu-id="c4e6c-117">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="c4e6c-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
