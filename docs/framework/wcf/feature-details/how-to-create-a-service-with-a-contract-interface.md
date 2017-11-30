---
title: "Instrukcje: Tworzenie usługi przy użyciu interfejsu kontraktu"
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
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b00a7cbbab343eb209895affbbbba76ef2af2959
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="a21e4-102">Instrukcje: Tworzenie usługi przy użyciu interfejsu kontraktu</span><span class="sxs-lookup"><span data-stu-id="a21e4-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="a21e4-103">Preferowany sposób tworzenia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Umowa jest przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a21e4-103">The preferred way to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> <span data-ttu-id="a21e4-104">Tego kontraktu określono, kolekcji i struktura wiadomości wymagany dostęp do oferty usługi.</span><span class="sxs-lookup"><span data-stu-id="a21e4-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="a21e4-105">Ten interfejs definiuje typów wejściowych i wyjściowych przez zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu i <xref:System.ServiceModel.OperationContractAttribute> klas do metody, które chcesz udostępnić.</span><span class="sxs-lookup"><span data-stu-id="a21e4-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a21e4-106">Umowy o świadczenie usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a21e4-106"> service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="a21e4-107">Tworzenie przy użyciu interfejsu kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="a21e4-107">Creating a WCF contract with an interface</span></span>  
  
1.  <span data-ttu-id="a21e4-108">Tworzenie nowego przy użyciu interfejsu [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# lub dowolnego innego wspólnego języka środowiska uruchomieniowego języka.</span><span class="sxs-lookup"><span data-stu-id="a21e4-108">Create a new interface using [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="a21e4-109">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a21e4-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3.  <span data-ttu-id="a21e4-110">Zdefiniuj metody w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="a21e4-110">Define the methods in the interface.</span></span>  
  
4.  <span data-ttu-id="a21e4-111">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, która musi być udostępniany jako część publicznego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontraktu.</span><span class="sxs-lookup"><span data-stu-id="a21e4-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a21e4-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a21e4-112">Example</span></span>  
 <span data-ttu-id="a21e4-113">Poniższy przykład kodu pokazuje interfejs, który definiuje kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="a21e4-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="a21e4-114">Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasa stosowana domyślnie używają komunikatów żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="a21e4-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a21e4-115">Ten wzorzec komunikatów, zobacz [porady: tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a21e4-115"> this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="a21e4-116">Można również utworzyć i używać innych wzorcach wiadomości przez ustawienie właściwości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a21e4-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="a21e4-117">Więcej przykładów można znaleźć [porady: tworzenie kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [porady: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a21e4-117">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a21e4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a21e4-118">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
