---
title: "Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c677ed869c0e5dd0df1288de48668ba403df5aa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="60ebb-102">Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności</span><span class="sxs-lookup"><span data-stu-id="60ebb-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="60ebb-103">Usługi WCF sprawia, że żadnych gwarancji dotyczących kolejności, w jakiej są przetwarzane wiadomości, chyba że zamykania kanału źródłowego.</span><span class="sxs-lookup"><span data-stu-id="60ebb-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="60ebb-104">Dla wystąpienia usługi WCF, który używa MsmqInputChannel, który nie jest podczas zamykania kanału sesji, nie będzie można przetwarzać komunikatów w kolejności.</span><span class="sxs-lookup"><span data-stu-id="60ebb-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="60ebb-105">Istnieją pewne okoliczności, w których deweloper może mają w kolejności przetwarzania zachowanie, ale nie mają być używane sesje.</span><span class="sxs-lookup"><span data-stu-id="60ebb-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="60ebb-106">W tym temacie opisano sposób skonfigurowania tego zachowania, gdy usługa jest uruchomiona w trybie równoległym pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="60ebb-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="60ebb-107">Przetwarzanie komunikatów w kolejności</span><span class="sxs-lookup"><span data-stu-id="60ebb-107">In-order Message Processing</span></span>  
 <span data-ttu-id="60ebb-108">Nowy atrybut o nazwie <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> został dodany do <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="60ebb-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="60ebb-109">Gdy <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> jest ustawiona na wartość true i <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ustawiono <xref:System.ServiceModel.ConcurrencyMode.Single> komunikaty wysyłane do usługi będą przetwarzane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="60ebb-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="60ebb-110">Poniższy fragment kodu przedstawia sposób ustawiania tych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="60ebb-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="60ebb-111">Jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ma ustawioną wartość inną wartość <xref:System.InvalidOperationException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="60ebb-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ebb-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60ebb-112">See Also</span></span>  
 [<span data-ttu-id="60ebb-113">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="60ebb-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="60ebb-114">Współbieżność</span><span class="sxs-lookup"><span data-stu-id="60ebb-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
