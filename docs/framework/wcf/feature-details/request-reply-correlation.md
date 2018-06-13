---
title: Korelacja żądań i odpowiedzi
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497207"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="dab2d-102">Korelacja żądań i odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="dab2d-102">Request-Reply Correlation</span></span>
<span data-ttu-id="dab2d-103">Korelacja żądań i odpowiedzi jest używany z <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary do zaimplementowania dwukierunkowe operacji w usłudze przepływu pracy oraz <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary, który wywołuje operację dwukierunkowe w innej sieci Web Usługa.</span><span class="sxs-lookup"><span data-stu-id="dab2d-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="dab2d-104">Podczas wywoływania dwukierunkowe operacji usługi WCF, usługa może być albo tradycyjną usługi przepływu pracy może być konieczne usługi Windows Communication Foundation (WCF) oparte na kodzie lub go.</span><span class="sxs-lookup"><span data-stu-id="dab2d-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="dab2d-105">Umożliwia powiązanie dwustronne muszą być stosowane, takich jak korelacja żądań i odpowiedzi <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="dab2d-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="dab2d-106">Wywoływanie lub wykonania operacji dwukierunkowe, kroków inicjowania korelacji są podobne i są przedstawione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="dab2d-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="dab2d-107">W ramach operacji dwukierunkowe z odbierania SendReply przy użyciu korelacji</span><span class="sxs-lookup"><span data-stu-id="dab2d-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="dab2d-108">A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary jest używane do implementowania dwukierunkowe operacji w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dab2d-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="dab2d-109">Środowiska uruchomieniowego używa korelacja żądań i odpowiedzi, aby upewnić się, że odpowiedź jest wysyłane do wywołującego poprawne.</span><span class="sxs-lookup"><span data-stu-id="dab2d-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="dab2d-110">Gdy przepływ pracy jest hostowana przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>, czyli w przypadku usług przepływu pracy, a następnie inicjowanie domyślnych korelacja jest wystarczająca.</span><span class="sxs-lookup"><span data-stu-id="dab2d-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="dab2d-111">W tym scenariuszu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary jest używany przez przepływ pracy i nie jest wymagana żadna konfiguracja określonych korelacji.</span><span class="sxs-lookup"><span data-stu-id="dab2d-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="dab2d-112">Jawne inicjowanie korelacji "żądanie-odpowiedź"</span><span class="sxs-lookup"><span data-stu-id="dab2d-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="dab2d-113">W przypadku innych operacji dwukierunkowe równolegle, następnie korelacji należy jawnie skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="dab2d-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="dab2d-114">Można to zrobić, określając <xref:System.ServiceModel.Activities.CorrelationHandle> i <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, lub umieszczając <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> wewnątrz <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="dab2d-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="dab2d-115">W tym przykładzie skonfigurowano korelacja żądań i odpowiedzi na <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary.</span><span class="sxs-lookup"><span data-stu-id="dab2d-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
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
  
 <span data-ttu-id="dab2d-116">Zamiast konfigurować jawnie korelacji, <xref:System.ServiceModel.Activities.CorrelationScope> działanie może być używane.</span><span class="sxs-lookup"><span data-stu-id="dab2d-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="dab2d-117"><xref:System.ServiceModel.Activities.CorrelationScope> zapewnia niejawny <xref:System.ServiceModel.Activities.CorrelationHandle> do obsługi komunikatów działań, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="dab2d-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="dab2d-118">W tym przykładzie <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary znajduje się wewnątrz <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="dab2d-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="dab2d-119">Nie jest wymagana żadna konfiguracja jawne korelacji.</span><span class="sxs-lookup"><span data-stu-id="dab2d-119">No explicit correlation configuration is required.</span></span>  
  
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
  
 <span data-ttu-id="dab2d-120">Jeśli wymagane są dodatkowe korelacji, można je skonfigurować przy użyciu <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> właściwości odpowiednich działań komunikacji przy użyciu żądaną `CorrelationInitializer` typów.</span><span class="sxs-lookup"><span data-stu-id="dab2d-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="dab2d-121">W ramach operacji dwukierunkowe z wysyłania/ReceiveReply przy użyciu korelacji</span><span class="sxs-lookup"><span data-stu-id="dab2d-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="dab2d-122">Gdy <xref:System.ServiceModel.Activities.Receive> działania można używać tylko w obsługiwanych przez usługi przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary mogą być używane w każdy przepływ pracy, który należy wywołać metodę dla usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="dab2d-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="dab2d-123">Jeśli przepływ pracy jest hostowana przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost> , a następnie stosuje korelacji domyślne opisane w poprzedniej sekcji, ale jeśli nie, korelacji musi być skonfigurowany albo jawnie za pomocą żądaną <xref:System.ServiceModel.Activities.CorrelationInitializer> i <xref:System.ServiceModel.Activities.CorrelationHandle>, lub za pomocą niejawne Obsługa zarządzania <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="dab2d-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="dab2d-124">Korzystając z **Dodaj odwołanie do usługi** na usługi za pomocą operacji dwukierunkowe, są generowane działania tego zawijania <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> jawnie parę działania wewnętrznie o korelacji żądania/odpowiedzi określona.</span><span class="sxs-lookup"><span data-stu-id="dab2d-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
