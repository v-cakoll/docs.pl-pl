---
title: Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: ecabb9a6e838b0137c538d76c554646356ea87f5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991501"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="0d385-102">Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności</span><span class="sxs-lookup"><span data-stu-id="0d385-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="0d385-103">Funkcja WCF nie gwarantuje kolejności, w której przetwarzane są komunikaty, chyba że źródłowy kanał to sesja.</span><span class="sxs-lookup"><span data-stu-id="0d385-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="0d385-104">Na przykład usługa WCF korzystająca z MsmqInputChannel, która nie jest kanałem sesji, nie przetwarza komunikatów w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="0d385-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="0d385-105">Istnieją pewne sytuacje, w których deweloper może chcieć wykonać przetwarzanie w kolejności, ale nie chce używać sesji.</span><span class="sxs-lookup"><span data-stu-id="0d385-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="0d385-106">W tym temacie opisano sposób konfigurowania tego zachowania, gdy usługa jest uruchomiona w trybie pojedynczego współbieżności.</span><span class="sxs-lookup"><span data-stu-id="0d385-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="0d385-107">Przetwarzanie komunikatów w porządku</span><span class="sxs-lookup"><span data-stu-id="0d385-107">In-order Message Processing</span></span>  
 <span data-ttu-id="0d385-108"><xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> Dodano<xref:System.ServiceModel.ServiceBehaviorAttribute>nowy atrybut o nazwie.</span><span class="sxs-lookup"><span data-stu-id="0d385-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="0d385-109">Gdy <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> jest ustawiona na wartość true <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> i jest ustawiona <xref:System.ServiceModel.ConcurrencyMode.Single> na komunikaty wysyłane do usługi, zostanie przetworzona w kolejności.</span><span class="sxs-lookup"><span data-stu-id="0d385-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="0d385-110">Poniższy fragment kodu ilustruje sposób ustawiania tych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0d385-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="0d385-111">Jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> jest ustawiona na inną wartość <xref:System.InvalidOperationException> , zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="0d385-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d385-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d385-112">See also</span></span>

- [<span data-ttu-id="0d385-113">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="0d385-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="0d385-114">Współbieżność</span><span class="sxs-lookup"><span data-stu-id="0d385-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
