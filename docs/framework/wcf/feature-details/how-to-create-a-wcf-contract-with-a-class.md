---
title: 'Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy'
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
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa09e1900b0709130cb4c58240c38d1bd5d1d92d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="4ee3e-102">Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy</span><span class="sxs-lookup"><span data-stu-id="4ee3e-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="4ee3e-103">Preferowany sposób tworzenia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Umowa jest przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-103">The preferred way of creating a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="4ee3e-104"> [Porady: definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="4ee3e-104"> [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="4ee3e-105">Tutaj alternatywne, obramowane ma utworzyć klasę, a następnie zastosować <xref:System.ServiceModel.ServiceContractAttribute> bezpośrednio do klasy atrybutu i <xref:System.ServiceModel.OperationContractAttribute> atrybutu do każdej z metod w klasie, które są częścią kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4ee3e-106">`[ServiceContract]` i `[ServiceContractAttribute]` tak samo postąpić.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="4ee3e-107">To samo wartość true, aby uzyskać `[OperationContract]` i `[OperationContractAttribute]`.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-107">The same thing it true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="4ee3e-108">W każdym przypadku jest skrócona dla niego.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-108">In each case the former is shorthand for the latter.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4ee3e-109"> Umowy o świadczenie usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="4ee3e-109"> service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="4ee3e-110">Tworzenie kontraktu programu Windows Communication Foundation z klasą</span><span class="sxs-lookup"><span data-stu-id="4ee3e-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1.  <span data-ttu-id="4ee3e-111">Utwórz nową klasę za pomocą Visual Basic, C# lub dowolnego innego wspólnego języka środowiska uruchomieniowego języka.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="4ee3e-112">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy do klasy.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3.  <span data-ttu-id="4ee3e-113">Utwórz metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-113">Create methods in the class.</span></span>  
  
4.  <span data-ttu-id="4ee3e-114">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, która musi być udostępniany jako część publicznego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ee3e-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ee3e-115">Example</span></span>  
 <span data-ttu-id="4ee3e-116">Poniższy przykład kodu pokazuje klasa, która definiuje kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="4ee3e-117">Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasa stosowana domyślnie używają komunikatów żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4ee3e-118"> Ten wzorzec komunikatów, zobacz [porady: tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="4ee3e-118"> this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="4ee3e-119">Można również utworzyć i używać innych wzorcach wiadomości przez ustawienie właściwości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="4ee3e-120">Więcej przykładów można znaleźć [porady: tworzenie kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [porady: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="4ee3e-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee3e-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ee3e-121">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
