---
title: Korelacja żądań i odpowiedzi
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: 34a41a149e740faf0f3816bba2c9bd9b47d4996e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184543"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="6a1e3-102">Korelacja żądań i odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="6a1e3-102">Request-Reply Correlation</span></span>
<span data-ttu-id="6a1e3-103">Korelacja żądanie-odpowiedź jest używana <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> z parą w celu zaimplementowania <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> operacji dwukierunkowej w usłudze przepływu pracy i z parą, która wywołuje operację dwukierunkową w innej usłudze sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="6a1e3-104">Podczas wywoływania operacji dwukierunkowej w usłudze WCF usługa może być tradycyjną usługą Fundacji komunikacji systemu Windows (WCF) opartą na kodzie imperatywu lub może być usługą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="6a1e3-105">Aby użyć korelacji żądanie odpowiedź musi być używany dwukierunkowe powiązanie, takie jak <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="6a1e3-106">Niezależnie od tego, czy jest wywoływanie lub implementowanie operacji dwukierunkowej, kroki inicjowania korelacji są podobne i są omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="6a1e3-107">Korzystanie z korelacji w operacji dwukierunkowej z odbierania/wysyłania</span><span class="sxs-lookup"><span data-stu-id="6a1e3-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="6a1e3-108"><xref:System.ServiceModel.Activities.Receive> / Para <xref:System.ServiceModel.Activities.SendReply> jest używana do implementowania operacji dwukierunkowej w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="6a1e3-109">Środowisko wykonawcze używa korelacji żądanie odpowiedź, aby upewnić się, że odpowiedź jest wywoływana do poprawnego wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="6a1e3-110">Gdy przepływ pracy jest <xref:System.ServiceModel.Activities.WorkflowServiceHost>obsługiwany przy użyciu , co ma miejsce w przypadku usług przepływu pracy, wystarczy domyślna inicjalizacja korelacji.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="6a1e3-111">W tym scenariuszu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> para jest używana przez przepływ pracy i nie jest wymagana określona konfiguracja korelacji.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="6a1e3-112">Jawnie inicjowanie korelacji żądanie-odpowiedź</span><span class="sxs-lookup"><span data-stu-id="6a1e3-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="6a1e3-113">Jeśli inne operacje dwukierunkowe są równolegle, a następnie korelacji powinny być jawnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="6a1e3-114">Można to zrobić, określając <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>i , lub <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> umieszczając <xref:System.ServiceModel.Activities.CorrelationScope>wnętrze .</span><span class="sxs-lookup"><span data-stu-id="6a1e3-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="6a1e3-115">W tym przykładzie korelacja żądanie odpowiedź jest <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> skonfigurowany na parze.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
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
  
 <span data-ttu-id="6a1e3-116">Zamiast jawnie konfigurowania korelacji, <xref:System.ServiceModel.Activities.CorrelationScope> działania mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="6a1e3-117"><xref:System.ServiceModel.Activities.CorrelationScope>udostępnia niejawne <xref:System.ServiceModel.Activities.CorrelationHandle> działania obsługi wiadomości, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="6a1e3-118">W tym przykładzie <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> para znajduje <xref:System.ServiceModel.Activities.CorrelationScope>się wewnątrz pliku .</span><span class="sxs-lookup"><span data-stu-id="6a1e3-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="6a1e3-119">Nie jest wymagana jawna konfiguracja korelacji.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-119">No explicit correlation configuration is required.</span></span>  
  
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
  
 <span data-ttu-id="6a1e3-120">Jeśli wymagane są dodatkowe korelacje, można je <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> skonfigurować przy użyciu właściwości odpowiednich `CorrelationInitializer` działań obsługi wiadomości przy użyciu żądanych typów.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="6a1e3-121">Korzystanie z korelacji w operacji dwukierunkowej z wyślij/odbierz</span><span class="sxs-lookup"><span data-stu-id="6a1e3-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="6a1e3-122">Podczas <xref:System.ServiceModel.Activities.Receive> gdy działanie może być używane tylko w <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> usłudze <xref:System.ServiceModel.Activities.Send> / przepływu pracy obsługiwanej przez program , a <xref:System.ServiceModel.Activities.ReceiveReply> para może być używana w dowolnym przepływie pracy, który musi wywołać metodę w usłudze sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="6a1e3-123">Jeśli przepływ pracy jest <xref:System.ServiceModel.Activities.WorkflowServiceHost> obsługiwany przy użyciu, stosuje się domyślną korelację opisaną w poprzedniej sekcji, ale jeśli nie, <xref:System.ServiceModel.Activities.CorrelationInitializer> to <xref:System.ServiceModel.Activities.CorrelationHandle>korelacja musi być skonfigurowana <xref:System.ServiceModel.Activities.CorrelationScope>jawnie przy użyciu żądanego i , lub za pomocą zarządzania niejawnymi uchwytami .</span><span class="sxs-lookup"><span data-stu-id="6a1e3-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="6a1e3-124">Podczas korzystania z **add service reference** w usłudze z operacji <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> dwukierunkowych, działania są generowane, które zawijają działanie pary wewnętrznie z żądaniem/odpowiedzi korelacji jawnie określone.</span><span class="sxs-lookup"><span data-stu-id="6a1e3-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
