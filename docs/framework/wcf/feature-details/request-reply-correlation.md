---
title: Korelacja żądań i odpowiedzi
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991136"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="754c5-102">Korelacja żądań i odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="754c5-102">Request-Reply Correlation</span></span>
<span data-ttu-id="754c5-103">Korelacja żądań i odpowiedzi jest używany z <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Paruj, aby zaimplementować dwukierunkowe operacji w usłudze przepływu pracy i <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> parą, która wywołuje dwukierunkowe operacji w innej sieci Web Usługa.</span><span class="sxs-lookup"><span data-stu-id="754c5-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="754c5-104">Podczas wywoływania dwukierunkowe operacji usługi WCF, usługa może być albo tradycyjne imperatywne oparte na kodzie usługi Windows Communication Foundation (WCF) lub może być usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="754c5-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="754c5-105">Aby użyć korelacji "żądanie-odpowiedź" powiązanie dwustronne należy użyć, takie jak <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="754c5-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="754c5-106">Czy wywołania Implementowanie dwukierunkowej operacji, kroków inicjowania korelacji są podobne i zostały omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="754c5-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="754c5-107">W ramach operacji dwukierunkowego z otrzymywać SendReply przy użyciu korelacji</span><span class="sxs-lookup"><span data-stu-id="754c5-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="754c5-108">A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary jest używany do implementowania dwukierunkowe operacji w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="754c5-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="754c5-109">Środowisko wykonawcze używa korelacji "żądanie-odpowiedź", aby upewnić się, że odpowiedź jest wysyłane do poprawny obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="754c5-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="754c5-110">Gdy przepływ pracy znajduje się za pomocą <xref:System.ServiceModel.Activities.WorkflowServiceHost>, co ma miejsce w przypadku usług przepływu pracy, a następnie inicjowanie korelacji domyślne są wystarczające.</span><span class="sxs-lookup"><span data-stu-id="754c5-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="754c5-111">W tym scenariuszu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary jest używany w ramach przepływu pracy i jest wymagana żadna konfiguracja określonych korelacji.</span><span class="sxs-lookup"><span data-stu-id="754c5-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="754c5-112">Jawne inicjowanie korelacji "żądanie-odpowiedź"</span><span class="sxs-lookup"><span data-stu-id="754c5-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="754c5-113">W przypadku innych operacji dwukierunkowe w sposób równoległy, następnie korelacji powinny być jawnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="754c5-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="754c5-114">Można to zrobić, określając <xref:System.ServiceModel.Activities.CorrelationHandle> i <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, lub poprzez umieszczenie <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> wewnątrz <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="754c5-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="754c5-115">W tym przykładzie korelacja żądań i odpowiedzi jest konfigurowany na <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary.</span><span class="sxs-lookup"><span data-stu-id="754c5-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 <span data-ttu-id="754c5-116">Zamiast konfigurować jawnie korelacji, <xref:System.ServiceModel.Activities.CorrelationScope> działanie może być używane.</span><span class="sxs-lookup"><span data-stu-id="754c5-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="754c5-117"><xref:System.ServiceModel.Activities.CorrelationScope> zapewnia niejawny <xref:System.ServiceModel.Activities.CorrelationHandle> do działań dotyczących komunikatów, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="754c5-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="754c5-118">W tym przykładzie <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary znajduje się wewnątrz <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="754c5-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="754c5-119">Jawne korelacji jest wymagana żadna konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="754c5-119">No explicit correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =   
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 <span data-ttu-id="754c5-120">Jeśli wymagane są dodatkowe korelacji, a następnie takie grupy można skonfigurować przy użyciu <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> właściwość odpowiednich działań dotyczących komunikatów za pomocą żądaną `CorrelationInitializer` typów.</span><span class="sxs-lookup"><span data-stu-id="754c5-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="754c5-121">Przy użyciu korelacja dwukierunkowa operacji za pomocą wysyłania/ReceiveReply</span><span class="sxs-lookup"><span data-stu-id="754c5-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="754c5-122">Gdy <xref:System.ServiceModel.Activities.Receive> działania można używać tylko w usłudze przepływu pracy pracujących na <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary mogą być używane w każdym przepływie pracy, należy wywołać metody usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="754c5-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="754c5-123">Jeśli przepływ pracy znajduje się za pomocą <xref:System.ServiceModel.Activities.WorkflowServiceHost> , a następnie stosuje korelacji domyślnej opisanego w poprzedniej sekcji, ale jeśli nie, następnie korelacji musi być skonfigurowany jawnie za pomocą żądaną <xref:System.ServiceModel.Activities.CorrelationInitializer> i <xref:System.ServiceModel.Activities.CorrelationHandle>, lub za pomocą niejawny Obsługa zarządzania <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="754c5-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="754c5-124">Korzystając z **Dodaj odwołanie do usługi** usłudze z operacjami dwukierunkowe są generowane działania tego zawijania <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> jawnie pair działania wewnętrznie z korelacją żądanie/nietypizowana odpowiedź określona.</span><span class="sxs-lookup"><span data-stu-id="754c5-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
