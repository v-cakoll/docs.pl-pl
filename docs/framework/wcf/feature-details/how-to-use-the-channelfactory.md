---
title: "Instrukcje: Używanie elementu ChannelFactory"
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
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37ad5181ad140c3ef3ea8ba5b3774fd44310dca7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="63ba9-102">Instrukcje: Używanie elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="63ba9-102">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="63ba9-103">Ogólnego <xref:System.ServiceModel.ChannelFactory%601> klasa jest używana w zaawansowanych scenariuszach, które wymagają utworzenia fabryki kanałów, który może służyć do tworzenia więcej niż jeden kanał.</span><span class="sxs-lookup"><span data-stu-id="63ba9-103">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="63ba9-104">Tworzenie i używanie klasy ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="63ba9-104">To create and use the ChannelFactory class</span></span>  
  
1.  <span data-ttu-id="63ba9-105">Tworzenie i uruchamianie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="63ba9-105">Build and run an [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="63ba9-106">[Projektowanie i Implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md), i [usług hostingu](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="63ba9-106"> [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configuring Services](../../../../docs/framework/wcf/configuring-services.md), and [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
2.  <span data-ttu-id="63ba9-107">Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania kontraktu (interfejs) dla klienta.</span><span class="sxs-lookup"><span data-stu-id="63ba9-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3.  <span data-ttu-id="63ba9-108">W kodzie klienta, użyj <xref:System.ServiceModel.ChannelFactory%601> klasę, aby utworzyć wiele odbiorników punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="63ba9-108">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63ba9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="63ba9-109">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
