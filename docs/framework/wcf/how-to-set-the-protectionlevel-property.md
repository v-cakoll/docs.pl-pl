---
title: 'Instrukcje: Ustawianie właściwości ProtectionLevel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: ce9fc8549218db5a1446026421f1a7ba1e5a23aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089851"
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="51d6c-102">Instrukcje: Ustawianie właściwości ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="51d6c-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="51d6c-103">Można ustawić poziom ochrony przez zastosowanie odpowiedniego atrybutu i ustawienie właściwości.</span><span class="sxs-lookup"><span data-stu-id="51d6c-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="51d6c-104">Można ustawić ochrony na poziomie usługi, aby wpływają na wszystkie elementy w każdej wiadomości lub ochrony można ustawić na coraz bardziej szczegółowym poziomie, od metody części wiadomości.</span><span class="sxs-lookup"><span data-stu-id="51d6c-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> <span data-ttu-id="51d6c-105">Aby uzyskać więcej informacji na temat `ProtectionLevel` właściwości, zobacz [zrozumieć poziom ochrony](../../../docs/framework/wcf/understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="51d6c-105">For more information about the `ProtectionLevel` property, see [Understanding Protection Level](../../../docs/framework/wcf/understanding-protection-level.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51d6c-106">Poziomy ochrony można ustawić tylko w przypadku kodu, a nie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="51d6c-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="51d6c-107">Aby zarejestrować wszystkie komunikaty dla usługi</span><span class="sxs-lookup"><span data-stu-id="51d6c-107">To sign all messages for a service</span></span>  
  
1.  <span data-ttu-id="51d6c-108">Utwórz interfejs dla usługi.</span><span class="sxs-lookup"><span data-stu-id="51d6c-108">Create an interface for the service.</span></span>  
  
2.  <span data-ttu-id="51d6c-109">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> atrybutu w usłudze i ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie (jest to domyślny poziom <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span><span class="sxs-lookup"><span data-stu-id="51d6c-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="51d6c-110">Aby zarejestrować wszystkie części komunikatu dla operacji</span><span class="sxs-lookup"><span data-stu-id="51d6c-110">To sign all message parts for an operation</span></span>  
  
1.  <span data-ttu-id="51d6c-111">Tworzenie interfejsu usługi i stosowanie <xref:System.ServiceModel.ServiceContractAttribute> atrybutu do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="51d6c-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2.  <span data-ttu-id="51d6c-112">Dodaj deklarację metody interfejsu.</span><span class="sxs-lookup"><span data-stu-id="51d6c-112">Add a method declaration to the interface.</span></span>  
  
3.  <span data-ttu-id="51d6c-113">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybutu do metody, a następnie ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="51d6c-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="51d6c-114">Ochrona komunikaty o błędach</span><span class="sxs-lookup"><span data-stu-id="51d6c-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="51d6c-115">Wyjątki wyrzucane usługi mogą być wysyłane do klienta jako błędach SOAP.</span><span class="sxs-lookup"><span data-stu-id="51d6c-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> <span data-ttu-id="51d6c-116">Aby uzyskać więcej informacji na temat tworzenia silnie typizowane błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) i [jak: Deklarowanie błędów w kontraktach usługi](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="51d6c-116">For more information about creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="51d6c-117">Aby chronić komunikatu o błędzie</span><span class="sxs-lookup"><span data-stu-id="51d6c-117">To protect a fault message</span></span>  
  
1.  <span data-ttu-id="51d6c-118">Utwórz typ, który reprezentuje komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="51d6c-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="51d6c-119">Poniższy przykład tworzy klasę o nazwie `MathFault` przy użyciu dwóch pól.</span><span class="sxs-lookup"><span data-stu-id="51d6c-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2.  <span data-ttu-id="51d6c-120">Zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego pola, które powinny być Zserializowany, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="51d6c-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  <span data-ttu-id="51d6c-121">W interfejsie, który zwróci błąd, należy zastosować <xref:System.ServiceModel.FaultContractAttribute> atrybutu do metody, która zwróci błąd i ustawić `detailType` parametr typu klasy błędów.</span><span class="sxs-lookup"><span data-stu-id="51d6c-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4.  <span data-ttu-id="51d6c-122">Również w konstruktorze, należy ustawić <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="51d6c-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="51d6c-123">Ochrona części wiadomości</span><span class="sxs-lookup"><span data-stu-id="51d6c-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="51d6c-124">Użyj kontraktu komunikatu, aby chronić części wiadomości.</span><span class="sxs-lookup"><span data-stu-id="51d6c-124">Use a message contract to protect parts of a message.</span></span> <span data-ttu-id="51d6c-125">Aby uzyskać więcej informacji na temat kontraktów komunikatu zobacz [za pomocą kontraktów komunikatu](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="51d6c-125">For more information about message contracts, see [Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="51d6c-126">Aby chronić treść komunikatu</span><span class="sxs-lookup"><span data-stu-id="51d6c-126">To protect a message body</span></span>  
  
1.  <span data-ttu-id="51d6c-127">Utwórz typ, który reprezentuje komunikat.</span><span class="sxs-lookup"><span data-stu-id="51d6c-127">Create a type that represents the message.</span></span> <span data-ttu-id="51d6c-128">Poniższy przykład tworzy `Company` klasy przy użyciu dwóch pól `CompanyName` i `CompanyID`.</span><span class="sxs-lookup"><span data-stu-id="51d6c-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2.  <span data-ttu-id="51d6c-129">Zastosuj <xref:System.ServiceModel.MessageContractAttribute> do klasy atrybutu i ustaw <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> właściwość <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="51d6c-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3.  <span data-ttu-id="51d6c-130">Zastosuj <xref:System.ServiceModel.MessageHeaderAttribute> atrybutu do pola, które będą wyrażone jako nagłówek wiadomości oraz ustawić `ProtectionLevel` właściwość <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="51d6c-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4.  <span data-ttu-id="51d6c-131">Zastosuj <xref:System.ServiceModel.MessageBodyMemberAttribute> do dowolnego pola, które będą wyrażone jako część treści wiadomości oraz ustawić `ProtectionLevel` właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="51d6c-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="51d6c-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="51d6c-132">Example</span></span>  
 <span data-ttu-id="51d6c-133">Poniższy przykład ustawia `ProtectionLevel` właściwość kilka klas atrybutów w różnych miejscach w usłudze.</span><span class="sxs-lookup"><span data-stu-id="51d6c-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="51d6c-134">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="51d6c-134">Compiling the Code</span></span>  
 <span data-ttu-id="51d6c-135">Poniższy kod przedstawia przestrzeni nazw, wymaganych do Kompilowanie przykładowego kodu.</span><span class="sxs-lookup"><span data-stu-id="51d6c-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="51d6c-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51d6c-136">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [<span data-ttu-id="51d6c-137">Omówienie poziomów ochrony</span><span class="sxs-lookup"><span data-stu-id="51d6c-137">Understanding Protection Level</span></span>](../../../docs/framework/wcf/understanding-protection-level.md)
