---
title: "Instrukcje: Wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF"
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
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba057a0b96d393a5efbaf054e75c34f446c7dde6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="93cc8-102">Instrukcje: Wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF</span><span class="sxs-lookup"><span data-stu-id="93cc8-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="93cc8-103">Kolejki upewnij się, że niezawodna obsługa komunikatów może wystąpić między klientem a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi, nawet jeśli usługa nie jest dostępna w tym czasie komunikacji.</span><span class="sxs-lookup"><span data-stu-id="93cc8-103">Queues ensure that reliable messaging can occur between a client and a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="93cc8-104">Poniższe procedury pokazują, jak zapewnić niezawodna komunikacja między klientem a usługą przy użyciu standardu w kolejce powiązania podczas implementowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="93cc8-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="93cc8-105">W tej sekcji opisano sposób korzystania <xref:System.ServiceModel.NetMsmqBinding> umieszczonych w kolejce komunikacji między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="93cc8-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="93cc8-106">Aby użyć usługi kolejkowania wiadomości usługi WCF</span><span class="sxs-lookup"><span data-stu-id="93cc8-106">To use queuing in a WCF service</span></span>  
  
1.  <span data-ttu-id="93cc8-107">Definiowanie kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="93cc8-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="93cc8-108">Oznacz operacje w interfejsie, które są częścią kontraktu usługi o <xref:System.ServiceModel.OperationContractAttribute> i określ je jako jednokierunkowe, ponieważ żadna odpowiedź do metody.</span><span class="sxs-lookup"><span data-stu-id="93cc8-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="93cc8-109">Następujący kod stanowi przykład kontrakt usługi i jego definicji operacji.</span><span class="sxs-lookup"><span data-stu-id="93cc8-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  <span data-ttu-id="93cc8-110">Gdy kontrakt usługi przekazuje typy danych zdefiniowane przez użytkownika, należy zdefiniować kontraktów danych dla tych typów.</span><span class="sxs-lookup"><span data-stu-id="93cc8-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="93cc8-111">Poniższy kod przedstawia dwa kontrakty danych, `PurchaseOrder` i `PurchaseOrderLineItem`.</span><span class="sxs-lookup"><span data-stu-id="93cc8-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="93cc8-112">Te dwa typy zdefiniować dane są przesyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="93cc8-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="93cc8-113">(Należy pamiętać, klasy, które definiują tego kontraktu danych będzie także zdefiniować na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="93cc8-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="93cc8-114">Te metody nie są traktowane jako część kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="93cc8-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="93cc8-115">Tylko te elementy członkowskie, które są zadeklarowane z `DataMember` atrybut jest częścią kontraktu danych.)</span><span class="sxs-lookup"><span data-stu-id="93cc8-115">Only those members that are declared with the `DataMember` attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  <span data-ttu-id="93cc8-116">Implementuje metody zdefiniowane w interfejsie klasa kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="93cc8-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="93cc8-117">Powiadomienie <xref:System.ServiceModel.OperationBehaviorAttribute> dotyczącymi `SubmitPurchaseOrder` metody.</span><span class="sxs-lookup"><span data-stu-id="93cc8-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="93cc8-118">Określa, czy ta operacja musi zostać wywołana w transakcji i że transakcji automatycznie działanie jest kończone po zakończeniu metody.</span><span class="sxs-lookup"><span data-stu-id="93cc8-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4.  <span data-ttu-id="93cc8-119">Tworzenie kolejki transakcyjnej przy użyciu <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="93cc8-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="93cc8-120">Można utworzyć kolejkę, zamiast niego Usługa kolejkowania wiadomości firmy Microsoft (MSMQ) programu Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="93cc8-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="93cc8-121">Jeśli tak, upewnij się, że tworzenie kolejką transakcyjną.</span><span class="sxs-lookup"><span data-stu-id="93cc8-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  <span data-ttu-id="93cc8-122">Zdefiniuj <xref:System.ServiceModel.Description.ServiceEndpoint> w konfiguracji, który określa adres usługi i korzysta ze standardu <xref:System.ServiceModel.NetMsmqBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="93cc8-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="93cc8-123">przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfiguracji, zobacz [Konfigurowanie aplikacji systemu Windows Communication Foundation](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="93cc8-123"> using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration, see [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
  
  
6.  <span data-ttu-id="93cc8-124">Utwórz hosta dla `OrderProcessing` usługi przy użyciu <xref:System.ServiceModel.ServiceHost> które odczytuje wiadomości z kolejki i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="93cc8-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="93cc8-125">Otworzyć hosta usługi, aby udostępnić usługę.</span><span class="sxs-lookup"><span data-stu-id="93cc8-125">Open the service host to make the service available.</span></span> <span data-ttu-id="93cc8-126">Wyświetla komunikat informujący o użytkownikowi naciśnij dowolny klawisz, aby zakończyć usługi.</span><span class="sxs-lookup"><span data-stu-id="93cc8-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="93cc8-127">Wywołanie `ReadLine` oczekiwania klawisz, aby zostać naciśnięte, a następnie Zamknij usługę.</span><span class="sxs-lookup"><span data-stu-id="93cc8-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="93cc8-128">Aby utworzyć klienta usługi kolejki</span><span class="sxs-lookup"><span data-stu-id="93cc8-128">To create a client for the queued service</span></span>  
  
1.  <span data-ttu-id="93cc8-129">Poniższy przykład przedstawia sposób uruchomienia hostingu aplikacji i korzystać z narzędzia Svcutil.exe do utworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="93cc8-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  <span data-ttu-id="93cc8-130">Zdefiniuj <xref:System.ServiceModel.Description.ServiceEndpoint> w konfiguracji, który określa adres i korzysta ze standardu <xref:System.ServiceModel.NetMsmqBinding> powiązanie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="93cc8-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  
  
  
  
3.  <span data-ttu-id="93cc8-131">Tworzenie zakresu transakcji można zapisać do kolejki transakcyjnej wywołania `SubmitPurchaseOrder` operacji, a następnie Zamknij [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="93cc8-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="93cc8-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="93cc8-132">Example</span></span>  
 <span data-ttu-id="93cc8-133">W poniższych przykładach pokazano kod usługi hostingu aplikacji, plik App.config i zawarte w tym przykładzie kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="93cc8-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="93cc8-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93cc8-134">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [<span data-ttu-id="93cc8-135">Transakcyjne powiązanie MSMQ</span><span class="sxs-lookup"><span data-stu-id="93cc8-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [<span data-ttu-id="93cc8-136">Tworzenie kolejek w programie WCF</span><span class="sxs-lookup"><span data-stu-id="93cc8-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="93cc8-137">Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="93cc8-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="93cc8-138">Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="93cc8-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="93cc8-139">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="93cc8-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="93cc8-140">Przykłady powiązanie integracji usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="93cc8-140">Message Queuing Integration Binding Samples</span></span>](http://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [<span data-ttu-id="93cc8-141">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="93cc8-141">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="93cc8-142">Zabezpieczenia komunikatów w ramach kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="93cc8-142">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
