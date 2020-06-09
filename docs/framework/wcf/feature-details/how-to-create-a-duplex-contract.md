---
title: 'Instrukcje: Tworzenie kontraktu dwukierunkowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: e5b6c7eecce08a23490b6ab1991e4561d9462469
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598986"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="b3c04-102">Instrukcje: Tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="b3c04-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="b3c04-103">W tym temacie przedstawiono podstawowe kroki tworzenia metod, które korzystają z dwukierunkowego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b3c04-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="b3c04-104">Umowa dupleksowa umożliwia klientom i serwerom komunikowanie się ze sobą niezależnie, aby można było inicjować wywołania do drugiego.</span><span class="sxs-lookup"><span data-stu-id="b3c04-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="b3c04-105">Umowa dupleksowa to jeden z trzech wzorców komunikatów dostępnych dla usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b3c04-105">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="b3c04-106">Pozostałe dwa wzorce komunikatów to jednokierunkowe i odpowiedzi na żądanie.</span><span class="sxs-lookup"><span data-stu-id="b3c04-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="b3c04-107">Umowa dupleksowa składa się z 2 1ych umów między klientem a serwerem i nie wymaga, aby wywołania metod były skorelowane.</span><span class="sxs-lookup"><span data-stu-id="b3c04-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="b3c04-108">Tego rodzaju kontraktu należy używać, gdy usługa musi wysyłać zapytania do klienta, aby uzyskać więcej informacji lub jawnie podnieść zdarzenia na kliencie.</span><span class="sxs-lookup"><span data-stu-id="b3c04-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="b3c04-109">Aby uzyskać więcej informacji na temat tworzenia aplikacji klienckiej dla kontraktu dupleksowego, zobacz [jak: dostęp do usług za pomocą kontraktu dupleksowego](how-to-access-services-with-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b3c04-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="b3c04-110">Aby uzyskać przykład roboczy, zobacz [dwustronny](../samples/duplex.md) przykład.</span><span class="sxs-lookup"><span data-stu-id="b3c04-110">For a working sample, see the [Duplex](../samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="b3c04-111">Aby utworzyć umowę dupleksową</span><span class="sxs-lookup"><span data-stu-id="b3c04-111">To create a duplex contract</span></span>  
  
1. <span data-ttu-id="b3c04-112">Utwórz interfejs, który tworzy stronę po stronie serwera umowy dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="b3c04-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2. <span data-ttu-id="b3c04-113">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasę do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b3c04-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. <span data-ttu-id="b3c04-114">Zadeklaruj sygnatury metod w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="b3c04-114">Declare the method signatures in the interface.</span></span>  
  
4. <span data-ttu-id="b3c04-115">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do sygnatury każdej metody, która musi być częścią kontraktu publicznego.</span><span class="sxs-lookup"><span data-stu-id="b3c04-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5. <span data-ttu-id="b3c04-116">Utwórz interfejs wywołania zwrotnego, który definiuje zestaw operacji, które usługa może wywoływać na kliencie.</span><span class="sxs-lookup"><span data-stu-id="b3c04-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. <span data-ttu-id="b3c04-117">Zadeklaruj sygnatury metod w interfejsie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3c04-117">Declare the method signatures in the callback interface.</span></span>  
  
7. <span data-ttu-id="b3c04-118">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do sygnatury każdej metody, która musi być częścią kontraktu publicznego.</span><span class="sxs-lookup"><span data-stu-id="b3c04-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8. <span data-ttu-id="b3c04-119">Połącz dwa interfejsy z umową dupleksową, ustawiając <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> Właściwość w interfejsie podstawowym na typ interfejsu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3c04-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="b3c04-120">Aby wywołać metody na kliencie</span><span class="sxs-lookup"><span data-stu-id="b3c04-120">To call methods on the client</span></span>  
  
1. <span data-ttu-id="b3c04-121">W implementacji usługi głównej kontraktu Zadeklaruj zmienną dla interfejsu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3c04-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2. <span data-ttu-id="b3c04-122">Ustaw zmienną na odwołanie do obiektu zwrócone przez <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metodę <xref:System.ServiceModel.OperationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="b3c04-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. <span data-ttu-id="b3c04-123">Wywołaj metody zdefiniowane przez interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3c04-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3c04-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3c04-124">Example</span></span>  
 <span data-ttu-id="b3c04-125">Poniższy przykład kodu ilustruje komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="b3c04-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="b3c04-126">Kontrakt usługi zawiera operacje usługi do przeniesienia do przodu i do tyłu.</span><span class="sxs-lookup"><span data-stu-id="b3c04-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="b3c04-127">Kontrakt klienta zawiera operację usługi do raportowania jej pozycji.</span><span class="sxs-lookup"><span data-stu-id="b3c04-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <span data-ttu-id="b3c04-128">Zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> atrybutów i <xref:System.ServiceModel.OperationContractAttribute> umożliwia automatyczne generowanie definicji kontraktu usługi w Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="b3c04-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
- <span data-ttu-id="b3c04-129">Użyj [Narzędzia do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , aby pobrać dokument WSDL i (opcjonalnie) kod i konfigurację dla klienta.</span><span class="sxs-lookup"><span data-stu-id="b3c04-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
- <span data-ttu-id="b3c04-130">Punkty końcowe uwidaczniające usługi dupleksowe muszą być zabezpieczone.</span><span class="sxs-lookup"><span data-stu-id="b3c04-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="b3c04-131">Gdy usługa otrzymuje komunikat o dupleksie, przegląda replikę replytą w tym komunikacie przychodzącym, aby określić, gdzie należy wysłać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="b3c04-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="b3c04-132">Jeśli kanał nie jest zabezpieczony, klient niezaufanego może wysłać złośliwą wiadomość z replytą maszyny docelowej, co prowadzi do odmowy usługi Maszyny docelowej.</span><span class="sxs-lookup"><span data-stu-id="b3c04-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="b3c04-133">W przypadku zwykłych komunikatów z żądaniem odpowiedzi nie jest to problem, ponieważ ReplyTo jest ignorowany, a odpowiedź jest wysyłana w kanale, w którym znajduje się pierwotny komunikat.</span><span class="sxs-lookup"><span data-stu-id="b3c04-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c04-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3c04-134">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="b3c04-135">Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="b3c04-135">How to: Access Services with a Duplex Contract</span></span>](how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="b3c04-136">Dupleks</span><span class="sxs-lookup"><span data-stu-id="b3c04-136">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="b3c04-137">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="b3c04-137">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="b3c04-138">Instrukcje: definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="b3c04-138">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="b3c04-139">Sesja</span><span class="sxs-lookup"><span data-stu-id="b3c04-139">Session</span></span>](../samples/session.md)
