---
title: 'Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: a514134ed0af3b691a2e66720f81594a51747b6f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089526"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="95fba-102">Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy</span><span class="sxs-lookup"><span data-stu-id="95fba-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="95fba-103">Jest preferowany sposób tworzenia kontraktu usługi Windows Communication Foundation (WCF) przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="95fba-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="95fba-104">Aby uzyskać więcej informacji, zobacz [jak: Definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="95fba-104">For more information, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="95fba-105">Tutaj alternatywne, schemat jest utworzyć klasę, a następnie zastosować <xref:System.ServiceModel.ServiceContractAttribute> bezpośrednio do klasy atrybutu i <xref:System.ServiceModel.OperationContractAttribute> atrybut do każdej metody w klasie, które są dostępne w ramach umowy.</span><span class="sxs-lookup"><span data-stu-id="95fba-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  `[ServiceContract]` <span data-ttu-id="95fba-106">i `[ServiceContractAttribute]` zrobić to samo.</span><span class="sxs-lookup"><span data-stu-id="95fba-106">and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="95fba-107">Dotyczy to samo `[OperationContract]` i `[OperationContractAttribute]`.</span><span class="sxs-lookup"><span data-stu-id="95fba-107">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="95fba-108">W każdym przypadku jest skrócona, w przypadku drugiego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="95fba-108">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="95fba-109">Aby uzyskać więcej informacji na temat kontraktów usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="95fba-109">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="95fba-110">Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy</span><span class="sxs-lookup"><span data-stu-id="95fba-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1.  <span data-ttu-id="95fba-111">Utwórz nową klasę w języku Visual Basic C#, lub dowolnego innego języka środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="95fba-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="95fba-112">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy do klasy.</span><span class="sxs-lookup"><span data-stu-id="95fba-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3.  <span data-ttu-id="95fba-113">Tworzenie metod w klasie.</span><span class="sxs-lookup"><span data-stu-id="95fba-113">Create methods in the class.</span></span>  
  
4.  <span data-ttu-id="95fba-114">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, które muszą być widoczne jako część publicznego kontraktu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="95fba-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95fba-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="95fba-115">Example</span></span>  
 <span data-ttu-id="95fba-116">Poniższy przykład kodu pokazuje klasę, która definiuje kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="95fba-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="95fba-117">Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasy stosowane domyślnie używają wzorzec komunikatów typu żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="95fba-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="95fba-118">Aby uzyskać więcej informacji na temat tego wzorca wiadomości zobacz [jak: Tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="95fba-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="95fba-119">Można również tworzyć i używać innych wzorców komunikatu przez ustawienie właściwości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="95fba-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="95fba-120">Aby uzyskać więcej przykładów, zobacz [jak: Tworzenie kontraktu jednokierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [jak: Tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="95fba-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fba-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95fba-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
