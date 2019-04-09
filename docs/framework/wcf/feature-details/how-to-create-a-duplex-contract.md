---
title: 'Instrukcje: tworzenie kontraktu dwukierunkowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: 002c94f2cb69e330e8d2796a9f93d977b10f53f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078177"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="8f57a-102">Instrukcje: tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="8f57a-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="8f57a-103">W tym temacie przedstawiono podstawowe kroki, aby utworzyć metody, które używają kontraktu dwukierunkowego (dwukierunkowe).</span><span class="sxs-lookup"><span data-stu-id="8f57a-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="8f57a-104">Kontrakt dupleksowy umożliwia klientów i serwerów komunikować się ze sobą niezależnie, aby albo może zainicjować wywołania do drugiego.</span><span class="sxs-lookup"><span data-stu-id="8f57a-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="8f57a-105">Kontraktu dwukierunkowego jest jednym z trzech wzorców komunikat dostępne dla usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8f57a-105">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="8f57a-106">Komunikat innych dwa wzorce są jednokierunkowe, a "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="8f57a-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="8f57a-107">Kontrakt dupleksowy składa się z dwóch jednokierunkowe umów między klientem a serwerem i nie wymaga, aby zostać skorelowane wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="8f57a-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="8f57a-108">Należy użyć tego rodzaju kontraktu, podczas usługi musi zapytania klienta, aby uzyskać więcej informacji lub jawnie wywoływać zdarzenia, na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="8f57a-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="8f57a-109">Aby uzyskać więcej informacji na temat tworzenia aplikacji klienckiej kontrakt dupleksowy, zobacz [jak: Uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="8f57a-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="8f57a-110">Przykładowy pracy [dwukierunkowego](../../../../docs/framework/wcf/samples/duplex.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="8f57a-110">For a working sample, see the [Duplex](../../../../docs/framework/wcf/samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="8f57a-111">Tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="8f57a-111">To create a duplex contract</span></span>  
  
1.  <span data-ttu-id="8f57a-112">Utwórz interfejs, tworzącą kontraktu dwukierunkowego po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="8f57a-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2.  <span data-ttu-id="8f57a-113">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8f57a-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3.  <span data-ttu-id="8f57a-114">Zadeklaruj podpisy metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8f57a-114">Declare the method signatures in the interface.</span></span>  
  
4.  <span data-ttu-id="8f57a-115">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy, aby każdy podpis metody, który musi być częścią publicznego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8f57a-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5.  <span data-ttu-id="8f57a-116">Utwórz interfejs wywołania zwrotnego, który definiuje zestaw operacji, które można wywołać usługę na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="8f57a-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6.  <span data-ttu-id="8f57a-117">Zadeklaruj podpisy metod w interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8f57a-117">Declare the method signatures in the callback interface.</span></span>  
  
7.  <span data-ttu-id="8f57a-118">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy, aby każdy podpis metody, który musi być częścią publicznego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8f57a-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8.  <span data-ttu-id="8f57a-119">Łączenie dwóch interfejsów w kontrakt dupleksowy, ustawiając <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> właściwość podstawowy interfejs do typu interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8f57a-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="8f57a-120">Wywoływanie metod na komputerze klienckim</span><span class="sxs-lookup"><span data-stu-id="8f57a-120">To call methods on the client</span></span>  
  
1.  <span data-ttu-id="8f57a-121">W implementacji usługi podstawowego kontraktu należy zadeklarować zmienną interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8f57a-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2.  <span data-ttu-id="8f57a-122">Ustaw zmienną na zwracane przez odwołanie do obiektu <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metody <xref:System.ServiceModel.OperationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="8f57a-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3.  <span data-ttu-id="8f57a-123">Wywołanie metody zdefiniowane przez interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8f57a-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f57a-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f57a-124">Example</span></span>  
 <span data-ttu-id="8f57a-125">Poniższy przykład kodu demonstruje komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="8f57a-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="8f57a-126">Kontrakt usługi zawiera operacje usługi do przenoszenia do przodu i do tyłu.</span><span class="sxs-lookup"><span data-stu-id="8f57a-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="8f57a-127">Umowy klienta zawiera operacji usługi raportowania położenia.</span><span class="sxs-lookup"><span data-stu-id="8f57a-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   <span data-ttu-id="8f57a-128">Stosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybuty umożliwia automatyczne generowanie definicje kontraktu usługi w sieci Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="8f57a-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
-   <span data-ttu-id="8f57a-129">Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do pobrania dokumentu WSDL i (opcjonalnie) kod i konfiguracja dla klientów.</span><span class="sxs-lookup"><span data-stu-id="8f57a-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
-   <span data-ttu-id="8f57a-130">Udostępnianie usługi dwukierunkowe punkty końcowe muszą być zabezpieczone.</span><span class="sxs-lookup"><span data-stu-id="8f57a-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="8f57a-131">Gdy usługa odbiera komunikat dwukierunkowego, analizuje ReplyTo w tej wiadomości przychodzących, aby określić, gdzie wysyłać odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8f57a-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="8f57a-132">Jeśli kanał nie jest zabezpieczony, niezaufanego klienta można wysyłanie wiadomości złośliwego z ReplyTo maszynę docelową, co prowadzi do typu "odmowa usługi maszyny docelowej".</span><span class="sxs-lookup"><span data-stu-id="8f57a-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="8f57a-133">Przy użyciu komunikatów regularne "żądanie-odpowiedź" to nie jest problemem, ponieważ ReplyTo jest ignorowana, a odpowiedź jest wysyłana na kanale, który oryginalnego komunikatu materiał na.</span><span class="sxs-lookup"><span data-stu-id="8f57a-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f57a-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f57a-134">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="8f57a-135">Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="8f57a-135">How to: Access Services with a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="8f57a-136">Dupleks</span><span class="sxs-lookup"><span data-stu-id="8f57a-136">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)
- [<span data-ttu-id="8f57a-137">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="8f57a-137">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="8f57a-138">Instrukcje: Definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="8f57a-138">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="8f57a-139">Sesja</span><span class="sxs-lookup"><span data-stu-id="8f57a-139">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)
