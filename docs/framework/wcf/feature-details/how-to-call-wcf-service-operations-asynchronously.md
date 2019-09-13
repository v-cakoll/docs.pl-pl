---
title: 'Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 2c0a6f1477ceec5471c22fa3e46d85f5856b298e
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895066"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="1e18b-102">Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF</span><span class="sxs-lookup"><span data-stu-id="1e18b-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="1e18b-103">W tym temacie opisano, jak klient może asynchronicznie uzyskiwać dostęp do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="1e18b-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="1e18b-104">Usługa w tym temacie implementuje `ICalculator` interfejs.</span><span class="sxs-lookup"><span data-stu-id="1e18b-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="1e18b-105">Klient może wywoływać operacje w tym interfejsie asynchronicznie przy użyciu opartego na zdarzeniach asynchronicznego modelu wywoływania.</span><span class="sxs-lookup"><span data-stu-id="1e18b-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="1e18b-106">(Aby uzyskać więcej informacji o asynchronicznym modelu wywoływania opartych na zdarzeniach, zobacz [programowanie wielowątkowe ze wzorcem asynchronicznym opartym na zdarzeniach](https://go.microsoft.com/fwlink/?LinkId=248184)).</span><span class="sxs-lookup"><span data-stu-id="1e18b-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="1e18b-107">Aby zapoznać się z przykładem, który pokazuje, jak zaimplementować operację asynchronicznie w [usłudze, zobacz How to: Implementowanie asynchronicznej operacji](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)usługi.</span><span class="sxs-lookup"><span data-stu-id="1e18b-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="1e18b-108">Aby uzyskać więcej informacji na temat operacji synchronicznych i asynchronicznych, zobacz [Operacje synchroniczne i asynchroniczne](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="1e18b-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e18b-109">Asynchroniczny model wywoływania oparty na zdarzeniach nie jest obsługiwany w przypadku <xref:System.ServiceModel.ChannelFactory%601>korzystania z programu.</span><span class="sxs-lookup"><span data-stu-id="1e18b-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="1e18b-110">Aby uzyskać informacje na temat wykonywania wywołań asynchronicznych przy [użyciu <xref:System.ServiceModel.ChannelFactory%601>, zobacz How to: Asynchroniczne wywoływanie operacji przy użyciu fabryki](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)kanałów.</span><span class="sxs-lookup"><span data-stu-id="1e18b-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="1e18b-111">Procedura</span><span class="sxs-lookup"><span data-stu-id="1e18b-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="1e18b-112">Aby asynchronicznie wywoływać operacje usługi WCF</span><span class="sxs-lookup"><span data-stu-id="1e18b-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="1e18b-113">Uruchom narzędzie do [przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) za pomocą obu `/async` opcji poleceń `/tcv:Version35` i, jak pokazano w poniższym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="1e18b-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="1e18b-114">Spowoduje to wygenerowanie, oprócz synchronicznych i standardowych operacji asynchronicznych opartych na delegatach, klasy klienta WCF, która zawiera:</span><span class="sxs-lookup"><span data-stu-id="1e18b-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="1e18b-115">Dwie <`operationName` > operacjidoużyciazpodejściemasynchronicznym`Async` wywołującym zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1e18b-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="1e18b-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1e18b-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="1e18b-117">Zdarzenia ukończone w formularzu <`operationName` > `Completed` do użycia z podejściem asynchronicznym wywołującym zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1e18b-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="1e18b-118">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1e18b-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="1e18b-119"><xref:System.EventArgs?displayProperty=nameWithType>typy dla każdej operacji (formularza <`operationName`>`CompletedEventArgs`) do użycia z podejściem asynchronicznym wywołującym zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1e18b-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="1e18b-120">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1e18b-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="1e18b-121">W aplikacji wywołującej Utwórz metodę wywołania zwrotnego, która ma być wywoływana po zakończeniu operacji asynchronicznej, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1e18b-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="1e18b-122">Przed wywołaniem operacji <xref:System.EventHandler%601?displayProperty=nameWithType> należy użyć nowego typu ogólnego <`operationName` > `EventArgs` , aby dodać metodę procedury obsługi (utworzoną w poprzednim kroku) do zdarzenia <`operationName`. > `Completed`</span><span class="sxs-lookup"><span data-stu-id="1e18b-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="1e18b-123">Następnie Wywołaj metodę`operationName` <> `Async` .</span><span class="sxs-lookup"><span data-stu-id="1e18b-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="1e18b-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1e18b-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="1e18b-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e18b-125">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e18b-126">Wskazówki dotyczące projektowania dla asynchronicznego stanu modelu opartego na zdarzeniach, które w przypadku zwrócenia więcej niż jednej wartości, jedna wartość jest zwracana `Result` jako właściwość, a pozostałe są zwracane jako właściwości <xref:System.EventArgs> w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="1e18b-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="1e18b-127">W związku z tym, jeśli klient Importuje metadane przy użyciu opcji poleceń asynchronicznych opartych na zdarzeniach, a operacja zwraca więcej niż jedną wartość, <xref:System.EventArgs> obiekt domyślny zwraca jedną wartość `Result` jako właściwość, a reszta jest <xref:System.EventArgs> właściwości obiektu. Jeśli chcesz otrzymać obiekt wiadomości jako `Result` Właściwość i mieć wartości zwracane jako właściwości dla tego obiektu, `/messageContract` Użyj opcji polecenia.</span><span class="sxs-lookup"><span data-stu-id="1e18b-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="1e18b-128">Spowoduje to wygenerowanie sygnatury zwracającej komunikat odpowiedzi jako `Result` Właściwość <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1e18b-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="1e18b-129">Wszystkie wewnętrzne wartości zwracane są następnie właściwościami obiektu komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1e18b-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="1e18b-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e18b-130">See also</span></span>

- [<span data-ttu-id="1e18b-131">Instrukcje: Implementowanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="1e18b-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
