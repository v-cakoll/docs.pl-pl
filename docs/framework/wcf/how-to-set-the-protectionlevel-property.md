---
title: "Instrukcje: Ustawianie właściwości ProtectionLevel"
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
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6105b1b367f9f8cab1f2ba3a38b148038478c780
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="461dd-102">Instrukcje: Ustawianie właściwości ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="461dd-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="461dd-103">Stosowanie odpowiedniego atrybutu i ustawiając właściwości można ustawić poziom ochrony.</span><span class="sxs-lookup"><span data-stu-id="461dd-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="461dd-104">Można ustawić ochrony na poziomie usługi wpływ na wszystkie części każdej wiadomości lub coraz bardziej szczegółowym poziomie, można ustawić ochrony z metody części wiadomości.</span><span class="sxs-lookup"><span data-stu-id="461dd-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="461dd-105">`ProtectionLevel` właściwości, zobacz [poziom ochrony opis](../../../docs/framework/wcf/understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="461dd-105"> the `ProtectionLevel` property, see [Understanding Protection Level](../../../docs/framework/wcf/understanding-protection-level.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="461dd-106">Poziomy ochrony można ustawić tylko w kodzie, a nie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="461dd-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="461dd-107">Aby podpisać wszystkie komunikaty dla usługi</span><span class="sxs-lookup"><span data-stu-id="461dd-107">To sign all messages for a service</span></span>  
  
1.  <span data-ttu-id="461dd-108">Utwórz interfejs dla usługi.</span><span class="sxs-lookup"><span data-stu-id="461dd-108">Create an interface for the service.</span></span>  
  
2.  <span data-ttu-id="461dd-109">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> atrybutu z usługą i ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie (jest to domyślny poziom <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span><span class="sxs-lookup"><span data-stu-id="461dd-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="461dd-110">Wszystkie części komunikatu dla operacji logowania</span><span class="sxs-lookup"><span data-stu-id="461dd-110">To sign all message parts for an operation</span></span>  
  
1.  <span data-ttu-id="461dd-111">Interfejs dla usługi tworzenia i stosowania <xref:System.ServiceModel.ServiceContractAttribute> do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="461dd-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2.  <span data-ttu-id="461dd-112">Dodawanie deklaracji metody interfejsu.</span><span class="sxs-lookup"><span data-stu-id="461dd-112">Add a method declaration to the interface.</span></span>  
  
3.  <span data-ttu-id="461dd-113">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybut do metody i ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="461dd-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="461dd-114">Ochrona komunikatów "Fault"</span><span class="sxs-lookup"><span data-stu-id="461dd-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="461dd-115">Wyjątki, które są generowane w usłudze można wysłać do klienta jako błędach SOAP.</span><span class="sxs-lookup"><span data-stu-id="461dd-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="461dd-116">Tworzenie silnie typizowanej błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) i [porady: deklarowanie błędów w kontraktach usług](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="461dd-116"> creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="461dd-117">Aby chronić komunikat o błędzie</span><span class="sxs-lookup"><span data-stu-id="461dd-117">To protect a fault message</span></span>  
  
1.  <span data-ttu-id="461dd-118">Utwórz typ reprezentujący komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="461dd-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="461dd-119">Poniższy przykład tworzy klasę o nazwie `MathFault` z dwoma polami.</span><span class="sxs-lookup"><span data-stu-id="461dd-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2.  <span data-ttu-id="461dd-120">Zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do typu i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego pola, które powinny być serializowane, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="461dd-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  <span data-ttu-id="461dd-121">W interfejsie zwróci błąd, należy zastosować <xref:System.ServiceModel.FaultContractAttribute> atrybut do metody, która zwróci błąd i ustawić `detailType` parametru na typ klasy błędów.</span><span class="sxs-lookup"><span data-stu-id="461dd-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4.  <span data-ttu-id="461dd-122">Również w konstruktorze, należy ustawić <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="461dd-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="461dd-123">Ochrona części wiadomości</span><span class="sxs-lookup"><span data-stu-id="461dd-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="461dd-124">Użyj kontraktu komunikatu, aby chronić części wiadomości.</span><span class="sxs-lookup"><span data-stu-id="461dd-124">Use a message contract to protect parts of a message.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="461dd-125">kontrakty, zobacz [za pomocą kontraktów komunikatu](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="461dd-125"> message contracts, see [Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="461dd-126">Aby chronić treści wiadomości</span><span class="sxs-lookup"><span data-stu-id="461dd-126">To protect a message body</span></span>  
  
1.  <span data-ttu-id="461dd-127">Utwórz typ, który reprezentuje wiadomość.</span><span class="sxs-lookup"><span data-stu-id="461dd-127">Create a type that represents the message.</span></span> <span data-ttu-id="461dd-128">Poniższy przykład tworzy `Company` klasy z polami dwóch `CompanyName` i `CompanyID`.</span><span class="sxs-lookup"><span data-stu-id="461dd-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2.  <span data-ttu-id="461dd-129">Zastosuj <xref:System.ServiceModel.MessageContractAttribute> do klasy atrybutu i ustaw <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="461dd-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3.  <span data-ttu-id="461dd-130">Zastosuj <xref:System.ServiceModel.MessageHeaderAttribute> do pola, które będą wyrażone jako nagłówek wiadomości i ustawić atrybut `ProtectionLevel` właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="461dd-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4.  <span data-ttu-id="461dd-131">Zastosuj <xref:System.ServiceModel.MessageBodyMemberAttribute> do dowolnego pola, które ma być wyrażone jako część treści wiadomości i ustaw `ProtectionLevel` właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="461dd-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="461dd-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="461dd-132">Example</span></span>  
 <span data-ttu-id="461dd-133">W poniższym przykładzie `ProtectionLevel` właściwości kilka klas atrybutów w różnych miejscach w usłudze.</span><span class="sxs-lookup"><span data-stu-id="461dd-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="461dd-134">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="461dd-134">Compiling the Code</span></span>  
 <span data-ttu-id="461dd-135">Poniższy kod przedstawia przestrzenie nazw wymaganego do skompilowania przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="461dd-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="461dd-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="461dd-136">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 [<span data-ttu-id="461dd-137">Omówienie poziomów ochrony</span><span class="sxs-lookup"><span data-stu-id="461dd-137">Understanding Protection Level</span></span>](../../../docs/framework/wcf/understanding-protection-level.md)
