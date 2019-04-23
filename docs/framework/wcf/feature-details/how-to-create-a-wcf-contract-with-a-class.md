---
title: 'Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 37d0e6fae8ad0f3a91f1bead23fb5823fc52d420
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313226"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="8e448-102">Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy</span><span class="sxs-lookup"><span data-stu-id="8e448-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="8e448-103">Jest preferowany sposób tworzenia kontraktu usługi Windows Communication Foundation (WCF) przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8e448-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="8e448-104">Aby uzyskać więcej informacji, zobacz [jak: Definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="8e448-104">For more information, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="8e448-105">Tutaj alternatywne, schemat jest utworzyć klasę, a następnie zastosować <xref:System.ServiceModel.ServiceContractAttribute> bezpośrednio do klasy atrybutu i <xref:System.ServiceModel.OperationContractAttribute> atrybut do każdej metody w klasie, które są dostępne w ramach umowy.</span><span class="sxs-lookup"><span data-stu-id="8e448-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8e448-106">`[ServiceContract]` i `[ServiceContractAttribute]` zrobić to samo.</span><span class="sxs-lookup"><span data-stu-id="8e448-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="8e448-107">Dotyczy to samo `[OperationContract]` i `[OperationContractAttribute]`.</span><span class="sxs-lookup"><span data-stu-id="8e448-107">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="8e448-108">W każdym przypadku jest skrócona, w przypadku drugiego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="8e448-108">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="8e448-109">Aby uzyskać więcej informacji na temat kontraktów usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8e448-109">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="8e448-110">Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy</span><span class="sxs-lookup"><span data-stu-id="8e448-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1. <span data-ttu-id="8e448-111">Utwórz nową klasę w języku Visual Basic C#, lub dowolnego innego języka środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="8e448-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="8e448-112">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy do klasy.</span><span class="sxs-lookup"><span data-stu-id="8e448-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3. <span data-ttu-id="8e448-113">Tworzenie metod w klasie.</span><span class="sxs-lookup"><span data-stu-id="8e448-113">Create methods in the class.</span></span>  
  
4. <span data-ttu-id="8e448-114">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, które muszą być widoczne jako część publicznego kontraktu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8e448-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e448-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e448-115">Example</span></span>  
 <span data-ttu-id="8e448-116">Poniższy przykład kodu pokazuje klasę, która definiuje kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="8e448-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="8e448-117">Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasy stosowane domyślnie używają wzorzec komunikatów typu żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="8e448-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="8e448-118">Aby uzyskać więcej informacji na temat tego wzorca wiadomości zobacz [jak: Tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="8e448-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="8e448-119">Można również tworzyć i używać innych wzorców komunikatu przez ustawienie właściwości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8e448-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="8e448-120">Aby uzyskać więcej przykładów, zobacz [jak: Tworzenie kontraktu jednokierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [jak: Tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="8e448-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e448-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e448-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
