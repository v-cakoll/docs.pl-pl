---
title: 'Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 9a7bd1d67d9730c75e3f3f3b1eeb59f5d2d3c49a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204838"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="1541e-102">Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF</span><span class="sxs-lookup"><span data-stu-id="1541e-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="1541e-103">W tym temacie opisano, jak klient może uzyskać dostęp do operacji usługi asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="1541e-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="1541e-104">Implementuje usługę, w tym temacie `ICalculator` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1541e-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="1541e-105">Klient może asynchroniczne wywoływanie operacji w tym interfejsie przy użyciu oparte na zdarzeniach asynchronicznych wywoływania modelu.</span><span class="sxs-lookup"><span data-stu-id="1541e-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="1541e-106">(Aby uzyskać więcej informacji na temat oparte na zdarzeniach asynchronicznych wywoływania modelu, zobacz [programowania wielowątkowe, za pomocą wzorca asynchronicznego opartego na zdarzeniach](https://go.microsoft.com/fwlink/?LinkId=248184)).</span><span class="sxs-lookup"><span data-stu-id="1541e-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="1541e-107">Aby uzyskać przykład przedstawia sposób implementowania operacji asynchronicznie w ramach usługi, zobacz [jak: Implementowanie asynchronicznej operacji usługi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="1541e-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="1541e-108">Aby uzyskać więcej informacji na temat operacje synchroniczne i asynchroniczne, zobacz [synchroniczne i asynchroniczne operacje](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="1541e-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1541e-109">Oparte na zdarzeniach asynchronicznych wywoływania modelu nie jest obsługiwane w przypadku korzystania <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="1541e-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="1541e-110">Uzyskać informacji na temat wywołań asynchronicznych za pomocą <xref:System.ServiceModel.ChannelFactory%601>, zobacz [jak: Wywoływanie operacji asynchronicznie za pomocą fabryki kanałów](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="1541e-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="1541e-111">Procedura</span><span class="sxs-lookup"><span data-stu-id="1541e-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="1541e-112">Aby asynchroniczne wywoływanie operacji usługi WCF</span><span class="sxs-lookup"><span data-stu-id="1541e-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="1541e-113">Uruchom [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie zarówno `/async` i `/tcv:Version35` polecenia Opcje ze sobą, jak pokazano w poniższym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="1541e-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="1541e-114">Spowoduje to wygenerowanie, oprócz synchroniczne i standardowych opartych na delegacie operacji asynchronicznych, klasa klienta WCF, która zawiera:</span><span class="sxs-lookup"><span data-stu-id="1541e-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    -   <span data-ttu-id="1541e-115">Dwa <`operationName` > `Async` operacje do użytku z programem oparte na zdarzeniach asynchronicznych wywoływania podejście.</span><span class="sxs-lookup"><span data-stu-id="1541e-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="1541e-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1541e-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   <span data-ttu-id="1541e-117">Ukończono operację zdarzenia w postaci <`operationName` > `Completed` do użytku z programem oparte na zdarzeniach asynchronicznych wywoływania podejście.</span><span class="sxs-lookup"><span data-stu-id="1541e-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="1541e-118">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1541e-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType> <span data-ttu-id="1541e-119">typy dla każdej operacji (w postaci <`operationName`>`CompletedEventArgs`) do użytku z programem oparte na zdarzeniach asynchronicznych wywoływania podejście.</span><span class="sxs-lookup"><span data-stu-id="1541e-119">types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="1541e-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1541e-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  <span data-ttu-id="1541e-121">W aplikacji wywołującej Utwórz metody wywołania zwrotnego wywoływana, gdy operacja asynchroniczna jest zakończona, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1541e-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  <span data-ttu-id="1541e-122">Przed wywołaniem operacji, korzystają z ogólnego nowe <xref:System.EventHandler%601?displayProperty=nameWithType> typu <`operationName` > `EventArgs` dodać metodę procedury obsługi (utworzonym w poprzednim kroku) do <`operationName` > `Completed` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1541e-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="1541e-123">Następnie wywołaj <`operationName` > `Async` metody.</span><span class="sxs-lookup"><span data-stu-id="1541e-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="1541e-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1541e-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="1541e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1541e-125">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1541e-126">Dotyczących projektowania opartego na zdarzeniach modelu asynchronicznego stanu, że jeśli zwracana jest więcej niż jedną wartość, jedną wartość jest zwracana jako `Result` właściwości i inne są zwracane jako właściwości na <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1541e-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="1541e-127">Jeden wynik tego jest to, że jeśli klient importuje metadane przy użyciu opcji oparte na zdarzeniach asynchronicznych polecenia, a operacja zwraca więcej niż jedną wartość, wartość domyślna <xref:System.EventArgs> zwraca jedną wartość jako `Result` właściwość i pozostałej właściwości <xref:System.EventArgs> obiektu. Jeśli chcesz otrzymywać obiekt komunikatu jako `Result` właściwości i mają zwracanych wartości, jak używać właściwości dla tego obiektu `/messageContract` opcja polecenia.</span><span class="sxs-lookup"><span data-stu-id="1541e-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="1541e-128">Spowoduje to wygenerowanie sygnaturę, która zwraca komunikat odpowiedzi jako `Result` właściwość <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1541e-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="1541e-129">Wszystkie wewnętrzne wartości zwracane są następnie właściwości obiektu komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1541e-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="1541e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1541e-130">See also</span></span>

- [<span data-ttu-id="1541e-131">Instrukcje: Wdrażanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="1541e-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
