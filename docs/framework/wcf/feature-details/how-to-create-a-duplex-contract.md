---
title: 'Instrukcje: Tworzenie kontraktu dwukierunkowego'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c06bd4f050eda3c3374684b5401b8c85fb9e1df9
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="e8146-102">Instrukcje: Tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="e8146-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="e8146-103">W tym temacie przedstawiono podstawowe kroki, aby utworzyć metody, które używają kontraktu dwukierunkowego (dwukierunkowe).</span><span class="sxs-lookup"><span data-stu-id="e8146-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="e8146-104">Kontrakt dupleksu umożliwia klienci i serwery komunikować się ze sobą niezależnie, aby albo mogą inicjować połączenia do drugiego.</span><span class="sxs-lookup"><span data-stu-id="e8146-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="e8146-105">Kontrakt dupleksu jest jednym z trzech komunikat dostępne [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="e8146-105">The duplex contract is one of three message patterns available to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="e8146-106">Inne dwóch komunikatów wzorce są jednokierunkowe i żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="e8146-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="e8146-107">Kontrakt dupleksowy składa się z dwóch jednokierunkowe kontraktów między klientem a serwerem i nie wymaga, aby zostać skorelowane wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="e8146-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="e8146-108">Użyj tego rodzaju kontraktu, jeśli usługa musi zapytań klienta, aby uzyskać więcej informacji, lub jawnie wywoływanie zdarzeń na kliencie.</span><span class="sxs-lookup"><span data-stu-id="e8146-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="e8146-109">Aby uzyskać więcej informacji na temat tworzenia aplikacji klienckiej dla kontraktu dwukierunkowego, zobacz [porady: dostęp do usług z kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="e8146-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="e8146-110">Dla przykładu pracy, zobacz [dupleksu](../../../../docs/framework/wcf/samples/duplex.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="e8146-110">For a working sample, see the [Duplex](../../../../docs/framework/wcf/samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="e8146-111">Aby utworzyć kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="e8146-111">To create a duplex contract</span></span>  
  
1.  <span data-ttu-id="e8146-112">Utwórz interfejs, który stanowi kontrakt dupleksu po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="e8146-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2.  <span data-ttu-id="e8146-113">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e8146-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3.  <span data-ttu-id="e8146-114">Deklarowanie podpisy metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e8146-114">Declare the method signatures in the interface.</span></span>  
  
4.  <span data-ttu-id="e8146-115">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody podpisie, który musi być część publicznego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e8146-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5.  <span data-ttu-id="e8146-116">Utwórz interfejs wywołania zwrotnego, który definiuje zestaw operacji, które może wywołać usługę na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="e8146-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6.  <span data-ttu-id="e8146-117">Deklarowanie sygnatury metody w interfejsie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e8146-117">Declare the method signatures in the callback interface.</span></span>  
  
7.  <span data-ttu-id="e8146-118">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody podpisie, który musi być część publicznego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e8146-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8.  <span data-ttu-id="e8146-119">Połącz dwa interfejsy do kontraktu dwukierunkowego przez ustawienie <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> właściwości w podstawowy interfejs do typu interfejsu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e8146-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="e8146-120">Wywoływanie metody na kliencie</span><span class="sxs-lookup"><span data-stu-id="e8146-120">To call methods on the client</span></span>  
  
1.  <span data-ttu-id="e8146-121">W implementacji usługi podstawowego kontraktu należy zadeklarować zmiennej dla interfejsu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e8146-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2.  <span data-ttu-id="e8146-122">Ustaw zmienną na odwołanie do obiektu zwrócony przez <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metody <xref:System.ServiceModel.OperationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="e8146-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3.  <span data-ttu-id="e8146-123">Wywołanie metody zdefiniowane przez interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e8146-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8146-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8146-124">Example</span></span>  
 <span data-ttu-id="e8146-125">Poniższy przykład kodu pokazuje komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="e8146-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="e8146-126">Kontrakt usługi zawiera działania usługi do przenoszenia do przodu i do tyłu.</span><span class="sxs-lookup"><span data-stu-id="e8146-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="e8146-127">Kontrakt klienta zawiera operacji usługi raportowania położenia.</span><span class="sxs-lookup"><span data-stu-id="e8146-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   <span data-ttu-id="e8146-128">Stosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybuty umożliwia automatyczne generowanie definicje kontraktu usługi w sieci Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="e8146-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
-   <span data-ttu-id="e8146-129">Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można pobrać dokument WSDL i kodu (opcjonalne) i konfigurację klienta.</span><span class="sxs-lookup"><span data-stu-id="e8146-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
-   <span data-ttu-id="e8146-130">Udostępnianie usługi dwukierunkowe punkty końcowe muszą być zabezpieczone.</span><span class="sxs-lookup"><span data-stu-id="e8146-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="e8146-131">Gdy usługa odbiera komunikat dupleksowy, analizuje ReplyTo w tej wiadomości przychodzących, aby określić, który ma zostać wysłana odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="e8146-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="e8146-132">Jeśli kanał nie jest zabezpieczony, niezaufanego klienta może wysłać komunikat złośliwego z ReplyTo na komputerze docelowym, co może prowadzić do odmowy usługi na docelowym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e8146-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="e8146-133">Z wiadomości regularne żądanie odpowiedź to nie jest problemem, ReplyTo jest ignorowany, ponieważ odpowiedź jest wysyłana w kanale, który pierwotny komunikat pochodzi w na.</span><span class="sxs-lookup"><span data-stu-id="e8146-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8146-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8146-134">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="e8146-135">Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="e8146-135">How to: Access Services with a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [<span data-ttu-id="e8146-136">Dupleks</span><span class="sxs-lookup"><span data-stu-id="e8146-136">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)  
 [<span data-ttu-id="e8146-137">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="e8146-137">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="e8146-138">Instrukcje: definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="e8146-138">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="e8146-139">Sesja</span><span class="sxs-lookup"><span data-stu-id="e8146-139">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)
