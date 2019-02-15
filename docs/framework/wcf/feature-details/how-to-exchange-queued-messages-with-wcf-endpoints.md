---
title: 'Instrukcje: Wymiana zakolejkowanych komunikatów z punktami końcowymi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 11435dc6f941a566427c0e0cb797e84f33dd66a2
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303650"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="3b098-102">Instrukcje: Wymiana zakolejkowanych komunikatów z punktami końcowymi WCF</span><span class="sxs-lookup"><span data-stu-id="3b098-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="3b098-103">Kolejki upewnij się, że niezawodna obsługa komunikatów może wystąpić między klientem a usługą Windows Communication Foundation (WCF), nawet jeśli usługa nie jest dostępna w czasie komunikacji.</span><span class="sxs-lookup"><span data-stu-id="3b098-103">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="3b098-104">Poniższe procedury pokazują, jak zapewnić niezawodne komunikacji między klientem a usługą przy użyciu standardu w kolejce wiążące podczas implementowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3b098-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="3b098-105">W tej sekcji wyjaśniono, jak używać <xref:System.ServiceModel.NetMsmqBinding> umieszczonych w kolejce komunikacji między klienta programu WCF i usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3b098-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="3b098-106">Aby użyć usługi kolejkowania wiadomości w usłudze WCF</span><span class="sxs-lookup"><span data-stu-id="3b098-106">To use queuing in a WCF service</span></span>  
  
1.  <span data-ttu-id="3b098-107">Definiowanie kontraktu usługi przy użyciu interfejsu oznaczone <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3b098-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="3b098-108">Oznacz operacji w interfejsie, które są częścią kontraktu usługi o <xref:System.ServiceModel.OperationContractAttribute> i określ je jako jednokierunkowe, ponieważ zwracany jest brak odpowiedzi do metody.</span><span class="sxs-lookup"><span data-stu-id="3b098-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="3b098-109">Poniższy kod stanowi przykład kontrakt usługi i jego definicję operacji.</span><span class="sxs-lookup"><span data-stu-id="3b098-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  <span data-ttu-id="3b098-110">Gdy kontrakt usługi przekazuje typy zdefiniowane przez użytkownika, należy zdefiniować kontraktów danych do tych typów.</span><span class="sxs-lookup"><span data-stu-id="3b098-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="3b098-111">W poniższym kodzie pokazano dwa kontraktów danych `PurchaseOrder` i `PurchaseOrderLineItem`.</span><span class="sxs-lookup"><span data-stu-id="3b098-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="3b098-112">Tych dwóch typów zdefiniować dane, które są wysyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="3b098-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="3b098-113">(Zwróć uwagę, że klasy, które definiują ten kontrakt danych również zdefiniować na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="3b098-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="3b098-114">Te metody nie są uważane za część kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="3b098-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="3b098-115">Tylko te elementy członkowskie, które są zadeklarowane za pomocą `DataMember` atrybutu są częścią kontraktu danych.)</span><span class="sxs-lookup"><span data-stu-id="3b098-115">Only those members that are declared with the `DataMember` attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  <span data-ttu-id="3b098-116">Implementuje metody zdefiniowane w interfejsie w klasie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="3b098-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="3b098-117">Zwróć uwagę <xref:System.ServiceModel.OperationBehaviorAttribute> umieszczone na `SubmitPurchaseOrder` metody.</span><span class="sxs-lookup"><span data-stu-id="3b098-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="3b098-118">Określa, że ta operacja musi zostać wywołana w transakcji i że transakcja automatycznie kończy się po zakończeniu działania metody.</span><span class="sxs-lookup"><span data-stu-id="3b098-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4.  <span data-ttu-id="3b098-119">Utwórz kolejkę transakcyjną za pomocą <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="3b098-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="3b098-120">Można utworzyć kolejkę, zamiast Microsoft usługi kolejkowania komunikatów (MSMQ) programu Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="3b098-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="3b098-121">Jeśli tak, upewnij się, że można utworzyć kolejkę transakcyjną.</span><span class="sxs-lookup"><span data-stu-id="3b098-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  <span data-ttu-id="3b098-122">Zdefiniuj <xref:System.ServiceModel.Description.ServiceEndpoint> w konfiguracji, który określa adres usługi i używa standardu <xref:System.ServiceModel.NetMsmqBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="3b098-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="3b098-123">Aby uzyskać więcej informacji na temat korzystania z konfiguracji usługi WCF, zobacz [usług WCF Konfigurowanie](../configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="3b098-123">For more information about using WCF configuration, see [Configuring WCF services](../configuring-services.md).</span></span>  
  
  
  
6.  <span data-ttu-id="3b098-124">Tworzenie hosta dla `OrderProcessing` usługi przy użyciu <xref:System.ServiceModel.ServiceHost> która odczytuje komunikaty z kolejki i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="3b098-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="3b098-125">Otwórz hosta usługi, aby udostępnić usługę.</span><span class="sxs-lookup"><span data-stu-id="3b098-125">Open the service host to make the service available.</span></span> <span data-ttu-id="3b098-126">Wyświetlenie komunikatu, informujący użytkownika, naciśnij dowolny klawisz, aby zakończyć usługi.</span><span class="sxs-lookup"><span data-stu-id="3b098-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="3b098-127">Wywołaj `ReadLine` oczekiwania klawisz, aby zostać naciśnięte, a następnie Zamknij usługę.</span><span class="sxs-lookup"><span data-stu-id="3b098-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="3b098-128">Można utworzyć klienta dla usługi w kolejce</span><span class="sxs-lookup"><span data-stu-id="3b098-128">To create a client for the queued service</span></span>  
  
1.  <span data-ttu-id="3b098-129">Poniższy przykład pokazuje, jak do uruchamiania aplikacji macierzystej, a za pomocą narzędzia Svcutil.exe, aby utworzyć klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="3b098-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  <span data-ttu-id="3b098-130">Zdefiniuj <xref:System.ServiceModel.Description.ServiceEndpoint> w konfiguracji, który określa adres i używa standardowych <xref:System.ServiceModel.NetMsmqBinding> powiązania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3b098-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  
  
  
  
3.  <span data-ttu-id="3b098-131">Tworzenie zakresu transakcji do zapisu do kolejki transakcyjne, wywołanie `SubmitPurchaseOrder` operacji, a następnie Zamknij klienta WCF, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3b098-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="3b098-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b098-132">Example</span></span>  
 <span data-ttu-id="3b098-133">W poniższych przykładach pokazano kod usługi, aplikacji macierzystej, plik App.config i kod klienta zawarte w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3b098-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="3b098-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b098-134">See also</span></span>
- <xref:System.ServiceModel.NetMsmqBinding>
- [<span data-ttu-id="3b098-135">Transakcyjne powiązanie MSMQ</span><span class="sxs-lookup"><span data-stu-id="3b098-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)
- [<span data-ttu-id="3b098-136">Tworzenie kolejek w programie WCF</span><span class="sxs-lookup"><span data-stu-id="3b098-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="3b098-137">Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="3b098-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="3b098-138">Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="3b098-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="3b098-139">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="3b098-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="3b098-140">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3b098-140">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="3b098-141">Zabezpieczenia komunikatów w ramach kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="3b098-141">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
