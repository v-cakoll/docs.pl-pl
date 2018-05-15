---
title: 'Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 296f500532040aaebf0f6d7d37a7a9aae99a3451
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="a40e3-102">Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy</span><span class="sxs-lookup"><span data-stu-id="a40e3-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="a40e3-103">Preferowaną metodą tworzenia kontraktu usługi Windows Communication Foundation (WCF) jest przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a40e3-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="a40e3-104">Aby uzyskać więcej informacji, zobacz [porady: definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a40e3-104">For more information, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="a40e3-105">Tutaj alternatywne, obramowane ma utworzyć klasę, a następnie zastosować <xref:System.ServiceModel.ServiceContractAttribute> bezpośrednio do klasy atrybutu i <xref:System.ServiceModel.OperationContractAttribute> atrybutu do każdej z metod w klasie, które są częścią kontraktu.</span><span class="sxs-lookup"><span data-stu-id="a40e3-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a40e3-106">`[ServiceContract]` i `[ServiceContractAttribute]` tak samo postąpić.</span><span class="sxs-lookup"><span data-stu-id="a40e3-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="a40e3-107">To samo wartość true, aby uzyskać `[OperationContract]` i `[OperationContractAttribute]`.</span><span class="sxs-lookup"><span data-stu-id="a40e3-107">The same thing it true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="a40e3-108">W każdym przypadku jest skrócona dla niego.</span><span class="sxs-lookup"><span data-stu-id="a40e3-108">In each case the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="a40e3-109">Aby uzyskać więcej informacji na temat kontraktów usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a40e3-109">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="a40e3-110">Tworzenie kontraktu programu Windows Communication Foundation z klasą</span><span class="sxs-lookup"><span data-stu-id="a40e3-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1.  <span data-ttu-id="a40e3-111">Utwórz nową klasę za pomocą Visual Basic, C# lub dowolnego innego wspólnego języka środowiska uruchomieniowego języka.</span><span class="sxs-lookup"><span data-stu-id="a40e3-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="a40e3-112">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy do klasy.</span><span class="sxs-lookup"><span data-stu-id="a40e3-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3.  <span data-ttu-id="a40e3-113">Utwórz metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="a40e3-113">Create methods in the class.</span></span>  
  
4.  <span data-ttu-id="a40e3-114">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, która musi być udostępniany jako część publicznego kontraktu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="a40e3-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a40e3-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="a40e3-115">Example</span></span>  
 <span data-ttu-id="a40e3-116">Poniższy przykład kodu pokazuje klasa, która definiuje kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="a40e3-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="a40e3-117">Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasa stosowana domyślnie używają komunikatów żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="a40e3-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="a40e3-118">Aby uzyskać więcej informacji o tym wzorcu komunikatów, zobacz [porady: tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a40e3-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="a40e3-119">Można również utworzyć i używać innych wzorcach wiadomości przez ustawienie właściwości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a40e3-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="a40e3-120">Więcej przykładów można znaleźć [porady: tworzenie kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [porady: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a40e3-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a40e3-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a40e3-121">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
