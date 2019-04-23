---
title: 'Instrukcje: używanie elementu ChannelFactory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7d542a3dcae514e75194b49c23a8dec5dd7e8c3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773730"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="e980f-102">Instrukcje: używanie elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="e980f-102">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="e980f-103">Ogólny <xref:System.ServiceModel.ChannelFactory%601> klasa jest używana w zaawansowanych scenariuszach, które wymagają utworzenia fabryki kanałów, który może służyć do utworzenia kanału więcej niż jeden.</span><span class="sxs-lookup"><span data-stu-id="e980f-103">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="e980f-104">Tworzenie i używanie klasy ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="e980f-104">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="e980f-105">Skompiluj i uruchom usługę Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e980f-105">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="e980f-106">Aby uzyskać więcej informacji, zobacz [projektowanie i Implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md), i [usług obsługującego](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="e980f-106">For more information, see [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configuring Services](../../../../docs/framework/wcf/configuring-services.md), and [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
2. <span data-ttu-id="e980f-107">Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania kontraktu (interfejs) dla klienta.</span><span class="sxs-lookup"><span data-stu-id="e980f-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="e980f-108">W kodzie klienta użyć <xref:System.ServiceModel.ChannelFactory%601> klasy, aby utworzyć wiele odbiorników punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e980f-108">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e980f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e980f-109">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
