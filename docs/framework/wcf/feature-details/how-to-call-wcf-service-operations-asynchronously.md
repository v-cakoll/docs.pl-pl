---
title: 'Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 5eae08ab6b8dee5ebece66a1c41c87ebab3387bc
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963277"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="1a6f4-102">Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF</span><span class="sxs-lookup"><span data-stu-id="1a6f4-102">How to: Call WCF Service Operations Asynchronously</span></span>

<span data-ttu-id="1a6f4-103">W tym artykule opisano, jak klient może asynchronicznie uzyskać dostęp do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-103">This article covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="1a6f4-104">Usługa w tym artykule implementuje interfejs `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-104">The service in this article implements the `ICalculator` interface.</span></span> <span data-ttu-id="1a6f4-105">Klient może wywoływać operacje w tym interfejsie asynchronicznie przy użyciu opartego na zdarzeniach asynchronicznego modelu wywoływania.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="1a6f4-106">(Aby uzyskać więcej informacji o asynchronicznym modelu wywoływania opartych na zdarzeniach, zobacz [programowanie wielowątkowe ze wzorcem asynchronicznym opartym na zdarzeniach](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span><span class="sxs-lookup"><span data-stu-id="1a6f4-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span></span> <span data-ttu-id="1a6f4-107">Aby zapoznać się z przykładem, który pokazuje, jak zaimplementować operację asynchronicznie w usłudze, zobacz [How to: implementowanie asynchronicznej operacji usługi](../how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="1a6f4-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="1a6f4-108">Aby uzyskać więcej informacji na temat operacji synchronicznych i asynchronicznych, zobacz [Operacje synchroniczne i asynchroniczne](../synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="1a6f4-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a6f4-109">Asynchroniczny model wywoływania oparty na zdarzeniach nie jest obsługiwany w przypadku używania <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="1a6f4-110">Aby uzyskać informacje na temat wykonywania wywołań asynchronicznych przy użyciu <xref:System.ServiceModel.ChannelFactory%601>, zobacz [How to: Call operacje asynchronicznie przy użyciu fabryki kanałów](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="1a6f4-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="1a6f4-111">Procedura</span><span class="sxs-lookup"><span data-stu-id="1a6f4-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="1a6f4-112">Aby asynchronicznie wywoływać operacje usługi WCF</span><span class="sxs-lookup"><span data-stu-id="1a6f4-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="1a6f4-113">Uruchom narzędzie do [przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z opcjami `/async` i `/tcv:Version35` polecenia, jak pokazano w poniższym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="1a6f4-114">Spowoduje to wygenerowanie, oprócz synchronicznych i standardowych operacji asynchronicznych opartych na delegatach, klasy klienta WCF, która zawiera:</span><span class="sxs-lookup"><span data-stu-id="1a6f4-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="1a6f4-115">Dwie <`operationName`>`Async` operacji do użycia z podejściem wywołań asynchronicznych opartych na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="1a6f4-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1a6f4-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="1a6f4-117">Zdarzenia ukończone w formularzu <`operationName`>`Completed` do użycia z podejściem wywołań asynchronicznych opartych na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="1a6f4-118">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1a6f4-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="1a6f4-119"><xref:System.EventArgs?displayProperty=nameWithType> typy dla każdej operacji (formularza <`operationName`>`CompletedEventArgs`) do użycia z podejście asynchroniczne wywołań asynchronicznych opartych na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="1a6f4-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1a6f4-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="1a6f4-121">W aplikacji wywołującej Utwórz metodę wywołania zwrotnego, która ma być wywoływana po zakończeniu operacji asynchronicznej, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="1a6f4-122">Przed wywołaniem operacji Użyj nowej generycznej <xref:System.EventHandler%601?displayProperty=nameWithType> typu <`operationName`>`EventArgs`, aby dodać metodę obsługi (utworzoną w poprzednim kroku) do <`operationName`>zdarzenia `Completed`.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="1a6f4-123">Następnie Wywołaj metodę <`operationName`>`Async`.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="1a6f4-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1a6f4-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="1a6f4-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a6f4-125">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a6f4-126">Wskazówki dotyczące projektowania dla asynchronicznego stanu modelu opartego na zdarzeniach, które w przypadku zwrócenia więcej niż jednej wartości są zwracane jako właściwość `Result`, a pozostałe są zwracane jako właściwości w obiekcie <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="1a6f4-127">Wynikiem tego jest to, że jeśli klient Importuje metadane przy użyciu opcji poleceń asynchronicznych opartych na zdarzeniach, a operacja zwraca więcej niż jedną wartość, domyślny obiekt <xref:System.EventArgs> zwraca jedną wartość jako właściwość `Result`, a pozostała część to właściwości obiektu <xref:System.EventArgs>. Jeśli chcesz otrzymać obiekt komunikatu jako właściwość `Result` i mieć wartości zwracanych jako właściwości dla tego obiektu, użyj opcji polecenie `/messageContract`.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="1a6f4-128">Spowoduje to wygenerowanie sygnatury zwracającej komunikat odpowiedzi jako właściwości `Result` w obiekcie <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="1a6f4-129">Wszystkie wewnętrzne wartości zwracane są następnie właściwościami obiektu komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="1a6f4-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a6f4-130">See also</span></span>

- [<span data-ttu-id="1a6f4-131">Instrukcje: wdrażanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="1a6f4-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
