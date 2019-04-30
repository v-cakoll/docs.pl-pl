---
title: Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: 785c2953e57eaf967209b0d9e52ab85a3a99c450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769450"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="fc093-102">Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności</span><span class="sxs-lookup"><span data-stu-id="fc093-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="fc093-103">Usługi WCF sprawia, że żadnej gwarancji dotyczącej kolejności, w jakiej komunikaty są przetwarzane, chyba że przekroczono kanału źródłowego.</span><span class="sxs-lookup"><span data-stu-id="fc093-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="fc093-104">Na przykład usługi WCF, która używa MsmqInputChannel, który nie jest kanału sesji, zakończy się niepowodzeniem do przetwarzania wiadomości w kolejności.</span><span class="sxs-lookup"><span data-stu-id="fc093-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="fc093-105">Istnieją pewne okoliczności, w której deweloper może ma zachowanie za przetwarzanie zamówień w, ale nie mają być używane sesji.</span><span class="sxs-lookup"><span data-stu-id="fc093-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="fc093-106">W tym temacie opisano sposób konfigurowania tego zachowania, gdy usługa jest uruchomiona w trybie pojedynczej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="fc093-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="fc093-107">W określonej kolejności przetwarzania wiadomości</span><span class="sxs-lookup"><span data-stu-id="fc093-107">In-order Message Processing</span></span>  
 <span data-ttu-id="fc093-108">Nowy atrybut o nazwie <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> została dodana do <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fc093-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="fc093-109">Gdy <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> jest ustawiona na wartość true i <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> jest ustawiona na <xref:System.ServiceModel.ConcurrencyMode.Single> komunikaty wysyłane do usługi, które będą przetwarzane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="fc093-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="fc093-110">Poniższy fragment kodu przedstawia sposób ustawiania tych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="fc093-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="fc093-111">Jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> jest ustawiona na jakąkolwiek inną wartość, <xref:System.InvalidOperationException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="fc093-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc093-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc093-112">See also</span></span>

- [<span data-ttu-id="fc093-113">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="fc093-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="fc093-114">Współbieżność</span><span class="sxs-lookup"><span data-stu-id="fc093-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
