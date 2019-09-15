---
title: 'Instrukcje: wymiana zakolejkowanych komunikatów z punktami końcowymi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 09b21c9483b4f2716409b560dbbb478fe5a6badd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972221"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="738ac-102">Instrukcje: wymiana zakolejkowanych komunikatów z punktami końcowymi WCF</span><span class="sxs-lookup"><span data-stu-id="738ac-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="738ac-103">Kolejki zapewniają niezawodne komunikaty między klientem a usługą Windows Communication Foundation (WCF), nawet jeśli usługa nie jest dostępna w chwili komunikacji.</span><span class="sxs-lookup"><span data-stu-id="738ac-103">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="738ac-104">Poniższe procedury przedstawiają sposób zapewnienia trwałej komunikacji między klientem a usługą przy użyciu standardowego powiązania kolejkowanego w kolejce podczas implementowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="738ac-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="738ac-105">W tej sekcji wyjaśniono, <xref:System.ServiceModel.NetMsmqBinding> jak używać w kolejce komunikacji między klientem programu WCF a usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="738ac-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="738ac-106">Aby użyć kolejkowania w usłudze WCF</span><span class="sxs-lookup"><span data-stu-id="738ac-106">To use queuing in a WCF service</span></span>  
  
1. <span data-ttu-id="738ac-107">Zdefiniuj kontrakt usługi przy użyciu interfejsu oznaczonego za <xref:System.ServiceModel.ServiceContractAttribute>pomocą.</span><span class="sxs-lookup"><span data-stu-id="738ac-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="738ac-108">Oznacz operacje w interfejsie, który jest częścią kontraktu usługi z <xref:System.ServiceModel.OperationContractAttribute> i określ je jako jednokierunkowe, ponieważ nie jest zwracana żadna odpowiedź na metodę.</span><span class="sxs-lookup"><span data-stu-id="738ac-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="738ac-109">Poniższy kod zawiera przykładowy kontrakt usługi i jego definicję operacji.</span><span class="sxs-lookup"><span data-stu-id="738ac-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. <span data-ttu-id="738ac-110">Gdy kontrakt usługi przekazuje typy zdefiniowane przez użytkownika, należy zdefiniować Kontrakty danych dla tych typów.</span><span class="sxs-lookup"><span data-stu-id="738ac-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="738ac-111">Poniższy kod przedstawia dwa kontrakty `PurchaseOrder` danych i. `PurchaseOrderLineItem`</span><span class="sxs-lookup"><span data-stu-id="738ac-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="738ac-112">Te dwa typy definiują dane, które są wysyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="738ac-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="738ac-113">(Należy zauważyć, że klasy, które definiują ten kontrakt danych, również definiują wiele metod.</span><span class="sxs-lookup"><span data-stu-id="738ac-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="738ac-114">Te metody nie są uważane za część kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="738ac-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="738ac-115">Tylko te elementy członkowskie, które są zadeklarowane z <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutem, są częścią kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="738ac-115">Only those members that are declared with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. <span data-ttu-id="738ac-116">Zaimplementuj metody kontraktu usług zdefiniowanego w interfejsie w klasie.</span><span class="sxs-lookup"><span data-stu-id="738ac-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="738ac-117">Zwróć uwagę na `SubmitPurchaseOrder`umieszczeniemetody . <xref:System.ServiceModel.OperationBehaviorAttribute></span><span class="sxs-lookup"><span data-stu-id="738ac-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="738ac-118">Oznacza to, że ta operacja musi zostać wywołana w ramach transakcji i że transakcja zostanie automatycznie zakończona po zakończeniu metody.</span><span class="sxs-lookup"><span data-stu-id="738ac-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4. <span data-ttu-id="738ac-119">Utwórz kolejkę transakcyjną <xref:System.Messaging>przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="738ac-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="738ac-120">Zamiast tego można utworzyć kolejkę za pomocą programu Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="738ac-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="738ac-121">Jeśli tak, upewnij się, że tworzysz kolejkę transakcyjną.</span><span class="sxs-lookup"><span data-stu-id="738ac-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. <span data-ttu-id="738ac-122">Zdefiniuj w konfiguracji, która określa adres usługi i używa standardowego <xref:System.ServiceModel.NetMsmqBinding> powiązania. <xref:System.ServiceModel.Description.ServiceEndpoint></span><span class="sxs-lookup"><span data-stu-id="738ac-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="738ac-123">Aby uzyskać więcej informacji o korzystaniu z konfiguracji WCF, zobacz [Konfigurowanie usług WCF](../configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="738ac-123">For more information about using WCF configuration, see [Configuring WCF services](../configuring-services.md).</span></span>  

6. <span data-ttu-id="738ac-124">Utwórz hosta dla `OrderProcessing` usługi korzystającej z <xref:System.ServiceModel.ServiceHost> programu, która odczytuje komunikaty z kolejki i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="738ac-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="738ac-125">Otwórz hosta usługi, aby udostępnić usługę.</span><span class="sxs-lookup"><span data-stu-id="738ac-125">Open the service host to make the service available.</span></span> <span data-ttu-id="738ac-126">Wyświetl komunikat informujący użytkownika o naciśnięciu dowolnego klawisza w celu zakończenia usługi.</span><span class="sxs-lookup"><span data-stu-id="738ac-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="738ac-127">Wywołaj `ReadLine` , aby poczekać na naciśnięcie klawisza, a następnie zamknij usługę.</span><span class="sxs-lookup"><span data-stu-id="738ac-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="738ac-128">Aby utworzyć klienta dla usługi w kolejce</span><span class="sxs-lookup"><span data-stu-id="738ac-128">To create a client for the queued service</span></span>  
  
1. <span data-ttu-id="738ac-129">Poniższy przykład pokazuje, jak uruchomić aplikację hostingu i użyć narzędzia Svcutil. exe, aby utworzyć klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="738ac-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. <span data-ttu-id="738ac-130">Zdefiniuj w konfiguracji, która określa adres i używa standardowego <xref:System.ServiceModel.NetMsmqBinding> powiązania, jak pokazano w poniższym przykładzie. <xref:System.ServiceModel.Description.ServiceEndpoint></span><span class="sxs-lookup"><span data-stu-id="738ac-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  

3. <span data-ttu-id="738ac-131">Utwórz zakres transakcji do zapisu w kolejce transakcyjnej, wywołaj `SubmitPurchaseOrder` operację i Zamknij klienta WCF, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="738ac-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="738ac-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="738ac-132">Example</span></span>  
 <span data-ttu-id="738ac-133">Poniższe przykłady przedstawiają kod usługi, aplikację hostingu, plik App. config oraz kod klienta uwzględniony w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="738ac-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a><span data-ttu-id="738ac-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="738ac-134">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- [<span data-ttu-id="738ac-135">Transakcyjne powiązanie MSMQ</span><span class="sxs-lookup"><span data-stu-id="738ac-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)
- [<span data-ttu-id="738ac-136">Tworzenie kolejek w programie WCF</span><span class="sxs-lookup"><span data-stu-id="738ac-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="738ac-137">Instrukcje: Wymiana komunikatów z punktami końcowymi WCF i aplikacjami usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="738ac-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="738ac-138">Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="738ac-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="738ac-139">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="738ac-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="738ac-140">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="738ac-140">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="738ac-141">Zabezpieczenia komunikatów w ramach kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="738ac-141">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
