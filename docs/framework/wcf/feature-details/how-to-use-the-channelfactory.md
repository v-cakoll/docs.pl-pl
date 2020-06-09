---
title: 'Instrukcje: Używanie elementu ChannelFactory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 4bb2053fb50931756e79d5346a3f14d2acbe04f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595313"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="82084-102">Instrukcje: Używanie elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="82084-102">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="82084-103">Klasa generyczna <xref:System.ServiceModel.ChannelFactory%601> jest używana w zaawansowanych scenariuszach, które wymagają utworzenia fabryki kanałów, której można użyć do utworzenia więcej niż jednego kanału.</span><span class="sxs-lookup"><span data-stu-id="82084-103">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="82084-104">Aby utworzyć i użyć klasy ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="82084-104">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="82084-105">Kompiluj i uruchamiaj usługę Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="82084-105">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="82084-106">Aby uzyskać więcej informacji, zobacz [projektowanie i implementowanie usług](../designing-and-implementing-services.md), [Konfigurowanie usług](../configuring-services.md)i [usług hostingowych](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="82084-106">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="82084-107">Użyj [Narzędzia do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania kontraktu (interfejsu) dla klienta.</span><span class="sxs-lookup"><span data-stu-id="82084-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="82084-108">W kodzie klienta Użyj <xref:System.ServiceModel.ChannelFactory%601> klasy, aby utworzyć odbiorniki wielu punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="82084-108">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82084-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="82084-109">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
