---
title: "Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b7e00e70bab0c5652bbc721d582a1b276e6a3fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a><span data-ttu-id="7cd99-102">Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF</span><span class="sxs-lookup"><span data-stu-id="7cd99-102">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>
<span data-ttu-id="7cd99-103"><xref:System.ServiceModel.Description.ServiceThrottlingBehavior> Klasa udostępnia właściwości, które można użyć, aby ograniczyć liczbę wystąpień lub sesji są tworzone na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd99-103">The <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class exposes properties that you can use to limit how many instances or sessions are created at the application level.</span></span> <span data-ttu-id="7cd99-104">Za pomocą tego zachowania, można dostosować wydajność sieci [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd99-104">Using this behavior, you can fine-tune the performance of your [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a><span data-ttu-id="7cd99-105">Kontrolowanie wystąpień usługi i równoczesnych wywołań</span><span class="sxs-lookup"><span data-stu-id="7cd99-105">Controlling Service Instances and Concurrent Calls</span></span>  
 <span data-ttu-id="7cd99-106">Użyj <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> właściwość, aby określić maksymalną liczbę komunikatów aktywnie przetwarzanych w obrębie <xref:System.ServiceModel.ServiceHost> klasy, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> właściwość, aby określić maksymalną liczbę <xref:System.ServiceModel.InstanceContext> obiektów w usłudze.</span><span class="sxs-lookup"><span data-stu-id="7cd99-106">Use the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> property to specify the maximum number of messages actively processing across a <xref:System.ServiceModel.ServiceHost> class, and the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> property to specify the maximum number of <xref:System.ServiceModel.InstanceContext> objects in the service.</span></span>  
  
 <span data-ttu-id="7cd99-107">Ponieważ określania ustawień tych właściwości zwykle odbywa się po rzeczywistych środowisko uruchamiania aplikacji przed ładowania ustawień <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> właściwości jest zazwyczaj określana w konfiguracji aplikacji plików przy użyciu [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7cd99-107">Because determining the settings for these properties usually takes place after real-world experience running the application against loads, the settings for the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> properties is typically specified in an application configuration file using the [\<serviceThrottling>](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) element.</span></span>  
  
 <span data-ttu-id="7cd99-108">W poniższym przykładzie pokazano sposób użycia <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> klasy z pliku konfiguracji aplikacji, która ustawia <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, i <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> właściwości na wartość 1 jako przykład prosta.</span><span class="sxs-lookup"><span data-stu-id="7cd99-108">The following code example shows the use of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class from an application configuration file that sets the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> properties to 1 as a trivial example.</span></span> <span data-ttu-id="7cd99-109">Praktyczne doświadczenie określa optymalne ustawienia dla każdej określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cd99-109">Real-world experience determines the optimal settings for any particular application.</span></span>  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 <span data-ttu-id="7cd99-110">Dokładne zachowania w czasie wykonywania zależy od wartości <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> i <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości, które kontrolują, ile komunikatów można wykonać wewnątrz operacji jednocześnie i okresy istnienia usługi <xref:System.ServiceModel.InstanceContext> względem przychodzących sesji kanału , odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="7cd99-110">The exact run-time behavior depends upon the values of the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> and <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> properties, which control how many messages can execute inside an operation at once and the lifetimes of the service <xref:System.ServiceModel.InstanceContext> relative to incoming channel sessions, respectively.</span></span>  
  
 <span data-ttu-id="7cd99-111">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, i <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span><span class="sxs-lookup"><span data-stu-id="7cd99-111">For details, see <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cd99-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cd99-112">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
