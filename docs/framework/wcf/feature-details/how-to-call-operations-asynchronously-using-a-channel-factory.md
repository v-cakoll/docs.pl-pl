---
title: "Instrukcje: Asynchroniczne wywoływanie operacji za pomocą fabryki kanałów"
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
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 216c0d529a15004ea9f7d6f087aeee4bf4f10e56
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="b6c05-102">Instrukcje: Asynchroniczne wywoływanie operacji za pomocą fabryki kanałów</span><span class="sxs-lookup"><span data-stu-id="b6c05-102">How to: Call Operations Asynchronously Using a Channel Factory</span></span>
<span data-ttu-id="b6c05-103">W tym temacie opisano, jak klienta można uzyskać dostępu do operacji usługi asynchronicznie przy użyciu <xref:System.ServiceModel.ChannelFactory%601>-aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="b6c05-103">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="b6c05-104">(Przy użyciu <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> obiekt do wywołania usługi można użyć sterowane zdarzeniami asynchroniczne wywołanie modelu.</span><span class="sxs-lookup"><span data-stu-id="b6c05-104">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="b6c05-105">Aby uzyskać więcej informacji, zobacz [porady: wywołania operacji usługi asynchronicznie](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="b6c05-105">For more information, see [How to: Call Service Operations Asynchronously](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="b6c05-106">Aby uzyskać więcej informacji na temat oparty na zdarzeniach asynchroniczne wywołanie modelu, zobacz [programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span><span class="sxs-lookup"><span data-stu-id="b6c05-106">For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span></span>  
  
 <span data-ttu-id="b6c05-107">Implementuje usługę w tym temacie `ICalculator` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b6c05-107">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="b6c05-108">Klienta można wywołać operacji w tym interfejsie asynchronicznie, co oznacza, że operacji, takich jak `Add` są podzielone na dwie metody `BeginAdd` i `EndAdd`, pierwsza z nich inicjuje połączenie i drugie, z których pobiera wynik Po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="b6c05-108">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="b6c05-109">Przykład pokazujący sposób zaimplementować operację asynchronicznie w usłudze, zobacz [porady: Implementowanie asynchronicznej operacji usługi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="b6c05-109">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="b6c05-110">Aby uzyskać szczegółowe informacje o operacjach synchroniczne i asynchroniczne, zobacz [synchroniczne i asynchroniczne operacje](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b6c05-110">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="b6c05-111">Procedura</span><span class="sxs-lookup"><span data-stu-id="b6c05-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="b6c05-112">Aby asynchroniczne wywoływanie operacji usługi WCF</span><span class="sxs-lookup"><span data-stu-id="b6c05-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="b6c05-113">Uruchom [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia z `/async` opcji, jak pokazano w poniższym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="b6c05-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="b6c05-114">Powoduje to wersja klienta asynchroniczne kontraktu usługi dla tej operacji.</span><span class="sxs-lookup"><span data-stu-id="b6c05-114">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2.  <span data-ttu-id="b6c05-115">Utwórz funkcję wywołania zwrotnego wywoływana, gdy operacja asynchroniczna jest zakończone, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="b6c05-115">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  <span data-ttu-id="b6c05-116">Aby uzyskać dostęp do operacji usługi asynchronicznie, należy utworzyć klienta i wywołania `Begin[Operation]` (na przykład `BeginAdd`) i określ funkcję wywołania zwrotnego, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="b6c05-116">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="b6c05-117">Podczas funkcja wywołania zwrotnego, gdy klient wywołuje `End<operation>` (na przykład `EndAdd`) można pobrać wyniku.</span><span class="sxs-lookup"><span data-stu-id="b6c05-117">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6c05-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6c05-118">Example</span></span>  
 <span data-ttu-id="b6c05-119">Implementuje usługę, która jest używana z kodu klienta, który jest używany w poprzedniej procedurze `ICalculator` interfejsu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b6c05-119">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="b6c05-120">Na stronie usługi `Add` i `Subtract` operacji kontraktu są wywoływane przez synchronicznie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] wykonawczego, nawet jeśli poprzednie kroki klienta są wywoływane asynchronicznie na kliencie.</span><span class="sxs-lookup"><span data-stu-id="b6c05-120">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="b6c05-121">`Multiply` i `Divide` operacje są używane do wywoływania usługi asynchronicznie po stronie usługi nawet wtedy, gdy klient wywołuje ich synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="b6c05-121">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="b6c05-122">W tym przykładzie <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="b6c05-122">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="b6c05-123">Ustawienie właściwości w połączeniu z implementacją [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wzorca asynchronicznego, określa, że czas uruchomienia do asynchronicznego wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="b6c05-123">This property setting, in combination with the implementation of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b6c05-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6c05-124">See Also</span></span>  
 [<span data-ttu-id="b6c05-125">Kontraktu usługi: Przykładowe asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="b6c05-125">Service Contract: Asynchronous Sample</span></span>](http://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7)
