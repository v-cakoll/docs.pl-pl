---
title: 'Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 400ed8e5ee8b236e9d0f843f27b7c2112ec28861
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601260"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="19e7e-102">Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF</span><span class="sxs-lookup"><span data-stu-id="19e7e-102">How to: Call WCF Service Operations Asynchronously</span></span>

<span data-ttu-id="19e7e-103">W tym artykule opisano, jak klient może asynchronicznie uzyskać dostęp do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="19e7e-103">This article covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="19e7e-104">Usługa w tym artykule implementuje `ICalculator` interfejs.</span><span class="sxs-lookup"><span data-stu-id="19e7e-104">The service in this article implements the `ICalculator` interface.</span></span> <span data-ttu-id="19e7e-105">Klient może wywoływać operacje w tym interfejsie asynchronicznie przy użyciu opartego na zdarzeniach asynchronicznego modelu wywoływania.</span><span class="sxs-lookup"><span data-stu-id="19e7e-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="19e7e-106">(Aby uzyskać więcej informacji o asynchronicznym modelu wywoływania opartych na zdarzeniach, zobacz [programowanie wielowątkowe ze wzorcem asynchronicznym opartym na zdarzeniach](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span><span class="sxs-lookup"><span data-stu-id="19e7e-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span></span> <span data-ttu-id="19e7e-107">Aby zapoznać się z przykładem, który pokazuje, jak zaimplementować operację asynchronicznie w usłudze, zobacz [How to: implementowanie asynchronicznej operacji usługi](../how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="19e7e-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="19e7e-108">Aby uzyskać więcej informacji na temat operacji synchronicznych i asynchronicznych, zobacz [Operacje synchroniczne i asynchroniczne](../synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="19e7e-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19e7e-109">Asynchroniczny model wywoływania oparty na zdarzeniach nie jest obsługiwany w przypadku korzystania z programu <xref:System.ServiceModel.ChannelFactory%601> .</span><span class="sxs-lookup"><span data-stu-id="19e7e-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="19e7e-110">Aby uzyskać informacje na temat wykonywania wywołań asynchronicznych przy użyciu <xref:System.ServiceModel.ChannelFactory%601> , zobacz [How to: Call operacje asynchronicznie przy użyciu fabryki kanałów](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="19e7e-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="19e7e-111">Procedura</span><span class="sxs-lookup"><span data-stu-id="19e7e-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="19e7e-112">Aby asynchronicznie wywoływać operacje usługi WCF</span><span class="sxs-lookup"><span data-stu-id="19e7e-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="19e7e-113">Uruchom narzędzie do [przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) za pomocą obu `/async` `/tcv:Version35` opcji poleceń i, jak pokazano w poniższym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="19e7e-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="19e7e-114">Spowoduje to wygenerowanie, oprócz synchronicznych i standardowych operacji asynchronicznych opartych na delegatach, klasy klienta WCF, która zawiera:</span><span class="sxs-lookup"><span data-stu-id="19e7e-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="19e7e-115">Dwie <`operationName` > `Async` operacji do użycia z podejściem asynchronicznym wywołującym zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19e7e-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="19e7e-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="19e7e-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="19e7e-117">Zdarzenia ukończone w formularzu <`operationName` > `Completed` do użycia z podejściem asynchronicznym wywołującym zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19e7e-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="19e7e-118">Przykład:</span><span class="sxs-lookup"><span data-stu-id="19e7e-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="19e7e-119"><xref:System.EventArgs?displayProperty=nameWithType>typy dla każdej operacji (formularza <`operationName` > `CompletedEventArgs` ) do użycia z podejściem asynchronicznym wywołującym zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19e7e-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="19e7e-120">Przykład:</span><span class="sxs-lookup"><span data-stu-id="19e7e-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="19e7e-121">W aplikacji wywołującej Utwórz metodę wywołania zwrotnego, która ma być wywoływana po zakończeniu operacji asynchronicznej, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="19e7e-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="19e7e-122">Przed wywołaniem operacji należy użyć nowego <xref:System.EventHandler%601?displayProperty=nameWithType> typu ogólnego <, `operationName` > `EventArgs` Aby dodać metodę procedury obsługi (utworzoną w poprzednim kroku) do `operationName` > `Completed` zdarzenia <.</span><span class="sxs-lookup"><span data-stu-id="19e7e-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="19e7e-123">Następnie Wywołaj `operationName` > `Async` metodę <.</span><span class="sxs-lookup"><span data-stu-id="19e7e-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="19e7e-124">Przykład:</span><span class="sxs-lookup"><span data-stu-id="19e7e-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="19e7e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="19e7e-125">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19e7e-126">Wskazówki dotyczące projektowania dla asynchronicznego stanu modelu opartego na zdarzeniach, które w przypadku zwrócenia więcej niż jednej wartości, jedna wartość jest zwracana jako `Result` Właściwość, a pozostałe są zwracane jako właściwości w <xref:System.EventArgs> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="19e7e-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="19e7e-127">W związku z tym, jeśli klient Importuje metadane przy użyciu opcji poleceń asynchronicznych opartych na zdarzeniach, a operacja zwraca więcej niż jedną wartość, <xref:System.EventArgs> obiekt domyślny zwraca jedną wartość jako `Result` Właściwość, a reszta jest właściwościami <xref:System.EventArgs> obiektu. Jeśli chcesz otrzymać obiekt wiadomości jako `Result` Właściwość i mieć wartości zwracane jako właściwości dla tego obiektu, użyj `/messageContract` opcji polecenia.</span><span class="sxs-lookup"><span data-stu-id="19e7e-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="19e7e-128">Spowoduje to wygenerowanie sygnatury zwracającej komunikat odpowiedzi jako `Result` Właściwość <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="19e7e-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="19e7e-129">Wszystkie wewnętrzne wartości zwracane są następnie właściwościami obiektu komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="19e7e-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="19e7e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19e7e-130">See also</span></span>

- [<span data-ttu-id="19e7e-131">Instrukcje: wdrażanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="19e7e-131">How to: Implement an Asynchronous Service Operation</span></span>](../how-to-implement-an-asynchronous-service-operation.md)
