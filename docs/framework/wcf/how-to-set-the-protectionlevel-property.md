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
ms.openlocfilehash: 4ff835f767852da586a3a35b7f4ce2edf99db283
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320913"
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="bca07-102">Instrukcje: Ustawianie właściwości ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="bca07-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="bca07-103">Poziom ochrony można ustawić, stosując odpowiedni atrybut i ustawiając właściwość.</span><span class="sxs-lookup"><span data-stu-id="bca07-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="bca07-104">Można ustawić ochronę na poziomie usługi, aby mieć wpływ na wszystkie części każdego komunikatu, lub można ustawić ochronę na coraz większych poziomach, od metod do części komunikatów.</span><span class="sxs-lookup"><span data-stu-id="bca07-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> <span data-ttu-id="bca07-105">Aby uzyskać więcej informacji na temat właściwości `ProtectionLevel`, zobacz [Opis poziomu ochrony](understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="bca07-105">For more information about the `ProtectionLevel` property, see [Understanding Protection Level](understanding-protection-level.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bca07-106">Poziomy ochrony można ustawić tylko w kodzie, a nie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bca07-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="bca07-107">Aby podpisać wszystkie komunikaty dotyczące usługi</span><span class="sxs-lookup"><span data-stu-id="bca07-107">To sign all messages for a service</span></span>  
  
1. <span data-ttu-id="bca07-108">Utwórz interfejs dla usługi.</span><span class="sxs-lookup"><span data-stu-id="bca07-108">Create an interface for the service.</span></span>  
  
2. <span data-ttu-id="bca07-109">Zastosuj atrybut <xref:System.ServiceModel.ServiceContractAttribute> do usługi i ustaw właściwość <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> na <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie (poziom domyślny to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span><span class="sxs-lookup"><span data-stu-id="bca07-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="bca07-110">Aby podpisywać wszystkie części komunikatów dla operacji</span><span class="sxs-lookup"><span data-stu-id="bca07-110">To sign all message parts for an operation</span></span>  
  
1. <span data-ttu-id="bca07-111">Utwórz interfejs dla usługi i zastosuj atrybut <xref:System.ServiceModel.ServiceContractAttribute> do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bca07-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2. <span data-ttu-id="bca07-112">Dodaj deklarację metody do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bca07-112">Add a method declaration to the interface.</span></span>  
  
3. <span data-ttu-id="bca07-113">Zastosuj atrybut <xref:System.ServiceModel.OperationContractAttribute> do metody i ustaw właściwość <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> na <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bca07-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="bca07-114">Ochrona komunikatów o błędach</span><span class="sxs-lookup"><span data-stu-id="bca07-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="bca07-115">Wyjątki zgłaszane w ramach usługi mogą być wysyłane do klienta jako błędy SOAP.</span><span class="sxs-lookup"><span data-stu-id="bca07-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> <span data-ttu-id="bca07-116">Aby uzyskać więcej informacji na temat tworzenia jednoznacznie wpisanych błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md) oraz [instrukcje: deklarowanie błędów w kontraktach usługi](how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="bca07-116">For more information about creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="bca07-117">Aby chronić komunikat o błędzie</span><span class="sxs-lookup"><span data-stu-id="bca07-117">To protect a fault message</span></span>  
  
1. <span data-ttu-id="bca07-118">Utwórz typ, który reprezentuje komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="bca07-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="bca07-119">Poniższy przykład tworzy klasę o nazwie `MathFault` z dwoma polami.</span><span class="sxs-lookup"><span data-stu-id="bca07-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2. <span data-ttu-id="bca07-120">Zastosuj atrybut <xref:System.Runtime.Serialization.DataContractAttribute> do typu i atrybutu <xref:System.Runtime.Serialization.DataMemberAttribute> do każdego pola, które powinny być serializowane, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bca07-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. <span data-ttu-id="bca07-121">W interfejsie, który zwróci błąd, zastosuj atrybut <xref:System.ServiceModel.FaultContractAttribute> do metody, która zwróci błąd i ustawił parametr `detailType` na typ klasy Fault.</span><span class="sxs-lookup"><span data-stu-id="bca07-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4. <span data-ttu-id="bca07-122">Ponadto w konstruktorze ustaw właściwość <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bca07-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="bca07-123">Ochrona części komunikatów</span><span class="sxs-lookup"><span data-stu-id="bca07-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="bca07-124">Użyj kontraktu komunikatu, aby chronić części wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bca07-124">Use a message contract to protect parts of a message.</span></span> <span data-ttu-id="bca07-125">Aby uzyskać więcej informacji na temat umów dotyczących komunikatów, zobacz [Używanie kontraktów komunikatów](./feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="bca07-125">For more information about message contracts, see [Using Message Contracts](./feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="bca07-126">Aby chronić treść wiadomości</span><span class="sxs-lookup"><span data-stu-id="bca07-126">To protect a message body</span></span>  
  
1. <span data-ttu-id="bca07-127">Utwórz typ, który reprezentuje komunikat.</span><span class="sxs-lookup"><span data-stu-id="bca07-127">Create a type that represents the message.</span></span> <span data-ttu-id="bca07-128">Poniższy przykład tworzy klasę `Company` z dwoma polami, `CompanyName` i `CompanyID`.</span><span class="sxs-lookup"><span data-stu-id="bca07-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2. <span data-ttu-id="bca07-129">Zastosuj atrybut <xref:System.ServiceModel.MessageContractAttribute> do klasy i ustaw właściwość <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="bca07-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3. <span data-ttu-id="bca07-130">Zastosuj atrybut <xref:System.ServiceModel.MessageHeaderAttribute> do pola, które będzie wyrażone jako nagłówek komunikatu, i ustaw właściwość `ProtectionLevel` na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="bca07-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4. <span data-ttu-id="bca07-131">Zastosuj <xref:System.ServiceModel.MessageBodyMemberAttribute> do dowolnego pola, które będzie wyrażone jako część treści komunikatu, i ustaw właściwość `ProtectionLevel` na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bca07-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="bca07-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="bca07-132">Example</span></span>  
 <span data-ttu-id="bca07-133">Poniższy przykład ustawia właściwość `ProtectionLevel` kilku klas atrybutów w różnych miejscach w usłudze.</span><span class="sxs-lookup"><span data-stu-id="bca07-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bca07-134">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bca07-134">Compiling the Code</span></span>  
 <span data-ttu-id="bca07-135">Poniższy kod przedstawia przestrzenie nazw wymagane do skompilowania przykładowego kodu.</span><span class="sxs-lookup"><span data-stu-id="bca07-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="bca07-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bca07-136">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [<span data-ttu-id="bca07-137">Omówienie poziomów ochrony</span><span class="sxs-lookup"><span data-stu-id="bca07-137">Understanding Protection Level</span></span>](understanding-protection-level.md)
